---
title: "exeption Emask problem pls hlp!"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by mayardjembe on 2008-05-22
Hi!
I am a very very happy Ubuntu user, with no much knowlege though:)

I have this problem:
my sistem crashed after trying to use xine, had to do a hard reboot, after that can't get the login screen. Just the mouse pointer, no login space, no other oprtions not even the UBUNTU text, only the background color.
When I try ctrl-alt-f1 or any other while booting there are no errors until it is ready to show the login screen that never show.
After a little bit i get something like this

ata1.00 status DRYERR
exeption Emask 0x0 Sact 0x0 Serr 0x0 action 0x0 BMDA stat 0x25 cmd c8

at the end is e4 tag Ddma 4096 in

I have tryied the dpkg broken packages from the recovery boot, the xorg recoverer, 
also apt-get remove gdm ubuntu-desktop, with this i could log in a terminal otherwise i wouldn't and then install it with apt-get install gdm ubuntu-desktop.
Also i tryed dpkg-reconfigure X11-common and dpkg-reconfigure -phigh xserver-xorg
oh yes! and also the e2fsck -f-y-v from the live cd



so far is what i have found on diferent forums but still no login screen...

pls hlp

thank you in advance...

---

### Post by mayardjembe on 2008-05-22
Btw i have a packard bell easy note R4 celeronM notebook

using one partition for win xp (i know i know):mad: and another for UBUNTU 8.04

any comments?

---

### Post by mayardjembe on 2008-05-26
Ok by removing gdm and ubuntu-desktop using the root applicatin on the recovery boot it is possible to log in...
mmmh now loged in lets find out how to solve the problem or back up to make a new installation of the system

I don't know why but i feel like xserver could be the problem...

i will try

sudo apt-get remove xserver-xorg-core

hope this would do

---

### Post by mayardjembe on 2008-05-27
No answers? = No solution found, 

sudo apt-get remove xserver-xorg-core didn't worked
:( reinstalling the system


Thank you any way...

---

