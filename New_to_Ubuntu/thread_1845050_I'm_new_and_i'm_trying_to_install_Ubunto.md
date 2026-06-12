---
title: "I'm new and i'm trying to install Ubunto"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by cohenelad on 2011-09-16
Hi to everyone,
I'm trying w/o any luck to install the Ubuntu 11.04 on my pc.
i tried everything think that i could think of but i'm still getting some error message.
if any one can help me that would be great.
I'm trying to install the Ubunto next to win7 so i can choose which one i want to work with.
I'll upload the log file. maybe it will help to understand what's the problem.

tnx
Elad

---

### Post by arochester on 2011-09-16
Googled: dual boot windows 7 and Linux

Look at e.g.[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

It's no good saying "some error message". You need to say exactly what the error message is...

---

### Post by Mark Phelps on 2011-09-16
If you have a PC that came with Windows 7 preinstalled, it's likely to already have the drive filled with the maximum of four partitions.  In that case, there's nothing the installer can do for you.

You can check that by booting from the Ubuntu CD, selecting the Try Ubuntu option, and when you get to a desktop, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list out the partitions on your drive.

---

