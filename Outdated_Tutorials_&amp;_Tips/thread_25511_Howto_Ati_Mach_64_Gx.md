---
title: "Howto Ati Mach 64 Gx"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by ankitmalik on 2005-04-10
Hello

If any one of you has a buggy ATI MACH 64 GX card which is not recognized by Ubuntu follow the instructions to set it up >


Boot into Ubuntu Hoary Recovery Mode [you get this option @ GRUB during booting

$ cd /usr/X11*/bin
$./xorgconfig

Go through the complete Configuration answering each question one by one and when asked for the Video Driver, use the VESA Driver
Number for Vesa Driver = 0

After the file is written, 

$ sudo /etc/init.d/gdm restart

Now Ubuntu must work for you but not so snappy due to the VESA driver you are using. In that case you probably have two options AFAIK

a) Get a better card

b) Get Scitech drivers : they are free for non commercial use but you need to register!

After grabbing the Scitech Driver for ATI MACH 64 GX run the installer for the driver and then in the xorg.conf file 

replace vesa with scitech

There you go, a more responsive desktop with ATI MACH 64 GX and Ubuntu Hoary/Warty!

---

