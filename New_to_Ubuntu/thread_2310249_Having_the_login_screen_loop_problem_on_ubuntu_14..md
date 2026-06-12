---
title: "Having the login screen loop problem on ubuntu 14.04"
date: 2016-01-17
forum: New to Ubuntu
---

### Post by lefteris3 on 2016-01-17
Hello everybody! Im new to Ubuntu, I did some research online before posting and didn't find cases fitting to my problem. I am on a Sony Vaio laptop, running only ubuntu 14.04 (no dual boot). The login screen keeps looping either when entering the correct password for my session or guest. I press Control+Alt+F1 to enter the command line and type the following commands.

Looking at past posts on the same problem I tried:
input:**ls -al /home/** 
output: rw privileges provided to user lef (=me)

input: **ls -al /home/lef/.Xauthority** and **ls -al /home/lef/.ICEauthority**
output: both give rw only privileges to lef  (i.e.-rw------- 1 lef lef ...)

input:**lspci -vnn | grep VGA -A 12**
output: VGA compatible controller [0300]: Advanced Micro Devices. Inc. [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470] .... [VGA controller]

input: **sudo lshw -C display**
output: 
*-display
description: VGA compatible controller
product: RV620/M82 [Mobility Radeon HD 3450/3470]
vendor: AMD/ATI
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width:32 bits
clock: 33Mhz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:49 memory:c0000000-cfffffff ioport:9000(size=256) memory:d0020000-d002ffff memory:d0000000-d001ffff

input: sudo ubuntu-drivers list
output: Gives nothing as output

I have uninstalled/reinstalled/reconfigured lightdm manager (is the only installed as seen in /etc/X11/default-display-manager) and still nothing, the problem remains.

Permissions of [COLOR=#0000ff]/tmp[/COLOR] look good i.e., it must be drwxrwxrwt ,and it is.

I am just ruling out cases I read at the posts, I have no idea where might be the problem. Any ideas? Is this for real?

---

### Post by lefteris3 on 2016-01-18
Hello all, the problem is solved by looking at this post:[http://ubuntuforums.org/showthread.php?t=2267058](http://ubuntuforums.org/showthread.php?t=2267058)

I looked for errors in .xsession-errors and found this: "[COLOR=#333333][FONT=monospace]/etc/X11/Xsession.d/99x11-common_start: line 5 exec: init: not found"[/FONT][/COLOR], seemed Xession never was initialised. 

Changes to .profile made it work as explained to the post above.

Tc all!

---

