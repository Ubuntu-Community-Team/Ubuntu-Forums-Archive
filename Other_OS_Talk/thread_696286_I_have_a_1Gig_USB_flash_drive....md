---
title: "I have a 1Gig USB flash drive..."
date: 2008-02-13
forum: Other OS Talk
---

### Post by Pogeymanz on 2008-02-13
Here's what I want. I want to be able to stick it into a computer, reboot, and have a Linux OS; like a liveCD. 

But I also want to have a partition on it for storing files that I can share with a Windows computer, so I can just stick it into the computer and be able to get those files.

Is it possible to use gparted to make a FAT32 partition and do a USB install of Puppy or DSL-n on the rest of the stick? I'm not familiar at all with USB-installs.

---

### Post by jcwmoore on 2008-02-13
yes it is, I have done this several times, with several different Linux distros,
look here....
[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

I recommend using the custom distro, pendrive Linux, it is debain based and easy to get around in

---

### Post by HappyFeet on 2008-02-13
i did the persistent gutsy install, and it's great.  linuxmint on a stick is also pretty good.

---

### Post by SunnyRabbiera on 2008-02-13
Damnsmall should be able to do something like this too as it is great for limited spaces.

---

### Post by smartboyathome on 2008-02-13
> **HappyFeet said:**
> i did the persistent gutsy install, and it's great.  linuxmint on a stick is also pretty good.

Though for a 1GB, it is not so good, as there will be hardly any space to store files. :(

---

### Post by SunnyRabbiera on 2008-02-13
> **smartboyathome said:**
> Though for a 1GB, it is not so good, as there will be hardly any space to store files. :(

unless he/she wants to boot from the flash drive but keep the current system on his/her computer without risking ruining it.
I know many people who like to have a base system on their computers but use a flash drive to put the OS on to.
thumb drives are very good for when you are at work and dont have the room for a livecd.

---

### Post by kerry_s on 2008-02-14
go with DSL, you can boot it to ram from flash and then remove the flash. you could also just do that with the cdrom. 
can you spare 50mb of ram to run a linux os in ram? :)
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
try both 3.x and 4.x to see witch you like best

---

### Post by dptxp on 2008-02-14
use puppy linux.

---

### Post by Antman on 2008-02-14
> **dptxp said:**
> use puppy linux.

+1

---

### Post by Fred_E _krugar on 2008-02-14
I would vote for Puppy also.

---

### Post by Pogeymanz on 2008-02-14
Well, since I was leaning toward puppy anyway, I will go ahead and use that. But now I have more specific questions.

How much space will Puppy take up? I know the iso is about 100MB, but is that what it will be if I install it to the USB flash drive? Then, of course I will add apps to it, so it will be even bigger.

Also, should I have swap space? If so, how much? Should I put the puppy partition before or after my FAT32 partition?

---

### Post by smartboyathome on 2008-02-14
> **EmosSuck777 said:**
> Well, since I was leaning toward puppy anyway, I will go ahead and use that. But now I have more specific questions.

How much space will Puppy take up? I know the iso is about 100MB, but is that what it will be if I install it to the USB flash drive? Then, of course I will add apps to it, so it will be even bigger.

Also, should I have swap space? If so, how much? Should I put the puppy partition before or after my FAT32 partition?

It will only take up ~230mbs. You don't need much (if any) swap space if you have over 512mbs ram. You can just load the whole thing into ram. and it will be super fast.

---

### Post by Pogeymanz on 2008-02-14
I've decided against making a swap partition because I heard that writing to the flash drive more often than necessary is bad for it's life.

I'm in puppy LiveCD right now and for some reason Gparted is having so much trouble resizing the partition on the stick. I don't really want to delete the partition because apparently it has some neat software for windows that comes on it. 

Am I missing something? I tried to just shrink the FAT16 partition and leave blank space in front, but once the operation is complete, it shows the FAT16 taking up the whole thing again, as if it didn't do anything!

Then I tried to shrink fat16 and make an ext3 partition in front and I get an error: "Attempt to write sectors 128-128 outside of partition on /dev/sda"

---

### Post by smartboyathome on 2008-02-14
> **EmosSuck777 said:**
> I've decided against making a swap partition because I heard that writing to the flash drive more often than necessary is bad for it's life.

I'm in puppy LiveCD right now and for some reason Gparted is having so much trouble resizing the partition on the stick. I don't really want to delete the partition because apparently it has some neat software for windows that comes on it. 

Am I missing something? I tried to just shrink the FAT16 partition and leave blank space in front, but once the operation is complete, it shows the FAT16 taking up the whole thing again, as if it didn't do anything!

Then I tried to shrink fat16 and make an ext3 partition in front and I get an error: "Attempt to write sectors 128-128 outside of partition on /dev/sda"

Ugh, you got a U3 stick. Get rid of U3, it is crap. If you have a windows computer, run the uninstaller on it. Other than that, you are using the wrong partition (the U3 program makes the U3 partition look like a CD and you can't resize a CD).

---

### Post by Pogeymanz on 2008-02-14
Good call. I tried using the program stuff on it anyway; totally unnecessary. I just want to swap source code files and pictures anyway.

Anyway, all is good now that I got rid of that stuff. I feel like I paid for something that I don't even have anymore, though... The same reason I keep WinXP on my computer even though I never use it: I bought it, I should keep it! :)

---

### Post by init1 on 2008-02-14
> **smartboyathome said:**
> Ugh, you got a U3 stick. Get rid of U3, it is crap. If you have a windows computer, run the uninstaller on it. Other than that, you are using the wrong partition (the U3 program makes the U3 partition look like a CD and you can't resize a CD).
Agreed.
Edit:
I've got two that I received as gifts, so I'm stuck using them.

---

