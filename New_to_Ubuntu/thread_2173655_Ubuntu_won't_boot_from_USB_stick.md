---
title: "Ubuntu won't boot from USB stick"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by robert31 on 2013-09-10
[FONT=century gothic]Hello I'm new to Linux, I cannot get Ubuntu to 'boot' from my Lexar usb stick.
I followed this video on the major parts, [http://www.youtube.com/watch?v=ilGBGLejvfM](http://www.youtube.com/watch?v=ilGBGLejvfM), 
but he was on puppy OS so he did it differently.
I downloaded Ubuntu and then formatted my usb to FAT32 and partitioned it for Linux-swap 199mb using gparted.
I then extracted the Ubuntu .iso from the archive to the usb stick and then rebooted the computer
and pressed F10 to change boot order to the USB and it didn't work.
What did I do wrong? Also where can I learn how to use Lubuntu LXLE?

I'll include some screen shots of the usb in gparted and the usb installer.

**I'm trying to get Ubuntu on my usb because Lubuntu lxle isn't running 'right' on my Emachine W3107
for some reason or another. I'm guessing it's hardware related but I'm only speculating. 
I'm hoping that Ubuntu will run a lot faster on my computer since it's only 900mb in size and Lubuntu LXLE is 1.3GB.

Computer specifications are:
[/FONT]

[LIST]
[*] Processor AMD Sempron 3100+ / 1.8 GHz 
[*] Memory 620 MB 
[*] Hard Drive(s) 13 GB hard drive / Quantum 20 GB Fireball hard drive 
[*] Operating System Lubuntu LXLE 12.04 
[*]Unknown replacement disc drive 
[*] Graphics Processor NVIDIA GeForce 6100 Shared video memory (UMA) 
[*] Graphics Controller Integrated 
[/LIST]
[FONT=century gothic]
[/FONT]

---

### Post by oldfred on 2013-09-10
Just copying the ISO or even extracting the ISO yourself does not create a bootable USB flash drive. You may have all the files but never added syslinux to MBR.

Better to just use the tools that do all that for you like unetbootin.
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

      
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
Common USB BIOS boot options
[http://www.pendrivelinux.com/usb-bios-boot-options/](http://www.pendrivelinux.com/usb-bios-boot-options/)

---

### Post by geekrod on 2013-09-11
Other option is that you install Grub2 to USB and directly boot an iso file [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

Note that it will act as a Live CD so changes will not be saved, which is fine for testing purposes. If you want permanent changes create an ext2 partition named casper-rw, and add *persistent *to kernel parameters on grub.cfg

---

### Post by robert31 on 2013-09-11
Thanks I'll give this a try soon but as for now work has got me preoccupied so I'll have to put it off.

---

