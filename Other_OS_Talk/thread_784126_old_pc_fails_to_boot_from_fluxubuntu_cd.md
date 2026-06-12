---
title: "old pc fails to boot from fluxubuntu cd"
date: 2008-05-06
forum: Other OS Talk
---

### Post by anfractuosities on 2008-05-06
I am trying to install fluxubuntu on my rents 500mHz mmx 256mb RAm pc.  When I boot the computer with the disc in the drive it comes up as failed.  It works fine on my laptop.  Also the Xubuntu disc boots fine on my rents pc.

any idears?

also ran check disk for errors and it is fine(on my laptop)

---

### Post by kerry_s on 2008-05-06
to little info

make,model?
can it boot from cd?
do you have it set to boot cd?

---

### Post by anfractuosities on 2008-05-06
It has been rebuilt.  It has a Celeron 500mHz MMX and 256 MB RAM, an MSI motherboard.  It was originaly a gateway2000, but everthing has been replaced, sans the case.

  It can and does boot from the cd rom.  I have installed xubuntu on it and it boots from the disk just fine, but xubuntu runs too slow.  I am going to try an older distro, but I would like to try fluxbuntu first.

---

### Post by kerry_s on 2008-05-06
you should go custom to get the most of the old rig. build it from the base up with only what you use.

i assume you have the alternate disk? (any ubuntu version)

do the command line install. after thats done, install X and the beginning of your build.
[B]sudo apt-get install xorg gdm fluxbox menu synaptic
sudo update-menus
reboot(ctrl+alt+delete)[/B]

select fluxbox in the session menu, log in, open synaptic and get what ever else you use. try to use gtk2 and light alternative programs.

i use a custom debian install on 450mhz 256mb ram, i find debian works better on my old rig, anyways nothing slow on mine.

---

### Post by anfractuosities on 2008-05-06
thank you much...I will give it a try...

---

