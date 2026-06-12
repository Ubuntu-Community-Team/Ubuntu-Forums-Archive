---
title: "remove encrypted Ubuntu 18.04.2"
date: 2019-07-22
forum: New to Ubuntu
---

### Post by coryn112 on 2019-07-22
I installed Ubuntu and completely removed Windows 10 from my very old laptop, hoping it would increase performance and speed.  Unfortunately, it is running even slower yet. (I've always been a fan of Ubuntu and just figured it would work out).  I have attempted to install another OS, but it won't work, because the hard drive is encrypted.  Reading the foums some people suggested to just install Ubuntu again.  That doesn't work either.  (What happens is it tried to install, then kicks it out, brings me to my hard drive password, and boots the OS).  There is nothing on it that i need.  I'd like to simply wipe it out to install an OS that is much simplier and not bogged down to bring life back to the computer.  

is it possible to decrypt the hard drive?   Can i just format the machine?  what are my options and what is the easiest way to go about this?  My knowledge is limited.

Thank You.

Coryn

---

### Post by Autodave on 2019-07-22
Can you please give us some specs or at least the make and model of your laptop?

---

### Post by Rubi1200 on 2019-07-22
Did you install Ubuntu using LUKS/LVM on the whole drive? How large is the disk?

---

### Post by uRock on 2019-07-22
I recently installed over a previously encrypted drive. I used the Debian Installer, which is different from the ubuntu installer. If your installers aren't seeing the drive, then you may be able to boot any live image that has Gparted on it, which ubuntu's does, and repartition the drive before running the installer. This is provided you aren't trying to preserve any of that data.

Plan D would possibly be to leave the ubuntu there and install LXDE within it. This will give you a much lighter desktop environment.

---

### Post by coryn112 on 2019-07-25
Sorry,  Its been years since i've been on a forum had to remember how to find my post again...

the laptop is quite old.  It's the original dell duo.  I believe it is this one   [https://wiki.archlinux.org/index.php/Dell_Inspiron_1090_(Duo)](https://wiki.archlinux.org/index.php/Dell_Inspiron_1090_(Duo))   All stickers and identies have worn off.  To answer a below question, I did completely wipe it out and replaced windows 10 with Ubuntu.   I have since been able to remove the encryption version and I have downloaded and installed other versions of ubuntu (Lbuntu, xbuntu)  I'm honestly not happy with them.  
Should Ubuntu run smoothly on my old dell?  if so, what do i need to do to make it run smoothly?   Thank You very much!

---

### Post by Rubi1200 on 2019-07-25
It seems funny but everyone has a slightly different experience with these kind of situations. No one size fits all.

I recommend trying the following to see if they work with your laptop and if you like the look and feel generally:

Ubuntu MATE

MX Linux

ArcoLinux

I have found them all to run quite nicely on an older laptop.

Worth trying I think.

---

### Post by coryn112 on 2019-07-25
Thank you so much Rubi.  I will try those.   :)

Coryn

---

