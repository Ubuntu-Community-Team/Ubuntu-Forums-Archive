---
title: "What linux OS to use for my old PC?"
date: 2007-06-21
forum: Other OS Talk
---

### Post by fasoulas on 2007-06-21
I was wondering what linux distro will be best for my old {**500mhz 8g 64 ram**} pc

I like ubuntu i use it on my new pc for almost a year but my old pc it won't run so well so i need some suggestions about ubuntu variants for old pc's or other distributions....

I forgot to say that i want it to dual boot with my winXP installation that is on the 8gb drive so i prefer a distro that will use grub as a boot manager because i like it on my ubuntu

I will use the linux partition for surfing the internet and listeing to music i just don;t want to surf on the intenet with winXP

Please leave me our comments and suggestions

---

### Post by Pipboy2000k on 2007-06-21
Try "Xubuntu  [http://www.xubuntu.org/]("http://www.xubuntu.org/")

Its an Ubuntu "Lite" distro

just make sure you have xp installed first (er thats how i do it at least)

then just install it and the grub should work its magic on boot

---

### Post by fasoulas on 2007-06-21
> **Pipboy2000k said:**
> Try "Xubuntu  [http://www.xubuntu.org/]("http://www.xubuntu.org/")

Its an Ubuntu "Lite" distro

just make sure you have xp installed first (er thats how i do it at least)

then just install it and the grub should work its magic on boot

Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

what is the difference from standart and the aldernative install ??

can i make a standert installatiion?

---

### Post by ThinkBuntu on 2007-06-21
I'd recommend Zenwalk or Vector Linux. Both are versatile, modern OS based on Slackware and should run very well on your PC. You also may want to consider using Debian with an Xfce desktop. There's a single install CD you can use that will install Debian with only Xfce (no GNOME, etc.).

---

### Post by tgalati4 on 2007-06-21
Assuming this is a PIII, 500 MHz, and you have the slots, try upgrading the memory to 128 MB or 256 MB and then you can run Dapper with a standard install.  You will want to create a 500 MB or 1 GB swap drive so you can install if you manage to get 128 MB RAM.

If you have a 2-slot RAM machine, you can probably go to 512 MB (256 by 2).  If your memory is PC100, it's pretty cheap these days and you will have a machine that can run most modern distos.

---

### Post by chicoicho on 2007-06-21
oh man by new  pc and install ubuntu -300-500 $ for new pc

---

### Post by fasoulas on 2007-06-21
I will reply to all of you....

I said that this is my old PC i have a new fast PC i don't need another one...i just have that old pc sitting there doing nothing and i want to bring it back to life but i never said i need suggestions about new pc hardware.

If i wanted a hardware update i would have done it but i just want suggestions on linux distros that i can use with this specifications and thats all...

---

### Post by smoker on 2007-06-21
with those specs i would recommend either puppy linux or damn small linux,
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

i also wouldn't install xp on those specs, if you need windows, w98se or w2000 at most. xp will be a painful crawl on that system.

best of luck

---

