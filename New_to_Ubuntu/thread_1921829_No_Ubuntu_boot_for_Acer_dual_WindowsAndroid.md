---
title: "No Ubuntu boot for Acer dual Windows/Android"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by skadish on 2012-02-07
Hi, I successfully created a bootable USB stick as described here (hoping to finally try Ubuntu for the first time):

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Everything went fine, until the installation asked to restart the computer. But when it restarted, there was (and still is) no opportunity to boot from Ubuntu.

I think I even understand what causes the problem, but I don't know how to solve it. You see, my small laptop is an Acer computer that came with a dual installation of Windows and Android. It has a special Windows program that allows choosing one of two options: Either boot directly to Windows from startup or else directly to Android (in the second case Android will start but revert to Windows in a certain number of seconds if no key is pressed). But in either case (if I understand correctly), the program doesn't allow the computer any other boot options because it is immediately directed to either Windows or Android.

The screen never gives any options or opportunity to edit BIOS; it is blank for a second or two after startup and then immediately begins loading Windows or Android.

Anyone have any suggestions?

---

### Post by trozamon on 2012-02-07
If there's no splash screen that shows what keys can be pressed to get into BIOS, I would just boot up then press F1-F12, Delete, and Escape until you get to BIOS. It's a haggard solution, but it can work.

---

### Post by QIII on 2012-02-07
Consult your documentation.  Surely there is a way to get to your BIOS.

Rapidly striking the DEL key is common.

Does your BIOS allow an option to boot from USB?

---

### Post by Mark Phelps on 2012-02-08
I would also try to boot from that USB stick on another PC.

I've had mixed results with booting from USB sticks -- sometimes they boot, sometimes they don't.  As to HOW to create them, same results -- sometimes unetbootin works well, sometimes the Universal USB Installer from PendriveLinux.com works better.

---

### Post by Bodsda on 2012-02-08
Esc, Del, F2, F8, F10 and F12 are the most common hotkeys to getting into the bios or showing the boot selection screen

Failing that, if you give us the exact make and model of the device and the bios version (you can get this by using PC Wizard or CPU-Z from cpuid.com) and we might be able to find out what the correct key is.

Bodsda

---

