---
authors: Noah Mehl <noahmehl@gmail.com>
state: predraft
---

# RFD 27 Add web based serial and vnc console

## Background
It can become difficult to work with machines that are virtualized via KVM, or even LX zones, when something goes wrong.  Users that transition to SDC from other platforms, such as OpenStack are familiar with having a VNC console through the web (Horizon in this case).

## Introduction

There are two open source projects that would allow users to gain access to the serial and vnc consoles of running machines in adminui.  It would be nice to be able to get to these consoles directly from the virtual machine pages in adminui.

Serial Console - https://github.com/antonylesuisse/qweb or http://anyterm.org
VNC Console - http://kanaka.github.io/noVNC/

## Requirements

When browsing an individual VM (/vms/{uuid}), there should be new "Actions" available.  One should be VNC console (when it should be available, i.e. KVM) and another should be Serial console (all vm's?).  When a user clicks on either action, it should open a new window with the appropriate console.  This should be proxied through adminui, and should follow the same user/rbac controls as the rest of adminui.

## Networking Considerations

If the adminui machine/s have external address/es, and end users are not able to route directly to compute nodes, then there will need to be some reverse proxy method (in adminui? or another zone?) to provide connectivity to the compute nodes.

## Other Considerations

These items should likely be exposed via CloudAPI (as recommended by rmustacc on IRC)
