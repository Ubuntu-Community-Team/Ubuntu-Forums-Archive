---
title: "HP Color Laserjet 2500n on network"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by rockinlinux on 2008-08-01
Hello,

Today i sent up a new network that has two printers on it wired in. The monochrome printer works just fine on all the linux boxes and windows boxes. For a while today all computers could also print to the color laser printer, but now they can only print the "test pages" and not from any programs. I have been in the web admin of both printers and know their IP's. The network is running DHCP but i have covered that end and am fairly certain the problem is not coming from the DHCP settings. Any help would be great.

Thanks for your time.

:)

---

### Post by rockinlinux on 2008-08-01
when trying to print form "eye of gnome" i gat a error that says:

open device failed; retry in 30 seconds.

I can print form firefox and test pages fine...just not anything else.

---

### Post by rockinlinux on 2008-08-01
home@home-desktop:~$ lpstat -p
printer HPColor now printing HPColor-167.  enabled since Fri 01 Aug 2008 12:05:43 PM MDT
        open device failed; will retry in 30 seconds...
printer ml2570 is idle.  enabled since Fri 01 Aug 2008 12:10:16 PM MDT
home@home-desktop:~$

---

### Post by phidia on 2008-08-01
Have you installed the hplip package and tried to set up that printer using the interface for hp devices?

---

### Post by rockinlinux on 2008-08-03
well acording to my system hplip is installed but i hve not set up the printer with it. please give a little more info on how i would do this.

Thanks!

---

