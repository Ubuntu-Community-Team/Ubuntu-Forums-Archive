---
title: "Problems with GRUB"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by lucas19 on 2014-05-30
Hi, first of all sorry if my english is not perfect but I'm not an english native speaker.
The deal is that some weeks ago I've installed Ubuntu. Now, I want to change the SO for Linux Mint. But GRUB keeps on bothering me. I'm trying to install Linux Mint from a pendrive (that works, I've tested it on several computers). I do open the BIOS and put it first in order to boot it first but it keeps on showing me GRUB.
I think there's a way to make GRUB boot the pendrive. I just want to get rid of GRUB and install Linux Mint. (my GRUB version is 1.99, I do not know if that will help). I've been trying some commands and they do not work.
By the way, please, explain me like I'm five years old, I'm a begginer. Thanks

---

### Post by crip720 on 2014-05-30
Linux Mint should install the same way as you installed Ubuntu.  You download an iso to your computer and then write to dvd, or use Unetbootin to write to usb.  If you have installed Mint to your usb as an operating system, then to use grub, you should boot up Ubuntu,  insert the usb stick, and then try sudo update-grub. Grub will then give you a choice to boot into Ubuntu or Mint.  If Mint is written to usb stick, the first screen you should see the language choice, then the screen with the Try Mint or Install Mint buttons.  You can continue to install Mint if you like.  If these screens don't show, but you have the Mint desktop screen, then you have installed the operating system on the usb stick.  You will have to re download the Mint iso to installed to your computer.

---

### Post by q64ceo on 2014-05-31
Specs please

Plus, is it EFI boot or regular?

---

