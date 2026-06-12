---
title: "[SOLVED] Error 21!!!"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by RoyHobbs on 2008-09-07
Hi

My Ubuntu 8.04 just froze up.  After waiting about 10 minutes and still nothing happening, I turned my pc off and went to turn it on again and I got the message

Grub Loading
Error 21

Then nothing at all!  Basically, this is all occurring before I even get to the menu to choose to use Ubuntu or Windows etc.  What do I need to do to fix this?  I can still boot off the cd I made, however I can't get into my already set up Ubuntu or Windows XP?  PLease don't tell me I need to reinstall Ubuntu!!!!!

---

### Post by Crafty Kisses on 2008-09-07
You can try using SuperGRUB to restore GRUB.

Try this link > [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)

---

### Post by RoyHobbs on 2008-09-07
> **Codename said:**
> You can try using SuperGRUB to restore GRUB.

Try this link > [http://supergrub.forjamari.linex.org](http://supergrub.forjamari.linex.org)

Hi

I tried super grub and everytime I tried reboot the grub or fix the mbr I kept getting 

error 15

SG did not succeed

Which I assume is not good!

---

### Post by RoyHobbs on 2008-09-07
Bump

---

### Post by Sef on 2008-09-07
Please wait 24 hours before bumping your thread.  Thank you.

How many hard drives do you have?

---

### Post by caljohnsmith on 2008-09-07
From your Ubuntu Live CD, please post the output of:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
You will probably get an error with one of the above Grub commands, so be sure to post the exact output.

---

### Post by RoyHobbs on 2008-09-07
> **Sef said:**
> Please wait 24 hours before bumping your thread.  Thank you.

How many hard drives do you have?

sorry :(

I only have one hard drive partitioned for windows xp / windows backup and Ubuntu.  I have a external hard drive attached via usb as well

---

### Post by RoyHobbs on 2008-09-08
> **caljohnsmith said:**
> From your Ubuntu Live CD, please post the output of:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
You will probably get an error with one of the above Grub commands, so be sure to post the exact output.

From the boot up from my Live CD I am unable to run the above script.  I paste the script into the terminal to run and I am unable to scroll back and forth through the response.  I have been trying to use the super grub CD (which has allowed me to boot into Windows) however it appears that the partition that I set up for my initial install of Ubuntu is no longer there?  I tried re installing Ubuntu from the live cd, however there was no longer the option to resize the partition when installing.  The only options where to write ove the full hard drive or to do it manually.  When I tried to partition the disk manually, I was not given the option to resize.  I am really concerned that I have fried the box....

---

### Post by caljohnsmith on 2008-09-08
> **RoyHobbs said:**
> From the boot up from my Live CD I am unable to run the above script.  I paste the script into the terminal to run and I am unable to scroll back and forth through the response.  I have been trying to use the super grub CD (which has allowed me to boot into Windows) however it appears that the partition that I set up for my initial install of Ubuntu is no longer there?  I tried re installing Ubuntu from the live cd, however there was no longer the option to resize the partition when installing.  The only options where to write ove the full hard drive or to do it manually.  When I tried to partition the disk manually, I was not given the option to resize.  I am really concerned that I have fried the box....
First off, since you are new to Linux, I can totally understand your idea of pasting the "script" into the terminal to run, but actually those commands are meant to be run one at a time. :) So if you can copy and paste them one-by-one, and let us know the output, we'll have a much better idea of how to help you at this point.

---

### Post by RoyHobbs on 2008-09-09
Hi

I'm not sure what I did, but after playing with SGD and going into XP I finally got Ubuntu back up and working!  Thank you everyone for your help!

---

