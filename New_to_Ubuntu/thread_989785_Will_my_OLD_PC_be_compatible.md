---
title: "Will my OLD PC be compatible?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by sqrooup on 2008-11-22
I was given on old PC, a Compaq Presario, the specs:

windoze 98
3GB hard drive
48MB ram
The CD ROM is no working, but I have a spare
Processor speed 333MHz
4 port USB (1.1 I would think, with windoze 98 I can't test them)
A dial up modem

I would like to recycle this PC (it would be a shame to throw it in the skip), making it into an Internet ready PC for charitable use, and I was thinking;

Xubuntu

What do you think my chances are of doing it (with a new CD ROM and a network card)? will it meet the Xubuntu specs?

---

### Post by ChanServ on 2008-11-22
mabey with xubuntu, but it's still under the bare min.
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by lykwydchykyn on 2008-11-22
I've run Xubuntu on machines with about twice those specs (128MB ram, PII 450) and it was miserably painfully slow.  

I'd recommend looking at an even lighter distro, like puppy or DSL. Or just install a minimal Debian stable and add xorg and icewm or jwm.

---

### Post by jay576 on 2008-11-22
needs more ram for xfce to run smoothly i would say

---

### Post by mikjp on 2008-11-22
> **sqrooup said:**
> Xubuntu

What do you think my chances are of doing it (with a new CD ROM and a network card)? will it meet the Xubuntu specs?

Your chances are around 0 % unless with Xubuntu unless you buy a lot more RAM. Try Slackware, Debian, or some distro especially meant for really old computers. I've used Debian 3.1 and Slackware with X on an P100 + 40 MB RAM, but I used it only for Emacs and LaTeX, not for browsing the web or using Openoffice.

You can use that for learning more about Linux, but if you give it away for someone with Linux preinstalled, the users will only think that Linux is crap, when the problem really is in the specs of the hardware.

Greetings, 

mikko

---

### Post by dazzled on 2008-11-22
Try Puppy Linux - 90 odd MB all up, which won't trouble your hard drive. There is some information in getting it tweaked to run with so little RAM here - [http://www.murga-linux.com/puppy/viewtopic.php?p=101137](http://www.murga-linux.com/puppy/viewtopic.php?p=101137)

I always keep Puppy on CD and USB stick just for repairs, disk and network testing etc, as it runs in RAM.    I doubt if you will give up Ubuntu for Puppy on a high end machine, but it leaves Windows in the shade.

---

### Post by roger_1960 on 2008-11-22
Hi

I agree, try Puppy (retro 4.1.1) its a great distro for min spec machines and usually works without messing around.  (I dont think you have a hope with Xubuntu with that RAM - if you can up it to 128M the alternate CD install may work)

---

### Post by davidsrsb on 2008-11-22
48 MB Ram is not enough to run X sensibly, but would be OK for text console mode
Your spec of PC could be fairly easily upgraded to 256MB Ram (probably 133MHz SDRAM) and run Puppy OK

---

### Post by stalkingwolf on 2008-11-22
I agree. try Puppy or DSL.

---

### Post by Neostar on 2008-11-22
You could also give some of these try...

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by ugm6hr on 2008-11-22
Puppy is a stretch for 48MB RAM - I tried 2.14 on 48MB, and it was essentially unusable.

DSL will work (at least v3 did fine) - and should be usable as an internet computer.

I gather DeliLinux is good for such systems too - never tried it.

In the end, I put DSL on mine and gave it away on freecycle UK to a mum home-schooling her daughter in Birmingham.

---

### Post by RandyNose on 2008-11-23
> **sqrooup said:**
> I was given on old PC, a Compaq Presario, the specs:

windoze 98
3GB hard drive
48MB ram
The CD ROM is no working, but I have a spare
Processor speed 333MHz
4 port USB (1.1 I would think, with windoze 98 I can't test them)
A dial up modem

I would like to recycle this PC (it would be a shame to throw it in the skip), making it into an Internet ready PC for charitable use, and I was thinking;

Xubuntu

What do you think my chances are of doing it (with a new CD ROM and a network card)? will it meet the Xubuntu specs?

If there is any way you can up the amount of ram in this thing, it will help no matter what you do.  Puppy Linux is also a good Tiny Distro, sorta funky to use if you're accustomed to WinX or Ubuntu's ..  In any event, you can easily put a Linux Distro on a flash drive and test it out..  If it's a test machine, and nothings going on with it, Hack away! HACK AWAY! That's the fun thing, IMHO...

---

### Post by RandyNose on 2008-11-23
> **ugm6hr said:**
> Puppy is a stretch for 48MB RAM - I tried 2.14 on 48MB, and it was essentially unusable.

DSL will work (at least v3 did fine) - and should be usable as an internet computer.

I gather DeliLinux is good for such systems too - never tried it.

In the end, I put DSL on mine and gave it away on freecycle UK to a mum home-schooling her daughter in Birmingham.

I think that 4.x of puppy has less RAM Requirements. Or at least that was one of the goals he had for it..

---

### Post by Tomatz on 2008-11-23
Try fluxbuntu:

[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)

Thats about as light as the 'buntu world goes. Unless you want to go CLI?

---

### Post by snowpine on 2008-11-24
> **RandyNose said:**
> If there is any way you can up the amount of ram in this thing, it will help no matter what you do.  Puppy Linux is also a good Tiny Distro, sorta funky to use if you're accustomed to WinX or Ubuntu's ..  In any event, you can easily put a Linux Distro on a flash drive and test it out..  If it's a test machine, and nothings going on with it, Hack away! HACK AWAY! That's the fun thing, IMHO...

Most Windows 98 era computers will not boot from a flash device, unfortunately. Definitely check your bios to see if this is a possibility before deciding to go this route.

---

### Post by snowpine on 2008-11-24
> **Tomatz said:**
> Try fluxbuntu:

[http://fluxbuntu.org/js.html](http://fluxbuntu.org/js.html)

Thats about as light as the 'buntu world goes. Unless you want to go CLI?

Fluxbuntu definitely will not run well with that computer; I would recommend 96mb minimum for Fluxbuntu, but even then there are other distros I would choose first.

In this case, I definitely think DSL is the best choice. Good luck!

---

### Post by Tomatz on 2008-11-24
> **snowpine said:**
> Fluxbuntu definitely will not run well with that computer; I would recommend 96mb minimum for Fluxbuntu, but even then there are other distros I would choose first.

In this case, I definitely think DSL is the best choice. Good luck!


The recycling centre would be best!

:lolflag:

---

### Post by Tomatz on 2008-11-24
or

[http://www.toms.net/rb/](http://www.toms.net/rb/)

:lolflag:

---

### Post by Wickd on 2008-11-24
Well I would say that FreeBSD is also a good alternative. I am busy setting up the m0n0wall firewall on a freeBSD pentiumm 2 with 64 MB RAM and a 200mhz processor

---

### Post by Tomatz on 2008-11-24
> **Wickd said:**
> Well I would say that FreeBSD is also a good alternative. I am busy setting up the m0n0wall firewall on a freeBSD pentiumm 2 with 64 MB RAM and a 200mhz processor

Free BSD and X? Or just CLI?

---

### Post by Wickd on 2008-11-25
Well I am only running CLI, but will give X a try this weekend and report back

---

### Post by randy78 on 2008-11-25
Slitaz: [http://slitaz.org/en/]("http://slitaz.org/en/")

---

