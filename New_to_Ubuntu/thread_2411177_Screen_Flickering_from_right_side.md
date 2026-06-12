---
title: "Screen Flickering from right side"
date: 2019-01-26
forum: New to Ubuntu
---

### Post by shilpapandey on 2019-01-26
My ubntu screen is  flickering and I have the following state of my system.  Its flickering from right side like shadow for few seconds in half an hour. 
Kindly help me if any software issue is there or hardware.


shilpa@shilpa-PC:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
shilpa@shilpa-PC:~$ uname -a  
Linux shilpa-PC 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
shilpa@shilpa-PC:~$ lspci -nnk | grep -iA2 vga 
00:02.0 VGA compatible controller [0300]: Intel Corporation Broadwell-U Integrated Graphics [8086:1616] (rev 09)
    Subsystem: Hewlett-Packard Company Device [103c:2296]
    Kernel driver in use: i915
shilpa@shilpa-PC:~$ env | grep DESK
DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity

---

### Post by Autodave on 2019-01-26
It could be either or both.  Is there a chance of borrowing a monitor off of a friend?  That would tell you quickly.  In the interim, have you checked connections at the monitor and the PC?

---

### Post by jdeca57 on 2019-01-27
Another idea is to use a live DVD/usb and boot another version of Ubuntu, like 18.04. That would also rule out a software problem. But older hardware can fail and a cable is usually a low-cost way to exclude a source  of problems.

---

