---
title: "Kubuntu 13.10 taking forever to boot/load programs"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by Wackerman370 on 2013-11-11
Hey everyone,

  I've been using Kubuntu on and off for a few months, I believe I had 13.04 with similar issues, but never of this magnitude.  I decided to give it another try yesterday, and I followed a friend's advice to update to the latest Kubuntu (13.10 is what I have now).  This took 10 hours.  After doing this, I allowed the system to restart, and upon booting back up, I noticed it was taking a very long time.  Even opening Chrome to simply browse the web is a problem.  

On my last login, it took a full 10 and 1/2 minutes from selecting Ubuntu on the boot selection screen until I was able to open Chrome and type in the url for this forum. 
Some YouTube videos will not load.  Some images on webpages also will not load.  

My computer is an eMachines T5230.  2Gb of RAM, AMD Athlon 64x2 4400+ (I believe 2.3 GHz), onboard NVIDIA GeForce 6150SE, shipped with Windows Vista, upgraded to Windows 7 and the dual-boot with Kubuntu shortly thereafter once Vista took a dive.  

I still dual-boot with Windows 7, and it runs fairly well.  I'm interested in using Linux of some sort because I've heard great things, and I love the spirit of everything being open source, and the control over how it runs, etc. etc.  I am also interested in using Wine to run some form of Photoshop and possibly iTunes (unless there's a good alternative to iTunes I'm missing out on).  

My level of experience with Ubuntu is very novice, but I've built Windows systems and worked at an office supplier that sold computers for years, and my current job is as a video editor, so I'm not completely "computer illiterate".  

Thanks in advance for any help!

---

### Post by mastablasta on 2013-11-12
did oyu load proprietary drivers for the GPU? i hope they have them.
you can see what is occupying CPu using top command in terminal. you can copy and post output here. htop has a nice interface. 

anyway it seems like the GPU issue. one thing you could try if you can't get any better drivers is to install kubuntu low fat package. or just turning off a few things Akonadi, Nepomuk, special desktop effects.

btw unless you have a very slow internet connection your upgrade took extremely long. i have a 1.6ghz dual core low power CPU, 2 GB ram (512MB taken by onboard GPU) and upgrade took about 3 hours.

---

