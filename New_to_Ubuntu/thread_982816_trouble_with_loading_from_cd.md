---
title: "trouble with loading from cd"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by shadowseeker on 2008-11-15
hiya people, i am very new to linux and ubuntu, i am trying to load it from cd on my main computer but all i get is busybox v1.1.3 and i dont know what to do from there. i downloaded the disk from the ubuntu site and i have had it booting from cd on my laptop so i know it works.is there some command i have to type in to get it working
thanx

---

### Post by Peter09 on 2008-11-15
Hi Shadowseeker,
BusyBox is often the result of a poor CD. You seem to suggest that you have been booting from the CD on other systems, might be worth checking that it is still bootable from them.

What are the specifications of the machine with the problem.

CPU?
Mem?

What is the O/S and CD you are using, is it the LiveCD and Ubuntu Hardy or Intrepid?

What error messages are you getting?

---

### Post by shadowseeker on 2008-11-15
hiya, im running a amd athlon 64 dual core 4200+ with 2 Gig ram and a 300 Gig hard drive.
ive just tried running the disk on another machine and it wont even boot on that let alone bring up busybox....guess i'll just have to burn another disk

---

### Post by blackened on 2008-11-15
This is a common problem. Try burning it at a slower speed, 4x usually works well for me.

---

### Post by shadowseeker on 2008-11-15
is there a program that people tend to recommend for burning....im using nero

---

### Post by Peter09 on 2008-11-15
Not sure fr Windows, plenty of options in Linux:)

Just burn it slowly and check it if you can get to the menu when it boots.

---

### Post by blackened on 2008-11-15
I prefer GnomeBaker.

---

### Post by endokendo on 2008-11-15
Hello everyone, I have the same error message during install on an old desktop PC (Intel Celeron, speed = not sure, has a 20 GB hard drive, 256 MB RAM, originally had Windows ME on it and it is able to surf the web). The error message is as follows:

BusyBox v.1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)

At the present moment, I am stuck and don't know what to do next.

I get this exact same error message if I try installing Xubuntu, Ubuntu 8.04 LTS, or Ubuntu 8.10 on this same computer, all from bootable CDs downloaded from the [www.ubuntu.com](www.ubuntu.com) website.

I have used these same install disks on other laptop PCs and installation was successful.

Therefore, what is wrong about this old desktop PC and why do I get the BusyBox error message? I have tried the following after reading through the forums:

Hit F6 at start up screen and delete "quiet place" and replace with boot=break

Then I waited a few minutes, then did the modprobe piix, then enter, then exit, then enter, and now I have the following error message:

cp: cannot create '/root/var/log/': No such file or directory
Done.
Begin: Running /scripts/init-bottom ...
mount: mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


Many thanks in advance! I have now switched to Ubuntu and I definitely want to get Ubuntu onto this old desktop PC.

---

### Post by Peter09 on 2008-11-15
EndoKendo - What Spec's are your PC

---

### Post by shadowseeker on 2008-11-15
ive just downloaded the new 8.10 version of ubuntu and im trying to load it from cd to try it out first and its asking for a username and password.
i have not set one of these up so what do i put in it ???

---

### Post by blackened on 2008-11-15
Did you let the initial menu time out? If you don't choose a language and then a menu option (Try it out without installing, check disk integrity, check memory, etc) it will pass you on to gdm and ask for a login. Don't know why this happens, but I've experienced it when my keyboard didn't initialize on boot.

---

### Post by shadowseeker on 2008-11-16
first menu is the language which i choose english then you get the 4 options and i wanna run it from disk but then it comes up with a username and password.....is this some sort of universal username and password ??

---