### Post by Martin Witte on 2007-06-21
On such a system xubuntu should work (see [http://www.xubuntu.org/get](http://www.xubuntu.org/get)), you can install it using the alternate cd. A short description of the alternate cd is here: [http://nl.archive.ubuntu.com/ubuntu-cdimage-xubuntu/releases/7.04/release/](http://nl.archive.ubuntu.com/ubuntu-cdimage-xubuntu/releases/7.04/release/)

---

### Post by Adam_GUI on 2007-06-21
You can try fluxbuntu.
[http://fluxbuntu.org/](http://fluxbuntu.org/)
Not the most intuitive.  And certainly not the most up to date.

But it is stable.  And the system requirements should be close to nill.

---

### Post by freshmeatz on 2007-06-21
be a man, use slackware :P
with the minimal items of system hardware you have listed i would say at best you are stuck to a lower end desktop , like xfce ect on a small linux platform, many distros out there . best to list what hardware you actually have though to get a better idea of the system in question.

---

### Post by fasoulas on 2007-06-22
I am downloading the standart xubuntu iso...will i have problems installing it??

---

### Post by bvanaerde on 2007-06-22
As a response to the suggestions above... Minimum required amount of RAM (with a normal installation):
[INDENT](X)ubuntu: 128MB
ZenWalk: 128MB
VectorLinux: 128MB
FluxBuntu: 128MB
Puppy Linux: 64MB
DSL: 16MB[/INDENT]

I have recently [installed]("http://iezy.be/news/id/34/") DSL on quite an old laptop with only 32MB of RAM.

So my suggestion is: try Puppy Linux first, it should work. Maybe not as smooth as you'd like, but I'd try it anyway as it is a great distro, imo. If it doesn't work well, try DSL, this one will surely be fast enough.

---

### Post by fasoulas on 2007-06-22
> **bvanaerde said:**
> As a response to the suggestions above... Minimum required amount of RAM (with a normal installation):
[INDENT](X)ubuntu: 128MB
ZenWalk: 128MB
VectorLinux: 128MB
FluxBuntu: 128MB
Puppy Linux: 64MB
DSL: 16MB[/INDENT]

I have recently [installed]("http://iezy.be/news/id/34/") DSL on quite an old laptop with only 32MB of RAM.

So my suggestion is: try Puppy Linux first, it should work. Maybe not as smooth as you'd like, but I'd try it anyway as it is a great distro, imo. If it doesn't work well, try DSL, this one will surely be fast enough.

Thnx for the suggestoins but do these 2 distros intall grub loader because i want to dual boot with winXP??

---

### Post by Lord Illidan on 2007-06-22
DSL and Puppy may be harder than Ubuntu to work with, but whatever they install : grub, or lilo, it should be possible to dualboot. You're not going to get very far with XP on 64 mb, though. It will crawl.

---

### Post by bvanaerde on 2007-06-22
> **fasoulas said:**
> Thnx for the suggestoins but do these 2 distros intall grub loader because i want to dual boot with winXP??
DSL uses GRUB or LILO, it's your choice ([HOWTO]("http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk"))
Puppy Linux uses GRUB too. ([HOWTO]("http://puppylinux.org/wikka/HardDiskInstall"))

You'll have to create the partitions yourself... so make sure you don't delete your existing Windows partitions in the process ;)
The howto links I gave don't cover dual boot installation, but that shouldn't be a problem.

As said above: WinXP won't work that well :)

---

### Post by ThinkBuntu on 2007-06-22
> **bvanaerde said:**
> As a response to the suggestions above... Minimum required amount of RAM (with a normal installation):
[INDENT](X)ubuntu: 128MB
ZenWalk: 128MB
VectorLinux: 128MB
FluxBuntu: 128MB
Puppy Linux: 64MB
DSL: 16MB[/INDENT]

I have recently [installed]("http://iezy.be/news/id/34/") DSL on quite an old laptop with only 32MB of RAM.

So my suggestion is: try Puppy Linux first, it should work. Maybe not as smooth as you'd like, but I'd try it anyway as it is a great distro, imo. If it doesn't work well, try DSL, this one will surely be fast enough.

Debian: 20MB, although 48MB is recommended.

---

### Post by fasoulas on 2007-06-22
> **ThinkBuntu said:**
> Debian: 20MB, although 48MB is recommended.

Will my old pc work with debian and gnome??

what exactly do u mean??

---

### Post by fasoulas on 2007-06-22
And to all of u that say that XP doesn't work well i can asure u that it runs perfect without freezing after a few tweaks but i don't dare to use it on the intenet thats why i want linux because i know the power and the safety that it has

---

### Post by fasoulas on 2007-06-22
I am downloading now this iso

[http://cdimage.debian.org/debian-cd/4.0_r0/i386/bt-cd/debian-40r0-i386-xfce-CD-1.iso.torrent](http://cdimage.debian.org/debian-cd/4.0_r0/i386/bt-cd/debian-40r0-i386-xfce-CD-1.iso.torrent)

I think it is the basic debian system with xfce is that right????

I think it is the correct one but there is a whole list there of about 21 iso's

is that the correct one?

---

### Post by lintoon on 2007-06-29
I agree with smoker.  Puppy linux or Damn Small Linux.  Both are really good.  I found puppy to be surprisingly fast.  Vector Linux is also an option.  I tried it on a P2 400Mhz and it worked fine.  Not very fast but it worked OK.

I'm just surprised you have XP running on 64Mb RAM.

---

### Post by RAV TUX on 2007-06-30
[enlisy]("http://enlisy.com/en/index.php?title=Main_Page") is awesome also.

---

### Post by dizee on 2007-06-30
Puppy CE is a very good looking and fast distro from my experience with a pentium II with 96mb of ram.

---

### Post by deanlinkous on 2007-07-01
debian! it is as small and as lite as you make it....plus you can still add so much more ot make it anything you want.

---

### Post by totalnub on 2007-07-01
i'd love to see a screenshot of your xp system properties window. ya know right click my comp. -> properties

---

