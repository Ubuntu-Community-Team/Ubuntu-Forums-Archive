---
title: "Doing everything to install Xubuntu"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by iamsabs on 2008-07-29
Hey everyone!

I've been trying to install Xubuntu 8.04 on my dad's Packard Bell Easynote XS20 (which doesn't have an optical drive), but I keep on failing miserably.

Right now, I've been trying to boot Xubuntu from a USB flash drive (via UNetBootin). But I can't get to the installation menu because after the loading screens appear, the screen freezes (with these strange colors at the upper half of the screen). Actually, this has been happening with every method of installation I tried. I'm not so sure, but this may be caused by this BIOS error #81[4943500] or something like that.

I really need help because I really wanna install Xubuntu (since XP Home is too slow on the XS20). 

Hope you guys can help me. :)

(BTW, my mom bought the XS20 last April. It runs on a 1.2 GHz VIA C7-M processor with about 1GB of RAM and VIA VX700 integrated graphics)

---

### Post by overdrank on 2008-07-29
> **iamsabs said:**
> Hey everyone!

I've been trying to install Xubuntu 8.04 on my dad's Packard Bell Easynote XS20 (which doesn't have an optical drive), but I keep on failing miserably.

Right now, I've been trying to boot Xubuntu from a USB flash drive (via UNetBootin). But I can't get to the installation menu because after the loading screens appear, the screen freezes (with these strange colors at the upper half of the screen). Actually, this has been happening with every method of installation I tried. I'm not so sure, but this may be caused by this BIOS error #81[4943500] or something like that.

I really need help because I really wanna install Xubuntu (since XP Home is too slow on the XS20). 

Hope you guys can help me. :)

(BTW, my mom bought the XS20 last April. It runs on a 1.2 GHz VIA C7-M processor with about 1GB of RAM and VIA VX700 integrated graphics)

Hi and welcome. I have never install Ubuntu but with the live cd or alternate. But what may be giving you the issue I believe is the VIA graphics. If there is anyway you could do like a safe graphics mode or remove the quiet splash from the kernel line and maybe add vga=775. It may help with the installation.

---

### Post by iamsabs on 2008-07-29
> **overdrank said:**
> Hi and welcome. I have never install Ubuntu but with the live cd or alternate. But what may be giving you the issue I believe is the VIA graphics. If there is anyway you could do like a safe graphics mode or remove the quiet splash from the kernel line and maybe add vga=775. It may help with the installation.

Uh, I'm not really sure how I can do that. :confused:

---

### Post by overdrank on 2008-07-29
> **iamsabs said:**
> Uh, I'm not really sure how I can do that. :confused:

Yea I may have to take a better look and see what I can find and maybe someone else will come up with a better idea.:)

---

### Post by halitech on 2008-07-29
I believe the way to make the changes is when it starts to boot and you get the grub screen, press 'e' to edit and then you can make the changes overdrank has suggested

---

### Post by iamsabs on 2008-07-30
> **halitech said:**
> I believe the way to make the changes is when it starts to boot and you get the grub screen, press 'e' to edit and then you can make the changes overdrank has suggested

I'm not sure about what the grub screen is. :confused:

So far I've tried pressing 'e' on every screen I know and nothing happens. :(

**[edit]** Nevermind. I was able to access the edit menu now. :)

---

### Post by iamsabs on 2008-07-30
I clicked "Start installer in safe graphics mode", but now I'm experiencing this command prompt-like thing ("BusyBox v1.1.3...Enter 'help' for a list of built-in commands")

---

### Post by overdrank on 2008-07-30
> **iamsabs said:**
> I clicked "Start installer in safe graphics mode", but now I'm experiencing this command prompt-like thing ("BusyBox v1.1.3...Enter 'help' for a list of built-in commands")

Ok after removing the quiet splash and adding the vga  add noapic.
before the --

---

