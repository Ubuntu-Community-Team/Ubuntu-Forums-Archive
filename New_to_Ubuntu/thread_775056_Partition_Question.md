---
title: "Partition Question"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Mad_Commander on 2008-04-29
Hello Folks

I have 2 HDD within my main PC and one Maxtor One Touch 4 500GB USB drive
I have XP installed in my Main Drive 120GB and My second drive is a 60GB (55GB due to MS 1024mb per GB and seagates 1000MB per GB) partioned into 3 primary partitions

Vista: 18.5GB Linux 18.5 Spare: 18.5 (drivers and stuff)

XP has been on my system for 6-7months and works fine. I desided that i realy should learn Vista and linux. (tho vista isn't all that diffrant from XP, Linux on the other hand is a whole new ballgame}. When i installed Vista it of corse came with a boot loader and i get the choice of "earlyer Version of Windows" (XP) and "Vista".
Now im wondering if i install linux on the Partition iv'e earmarked for it, Will it try to put its own boot loader program in or will it simply show in the vista bootloader? I dabbled in Linux redhat10 a few years ago and ended up creashing my MBR and having to start all over again (this time iv'e imaged my XP drive).

so simpley put: Will Ubuntu Install its on bootloader? ifso will it conflict with windows bootloader?

My technical knowlage is all based on wondows and im realy have no idea what im doing in linux. So please put any answers in PLAIN ENGLISH :lolflag:

Thanks in advance
M.C.

---

### Post by cartisdm on 2008-04-29
Are you going to do fresh installs of XP, Vista, and Ubuntu or do you already have the XP and Vista installed and you want to add Ubuntu?



**Edit:** Sorry I just re-read your post a little more closely.  I see you already have them installed.  Ubuntu is going to install it's own Grub loader which should allow you to choose your OS to boot into.  It's a matter of what options you choose when you install.

Sometimes things can get really tricky, even for someone who's done it before, so I'd recommend finding a step-by-step guide that applies exactly (or as close as possible) to your situation

---

### Post by lwvmobile on 2008-04-29
Yes, it will by default install Grub on the first disk designated by BIOS, but normally always will put in the Vista/Longhorn boot loader as a bootable option in Grub. It doesn't overwrite the Vista bootloader, just the portion in the MBR that points to it.

With multi hard drives, for best results, I find it better to overwrite the default in the MBR from Windows with the one from Grub. Just make sure grub is written to the hard drive BIOS is attempting to boot to. 

Another problem, though not necessary, you don't seem to have a 'swap' partition readily available.

Alternatively,

You can use the wubi installer. Just put the disk in in a windows session and install.

---

### Post by kansasnoob on 2008-04-29
I haven't done this, but I've used other tutorials provided here and they've always worked:

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by cartisdm on 2008-04-29
Also I can't stress enough BACK UP ANYTHING IMPORTANT.  No matter how idiot-proof a walkthrough can be, there will always be a point where you go "wait...which one do I choose?"  Trust me, if you have anything you can't live without on your harddrives you want to be 100% sure not 99.9% sure you are doing things ok.

I did a fresh install of Hardy last week on my dual boot with XP.  I thought I erased my windows partition but luckily I didn't especially since it was the day before my final exam project was do!!!

---

### Post by Mad_Commander on 2008-04-29
> **cartisdm said:**
> Also I can't stress enough BACK UP ANYTHING IMPORTANT.  No matter how idiot-proof a walkthrough can be, there will always be a point where you go "wait...which one do I choose?"  Trust me, if you have anything you can't live without on your harddrives you want to be 100% sure not 99.9% sure you are doing things ok.

I did a fresh install of Hardy last week on my dual boot with XP.  I thought I erased my windows partition but luckily I didn't especially since it was the day before my final exam project was do!!!

Thats the first thing i did before i imbarked on this project :) 
Thanks guys for your help. Since i have an image Of XP i think im just gonna go ahead and do it! :|
I will post the results for anyone else that wants to venture into the relm of tri-boot :P

G'Night

---

### Post by cartisdm on 2008-04-30
yea man, let us know how it goes and post the steps and any complications you run into

---

