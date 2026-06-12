---
title: "[SOLVED] pc does not boot from CD drive at all"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by mac-i-bear on 2008-10-28
is there an alternate way to install ubuntu-DESKTOP

this is an old dell dimension xps d333
have tried every thing except installing a new CD

---

### Post by Titan8990 on 2008-10-28
Have you tried changing the boot order in your BIOS? I don't think I have seen a computer in the last 10 years that can't boot from a cd...

---

### Post by handydan918 on 2008-10-28
> **mac-i-bear said:**
> is there an alternate way to install ubuntu-DESKTOP

this is an old dell dimension xps d333
have tried every thing except installing a new CD

If you are having trouble with the live cd, try the alternative installer cd. It will sometimes boot on older hardware that has trouble with the live cd. 
The alternative installer is a text-based interface, rather than a full GUI, but it isn't too daunting.

---

### Post by sudo_chop on 2008-10-28
> **Titan8990 said:**
> Have you tried changing the boot order in your BIOS?... 
 
Or there should be a key to press to bring up a boot menu

---

### Post by LinuxFox on 2008-10-28
> **Titan8990 said:**
> Have you tried changing the boot order in your BIOS? I don't think I have seen a computer in the last 10 years that can't boot from a cd...True, it's something like this example, the default order may be...

Boot device 1: Floppy
Boot device 2: Hard Drive
Boot device 3: CD/DVD-ROM drive

The idea is to make the CD drive the first boot device, and keeping the hard drive second this way you can still boot your computer if no CD (or a CD without boot data) is in the drive.  I had to do this when I first tried Linux with Knoppix, a Live CD. ;)

---

### Post by Bölvaður on 2008-10-28
After turning on the computer you are normally able to able to press some special button, (depends on your motherboard maker, mine is F10 but I've seen most of the Fx buttons used)

When you press that button in the start, you are introduced to a *"strange"* menu. There you are some settings there which is called "Boot order" make sure cd or dvd drive is at top, and your harddisk is second. (well and also make sure booting from cd drive is enabled).

Now put the cd in, save and quit... it should reboot from the cd now :D

---

### Post by snowpine on 2008-10-28
I know it's not really an answer to your question :) but I would not personally recommend Ubuntu on a 333mhz Pentium 2. If you are going to go for it, you should at the very least max out your ram at 384mb, which is the bare minimum to install Ubuntu. 

There are many fine alternatives if you're looking for a Linux distribution for older hardware. Puppy and DSL seem to be the two most popular these days. Good luck!

---

### Post by oilchangeguy on 2008-10-28
> **mac-i-bear said:**
> is there an alternate way to install ubuntu-DESKTOP

this is an old dell dimension xps d333
have tried every thing except installing a new CD

please provide the specs of this computer. because unless it's been upgraded at some point, it lacks the ram needed to run ubuntu.

---

### Post by mac-i-bear on 2008-10-29
thank you all for your help
(1 ) it was a case of bad CD hardware, as soon as i replaced i was able to boot from CD and installed ubuntu-desktop...
to answer some of your notes, 
(2) the machine is old but has 512M of ram and launches ubuntu
(3) as soon as it came on there was a message with updates available and it took 2 hours to download them and installed them
will see how it goes later on
(4) there is a message at boot up saying that BIOS is old 1998 and does not make 2000 cut off and some variable needs to be forced
will try to capture the info and come back to the forum fir help

---

### Post by random turnip on 2008-10-29
Normally, when you boot you pc up you will see a screen with a list of buttons and what they do at the bottom of the screen (it only stays there for 2 seconds, so you'll have to be quick!) look for the one that says somehting like "boot options" or somehting along this lines and press the corrisponding button before it has chance to load up any further, and set it to load from CD.

---

