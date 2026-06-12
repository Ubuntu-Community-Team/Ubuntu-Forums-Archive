---
title: "operating systems, hard drives, cd drives...ugh"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by shredfitz on 2008-08-17
OK. So I just lost an installation of Hardy. 

I have an athlon64 3000, a Gigabyte ga-m61sme-s motherboard, dvd-rw drive and 1gb of ram. 160gb Hd. This computer was put together like 10 months ago.

I started it with Windows, switched to Ubuntu(This was not my first Ubuntu install though). 

I have since had several errors where I have to manually run fsck. Errors. Think that I have fixed them and move on, until something else happens.

Tonight, I did a manual restart, everything seemed to shut down and restart normally, but instead I received an error, something like this: Kernel panic - not syncing: No init found. Try passing init= option to kernel.

I searched for help online, but just decided to try a different hd. This drive is the 80gb SATA drive that came with the set-up.

I have two different xp discs and three different ubuntu discs. Nothing will set up. Windows won't copy files like ks.sys. Ubuntu hangs up and gives errors as well when I attempt installs.

I have tried two different hd's and I have tried two different dvd/cd drives. The discs work in my Thinkpad. 

Could it be the motherboard? This system is rather budget priced when I purchased it. frustrating. If you have any ideas, I appreciate your input. Thanks.

---

### Post by residualbit on 2008-08-17
try this...

put it the cd and do a fresh install, but instead of clicking the normal install link there should be another link to install with special parameters or conditions or something. anyway, choose that option and it should bring up a command line looking thing across the bottom of the screen, don't bother with anything that is typed there just add the phrase "noapic" to the end and install (minus the quotes). I had a different system setup on my old laptop but was receiving the same errors, so give it a try. hopefully it will help!

---

### Post by overdrank on 2008-08-17
Hi and my first thought would be to reset cmos. Then setup bios again and try to install again.

---

### Post by sabby on 2008-08-17
> **shredfitz said:**
> 
I have tried two different hd's and I have tried two different dvd/cd drives. The discs work in my Thinkpad. 

Could it be the motherboard? This system is rather budget priced when I purchased it. frustrating. If you have any ideas, I appreciate your input. Thanks.

It seems to be an issue with the memory modules. 

I had a similar issue earlier while I was using xubuntu on my Pentium 3 machine running on 2 x 128 MB SD-RAM memory modules. xubuntu would get hung up every time and had to run fsck during each startup.

When I tried to install windows I would get an error saying could not copy driver.sys during the initial setup of windows.

The solution was to identify the bad memory module. Once I isolated the faulty module, removed the module and was able to run the windows setup. Once completed, reformatted the HDD and reinstalled xubuntu and has been working fine on a single 128MB module (a bit slower though)

---

### Post by shredfitz on 2008-08-28
> **sabby said:**
> It seems to be an issue with the memory modules. 



That's what it was. Replaced memory with new stuff and everything is great now.

---

