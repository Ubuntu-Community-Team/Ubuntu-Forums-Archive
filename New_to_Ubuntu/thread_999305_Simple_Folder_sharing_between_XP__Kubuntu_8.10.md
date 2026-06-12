---
title: "Simple Folder sharing between XP / Kubuntu 8.10"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-12-01
I have the following network setup:

1. Router:
192.168.1.1 fixed, running the network's DHCP server

2. Windows XP PC:
192.168.1.6 assigned by DHCP.
machine's name seems to be yyz 
(you can 'ping yyz' from another XP machine & get replies from 192.168.1.6)
Second IDE drive is D:\ - want to share D:\MUSIC which is enabled for sharing in XP
Workgroup name is 'WORKGROUP'

3. Kubuntu 8.10 PC
192.168.1.7 assigned by DHCP
If I 'ping yyz' using the terminal here,
I get replies from hit-nxdomain.opendns.com (208.69.34.132)

4. An XP laptop on 192.168.1.4

I'm trying to use 'Add Network Folder' ('Network Folder Wizard') from
K menu > Computer > Network
on the Kubuntu machine, to set up access to the XP machine's D:\MUSIC folder.

I'm specifying:
Microsoft (r) Windows (r) network drive
Name: Music
Server: yyz
Folder: D:\MUSIC 

On clicking 'Save & connect',  it tries for a while to connect to:

smb://yyz/D:/MUSIC

.. but eventually gives up, saying it can't find the server.

The 192.168.1.4 XP lappy can see '\\yyz\music' okay.

Help, I'm lost. 'yyz' is visible to Windows but isn't the right name to specify for linux? ping seems to want to ask the internet / opendns about it.. or am i barking up the wrong tree entirely

---

### Post by ecs_pf5 on 2008-12-01
Okay.. got it working by installing samba (doh, shouldn't have assumed it was installed by default) and using the current DHCP IP address of the Windows machine in the 'server' field of the wizard.

But.. that IP addy might change due to DHCP so I'd still like to refer to the XP machine by a name rather than an IP addy - I guess the name 'yyz' that it comes up under in Windows is wrong for samba, because it still isn't finding it. What should I be using instead?

---

