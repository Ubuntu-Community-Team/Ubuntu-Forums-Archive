---
title: "Help Installing Ubuntu as first operating system!!"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by Andres_Carbo on 2014-02-22
I've been trying to download ubuntu to my new custom build computer and I simply cant figure out why it wont allow me to and i'm getting very frustrated... I've searched the forums for answers and I haven't found one.. Im have no OS downloaded on this computer and I don't have a hard drive either and I am using a USB as my way of booting up the Ubuntu Installer. The size of the USB is 8GB.. I changed the bios and booted from usb and everything went well, I even tried out Ubuntu using the try Ubuntu option and it worked perfectly fine.. Now when I try and Install ubuntu I come to the Installation type window where it shows a box with nothing in it a couple unclickable grayed out buttons underneath it one says (new partion table)... Nothing is clickable except the drop down "Device for boot loader installation" which has only one option "/dev/sda"... Since I cant click anything else except that and "quit","back" and "Install Now" I click Install Now and a popup comes up saying " No root file system is defined. Please correct this from the partitioning menu." I've Tried with various versions of Ubuntu and keep getting the same thing... I've seen videos of people downloading Ubuntu to there computer without a hard drive and without a previous OS and they seem to get an extra Installation type window that says "This computer currently has no detected operating systems. What would you like to do?" and then lists various options.. Why don't I get this window? I would really appreciate the help, Thanks in advance to anyone that replies..

---

### Post by Vladlenin5000 on 2014-02-22
Hi, welcome!

Dumb question: If you don't have an HDD in that computer where exactly do you intend to install the OS (Ubuntu or any other for that matter)?

(additional info)
Although it's possible to install it and boot from a mass storage which isn't a HDD or SSD, let's say from a common USB flash drive like the one you're using to run the live session from there are (at least) a couple of things you should know:

1. Possible isn't the same as recommended, far from it. A full desktop OS running from a USB flash is barely usable, slow beyond belief. There are specialized ultra-lightweight distros 'designed' for that specific scenario, like Puppy Linux (at least one of their versions is based on Ubuntu), but Ubuntu itself certainly isn't one of them.
2. You can't under any circumstance install it to the same USB flash drive you're running the live session (or installer) from. Period.

---

