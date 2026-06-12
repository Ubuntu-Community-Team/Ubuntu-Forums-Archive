---
title: "Name a lot of beginner distros for me please..."
date: 2008-06-21
forum: Other OS Talk
---

### Post by Fzang on 2008-06-21
I've tried Ubuntu but nothing on the computer is compatible with Ubuntu it seems....

Currently I have Mandriva installed as 2nd OS in a dual boot, it's awesome! The live CD detects ALL my hardware and I can use the internet, sound and compiz fusion out of the box... but it just won't boot! I don't know if it's me or the OS... the live CD wouldn't boot either, and I'm starting to think that it isn't my CD drive anyways..

So, any other beginner distros I could check out for hardware compatibility?

---

### Post by wh0rd on 2008-06-21
You can try [Fedora]("http://fedoraproject.org/"), I've had better hardware compatiablity with it out of a fresh install. They also have a good [support community]("http://fedoraforum.org/") like Ubuntu.

---

### Post by Fzang on 2008-06-21
Which version do I have to download if I want a 32 bit version? My CPU is 64 bit, but I've heard that you need a ton of RAM, otherwise 64 bit is bad

---

### Post by wolfen69 on 2008-06-21
> **Fzang said:**
> Which version do I have to download if I want a 32 bit version? My CPU is 64 bit, but I've heard that you need a ton of RAM, otherwise 64 bit is bad

no, it doesnt need a ton of ram. if you have 512 or more, you will be just fine. and no, 64bit is not bad, it is just different. unless you have a specific need for it, you are better off staying with 32bit.

---

### Post by LaRoza on 2008-06-21
OpenSUSE is very good. Maybe PCLinuxOS is worth checking out as well.

You should have the hardware in question for better responses.

---

### Post by 67GTA on 2008-06-21
Mepis, or PCLinuxOS. Do as LaRoza suggested. Boot the live CD, open a terminal, and post the output of ```
lspci
``` Linux doesn't run on "all" hardware. We might be able to help more if you can supply this info.

---

### Post by mivo on 2008-06-21
> **Fzang said:**
> Which version do I have to download if I want a 32 bit version? My CPU is 64 bit, but I've heard that you need a ton of RAM, otherwise 64 bit is bad

You are mixing up two different things. :) The "tons of RAM" comes from the fact that if you have 4 or more GB of RAM, a default 32-bit kernel (or Windows) doesn't see/use more than about 3.2 GB. So if you have 4 GB or more, and need it, a 64-bit OS is a good approach. The other aspect is that a 64-bit OS with 64-bit apps uses a little more RAM. It was roughly about 10% more in my own tests on my own box. 

So, no, you don't need a ton of RAM for 64-bit and unless you have less than 1 GB, the slightly higher RAM usage doesn't have a practical impact.

(But it is likewise a bit of a myth that 64-bit makes a noticeable difference in speed. It only does for a small number of applications/tasks, i.e. compiling lots of code, video encoding, etc. -- the very computing intense stuff that the average home user never or only very rarely does.)

---

### Post by starcannon on 2008-06-21
[Ubuntu]("http://www.ubuntu.com/")
[Linux Mint]("http://www.linuxmint.com/")
[Mandriva]("http://www.mandriva.com/")

In my personal order these are my top 3 picks, your already using one of them. 

If your happy with Mandriva, and things are working, but you just want to try other distro's it might be a good idea to find an old beater for just that purpose, or another hdd to use as a toybox.

Use what you like, and like what you use.

GL

---

### Post by kk0sse54 on 2008-06-21
Mepis and PCLinuxOS are good beginner distros that you might want to check out.

---

### Post by cardinals_fan on 2008-06-21
OpenSUSE is good, if a bit bloated.  OpenSolaris is excellent if your hardware is supported; if not, you're screwed.

I'm a bit confused by your idea of a 'beginner distro'.  Arch could be considered a great beginner distro because of its documentation, but it does involve some commmand line work.

---

### Post by Fzang on 2008-06-21
Thanks, I'll get downloading tomorrow

Currently I'm struggling with having Mandriva even booting, I have absolutely no idea what's wrong and it's driving me crazy, because windows will boot..!

---

### Post by Nessa on 2008-06-21
I think all distributions with Live CD's would be ok for a beginner. So you can try it first before you install. That would more or less give you a feel of the OS and tell you if it supports your hardware.

[http://en.wikipedia.org/wiki/List_of_LiveDistros](http://en.wikipedia.org/wiki/List_of_LiveDistros)
[http://en.wikipedia.org/wiki/Comparison_of_Linux_LiveDistros](http://en.wikipedia.org/wiki/Comparison_of_Linux_LiveDistros)

---

### Post by Fzang on 2008-06-22
With "beginner distro" I'm thinking of something like ubuntu that's said to "welcome" windows users, as much GUI based as possible and not a ton of command line work

Sounds weak doesn't it? :KS

---

### Post by cardinals_fan on 2008-06-22
> **Fzang said:**
> With "beginner distro" I'm thinking of something like ubuntu that's said to "welcome" windows users, as much GUI based as possible and not a ton of command line work

Sounds weak doesn't it? :KS
OK, I guess that doesn't really fit Slackware :)

Still, you'll learn more about Linux (and to some degree UNIX) from using Slack than just about anything else.

---

### Post by regomodo on 2008-06-22
Mint, PCLOS, Ubuntu, Fedora, Mandriva, OpenSuse, Lin/Freespire (if they exist anymore)

---

### Post by lisati on 2008-06-22
> **Fzang said:**
> <snip>not a ton of command line work<snip>
:) I can relate to that!

I got flummoxed this morning by my laptop unceremoniously presetnting the command prompt during boot up (I wonder if powering up an external DVD writer AFTER powering up the laptop had anything to do with it) and found myself unconsciously reverting to the equivalent of the old MS-DOS trick of going for the "big red switch" (the power switch). Old habits can die hard - tomorrow I'll have to remember to let the first fix of caffeine and nicotine for the day kick in properly.

---

### Post by kazuya on 2008-06-23
Mepis would be my first recommendation.- based on debian
Linux Mint would be my second - based on Ubuntu
Pclinuxos would be my third. - one of the easiest rpm distros to use.

---

### Post by agray on 2008-06-23
I'd say Ubuntu is one of the easiest, and definitely Mint as well.  Mandriva's pretty nice, so you'll have to learn about rpm's if you're used to deb's but not much difference.  OpenSUSE11 is alot better that 10.3 as far as package management. but, yeah it depends on what you're after specifically.

---

