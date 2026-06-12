---
title: "unbuntu with mint"
date: 2016-04-25
forum: New to Ubuntu
---

### Post by Allisterguy on 2016-04-25
Hi
I am running MInt 17.3 Rosa on a 32 bt pc, no windows.
I would like to run  Ubuntu 14 alongside Mint or instead of mint.
 I am unsure how to create a  bootable dvd disk for unbuntu on Mint
In the past all my linux distros have run with a bought dvd and booted from windows
This pc had windows removed before mint was installed
Can I download a 14.4 onto a dvd? or usb stick and how to get it onto thedvd/stick.
really appreciate any advice
A.C.G.

---

### Post by sudodus on 2016-04-25
- ***Backup*** everything important (personal files etc) because it is risky to install an operating system.

- ***Download*** the iso file and check with md5sum, or get it via torrent (which checks the md5sum automatically).

- ***Get a tool*** to install from the iso file to a USB pendrive. Tools that use the cloning method are reliable, for example [mkusb](https://help.ubuntu.com/community/mkusb).

See this link for more details: [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

It is also possible to burn the iso file to a DVD using a burning tool. ***k3b*** is a good burning tool. (Do *not* make a data DVD, you should *'burn the image'*, the result should be that you see a lot of directories and files, if you insert the DVD disk after burning. If you see one big file, the iso file, you used the wrong method.)

-o-

Do not install Ubuntu directly, instead you should

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

You can decide, if you want to use the automatic method to install ***alongside*** Linux Mint, or if you want to make partitions manually with ***gparted*** before installing. If you make partitions before installing, you select ***Something else*** at the partitioning window, and select the partitions that you created. It is a good idea to share the swap partition with Mint.

---

### Post by Allisterguy on 2016-04-25
Hi
thank you so much
I burned the image to disc and booted it from mint and did the try ubuntu first it seemed fine except for printer. I then installed Ubuntu along side Mint and   both work well except for my epson WF 2630 printer
This printer is an air printer and It works fine with my ipad but not with Mint or Ubuntu
Allister

---

### Post by sudodus on 2016-04-25
Please start a new thread about the printer in the [Ubuntu Hardware Forum](http://ubuntuforums.org/forumdisplay.php?f=332). That way you have better chances to get help.

If the problems of the installation are solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

---

### Post by buzzingrobot on 2016-04-25
Mint has a rather nice GUI tool to burn an install ISO image to a USB stick.  It's installed by default, so you should have it.  Download an ISO, plugin the stick, and have at it.

---

### Post by oldrocker99 on 2016-04-25
As far as burning a USB thumb drive for a bootable installation disk, I have never had a problem using unetbootin. Just make sure the drive is formatted as FAT, and it always works.```
sudo apt-get install unetbootin
```

---

