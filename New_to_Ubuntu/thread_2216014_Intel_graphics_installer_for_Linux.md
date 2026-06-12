---
title: "Intel graphics installer for Linux"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by guber90 on 2014-04-09
Hi guys, first of all I'm ubuntu noob, so if I say something stupid sry, also my english is bad but I hope so you will understand me :).

I tryed runing Intel graphics installer for Linux, but when I run deb file, and install it I get this error after trying to update:

[IMG]http://pix.toile-libre.org/upload/original/1397063030.png[/IMG]

I really would like to update graphic card drivers cus I have a lot of odd bugs that I would say are graphic drivers related, like when I start ubuntu sometimes it "freezes" after log in and I have only black screen altought I can move cursor, or when I exit full screen youtube video I can't see bar where is clock ect.

This is some info if it would help you to help me :):

  ```
*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:90000000-903fffff memory:80000000-8fffffff ioport:5050(size=8)



```

---

### Post by grahammechanical on 2014-04-09
The 404 error indicates that the repository that you are trying to install that utility from does not exist. I do not understand what sopcast has to do with the Intel Graphic Installer. Are you installing the latest version or, perhaps an older version that is no longer supported? Hence the lack of a security key.

[https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux)

Regards.

---

### Post by guber90 on 2014-04-09
> **grahammechanical said:**
> The 404 error indicates that the repository that you are trying to install that utility from does not exist. I do not understand what sopcast has to do with the Intel Graphic Installer. Are you installing the latest version or, perhaps an older version that is no longer supported? Hence the lack of a security key.

[https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.4-linux)

Regards.
Well I must say thank you, problem was with that (sopcast) repo (I'm iPhone user so I think repo is valid name :)), after removing it all went well.

Thanks again :).

---

### Post by Coolgirl on 2014-04-09
ANy body know a good video explained the advanteges of linux over mac or windows? I have mac and windows and was thinking about going to linux

---

