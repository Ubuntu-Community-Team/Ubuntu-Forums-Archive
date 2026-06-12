---
title: "installation failure"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by WyzeGye25468 on 2012-04-17
I have a cheap little E-machine notebook.
It originally had Vista on it. The kid who owned it bungled it up pretty bad, and I ended up buying it for 50 bucks thinking it would be an easy fix.

I've tried installing Ubuntu, Mint, Windows 7, OpenSUSE, You name it, i've tried.

I had ubuntu running on it fine when i first tried, then i turned it on the next day, and Nothing.

since then i've had no luck. I've swapped out the ram, I've swapped out the hard drive. I've installed the above mentioned, bar windows, on a hard drive in my other notebook, and just moved over the hard drive to the problem notebook.


Is the CPU fried? Or am i overlooking something majorly?

---

### Post by fleamour on 2012-04-17
> **WyzeGye25468 said:**
> I've installed the above mentioned, bar windows, on a hard drive in my other notebook, and just moved over the hard drive to the problem notebook.


Is the CPU fried? Or am i overlooking something majorly?

Different hardware requires different drivers for different chipsets, that are determined on install.

You cannot install OS on other hardware then swap hard drive over & expect it to work.

---

### Post by mörgæs on 2012-04-17
Hi, welcome to the fora.

Memory problems is more likely. Have you tried running memtest from a live boot?

---

### Post by WyzeGye25468 on 2012-04-17
Sure you can, ive done it countless times, but thats not the point.

Installation fails every time. Just locks up no matter what i do.

---

### Post by mörgæs on 2012-04-17
> **fleamour said:**
> Different hardware requires different drivers for different chipsets, that are determined on install.

You cannot install OS on other hardware then swap hard drive over & expect it to work.

Yes you can. In Linux it actually works most of the time, since the drivers are in the kernel (assuming closed-source drivers have not been added).

---

### Post by WyzeGye25468 on 2012-04-17
> **mörgæs said:**
> Hi, welcome to the fora.

Memory problems is more likely. Have you tried running memtest from a live boot?

No, but ive done the less scientific method of replacing the ram.

---

### Post by WyzeGye25468 on 2012-04-18
So i tested the memory. 100% there.

Any other ideas?

---

### Post by HiImTye on 2012-04-18
when you turn it on do you see the BIOS POST or the logo display or is it just a blank screen?
if you get a POST or logo display, does it begin the bootup sequence?

---

### Post by houseworkshy on 2012-04-18
What it boots from is important, most will boot form a cd/dvd drive if the bios is set to look there first for a boot loader.  Some will boot from a flashdrive but many just won't.  If you try a live cd and it works then you should be ok, if not look at the bios.  How to get to the bios varies from machine to machine and will be along the lines of "hold down....( whatever key/s it is ) during the bootup.  You could find out by searching for the pc name +bios.  When in bios simply set it to look at the cd first, the convention is that what is looked at first will be top of the list.  If that doesn't work it may be woth looking at APCI which is also in bios, whether it is enabled or not can matter to some machines and operating systems.  Always make a note of what you do as bios is one area a machine can be really messed up.
Bios is also password lockable so if you can't get in you will need to chat to the person you got it from.  There are ways round that but not postworthy on this forum.

If the problem is memory then try a small distro to find out if the hardware functions, I'd recomend puppy as the live cd that works on almost everything.  If it's graphic card drivers one doesn't actually HAVE to install them to have a working machine as there are lower spec common to all drivers ( vga usually ) which will run on any old thing, these are included in most distros and work on most machines.  ( in windows, for example, "safe mode" will invoke them.).  

Once you get something running in live mode it is worth using the package manager as if you were going to install but back out instead.  This will auto detect then find out if drivers for the machine exist in the package repositories of which ever OP you are trying out before you commit to a hard drive install, saves time.  If they don't show don't give up on them yet.  Repositories can be added.  You can install tiny things to ram in a live cd session so I recomend popping "sysinfo" in.  This will dig around for the machines specs and give you the hardware info you need to search out driver packages, comaptability issues  etc or ask for detailed help.

Just re-read your first post and was going to edit the above thinking " oh he had it running once" then I remembered that Vista was the last windows I used before switching to linux and that it did in fact do things to bios.  So I'll leave the above as it is but add that even though you have had something running take a peek anyway.

There is another thing you could do for a clean start.  You could run a thing called Dban, it wipes all the drives it can find, takes a while but will almost return the machine to empty as new,  especially it will remove rootkits ( a nasty form of virus which can shell your system into itself)  too which formating often doesn't. Reconditioning shops use it to protect previous owners data.  If anything crucial is in there back it up as it would take a police/security level operation with equipment costing thousands to recover it afterwards.   Dban is a free download.

Another thought is to use write once only media for your installation disks, problems have been reported with re-writeables.  Also burn the iso's as slow as your software allows.  Good luck.

---

### Post by dzponce11 on 2012-04-18
> **houseworkshy said:**
> What it boots from is important, most will boot form a cd/dvd drive if the bios is set to look there first for a boot loader.  Some will boot from a flashdrive but many just won't.  If you try a live cd and it works then you should be ok, if not look at the bios.  How to get to the bios varies from machine to machine and will be along the lines of "hold down....( whatever key/s it is ) during the bootup.  You could find out by searching for the pc name +bios.  When in bios simply set it to look at the cd first, the convention is that what is looked at first will be top of the list.  If that doesn't work it may be woth looking at APCI which is also in bios, whether it is enabled or not can matter to some machines and operating systems.  Always make a note of what you do as bios is one area a machine can be really messed up.
Bios is also password lockable so if you can't get in you will need to chat to the person you got it from.  There are ways round that but not postworthy on this forum.

If the problem is memory then try a small distro to find out if the hardware functions, I'd recomend puppy as the live cd that works on almost everything.  If it's graphic card drivers one doesn't actually HAVE to install them to have a working machine as there are lower spec common to all drivers ( vga usually ) which will run on any old thing, these are included in most distros and work on most machines.  ( in windows, for example, "safe mode" will invoke them.).  

Once you get something running in live mode it is worth using the package manager as if you were going to install but back out instead.  This will auto detect then find out if drivers for the machine exist in the package repositories of which ever OP you are trying out before you commit to a hard drive install, saves time.  If they don't show don't give up on them yet.  Repositories can be added.  You can install tiny things to ram in a live cd session so I recomend popping "sysinfo" in.  This will dig around for the machines specs and give you the hardware info you need to search out driver packages, comaptability issues  etc or ask for detailed help.

Just re-read your first post and was going to edit the above thinking " oh he had it running once" then I remembered that Vista was the last windows I used before switching to linux and that it did in fact do things to bios.  So I'll leave the above as it is but add that even though you have had something running take a peek anyway.

There is another thing you could do for a clean start.  You could run a thing called Dban, it wipes all the drives it can find, takes a while but will almost return the machine to empty as new,  especially it will remove rootkits ( a nasty form of virus which can shell your system into itself)  too which formating often doesn't. Reconditioning shops use it to protect previous owners data.  If anything crucial is in there back it up as it would take a police/security level operation with equipment costing thousands to recover it afterwards.   Dban is a free download.

Another thought is to use write once only media for your installation disks, problems have been reported with re-writeables.  Also burn the iso's as slow as your software allows.  Good luck.

Noting on what this user said, here are some good small distros (some of them are live ONLY)
-TinyCore ([http://distro.ibiblio.org/tinycorelinux/welcome.html](http://distro.ibiblio.org/tinycorelinux/welcome.html))
-SliTaz ([http://www.slitaz.org/en/](http://www.slitaz.org/en/))
-DSL ([http://www.damnsmalllinux.org](http://www.damnsmalllinux.org))
-CrunchBang ([http://www.crunchbanglinux.org](http://www.crunchbanglinux.org))
-Lubuntu ([http://www.lubuntu.net](http://www.lubuntu.net))
-UnityLinux ([http://www.unity-linux.org](http://www.unity-linux.org))

---

### Post by WyzeGye25468 on 2012-04-18
Yeah, ive tried puppy, and dsl both the same effect, it will boot, but after about 45-90 seconds it becomes unusable, ive tried booting from a dvd-r, cd-r, flash drive and hard drive.


I thought about using dban, but with the above symptom, i dont believe the hdd to be the culprit.

And for the guy who wrote out the long reply, lol i apologize, i could have saved you some time if i mentioned that im more of an advanced linux user, and i take everything you said to be common sense. 

I just posted this here in hopes that somebody else had the same problem. 

To recap.

-Memtest returned no errors.
-Live distros as small as dsl slow to a crawl within a minute of booting up, from various media.
-Ubuntu was running great for 1 night then exploded the next day leaving me with this condition (i did have some trouble setting it up initially though)
-Cpu fan does its thing.
-Ive returned bios to default settings multiple times.
-Tried 3 different hdds.


This laptop doesnt understand that i dont need it, and i enjoy smashing electronics that dont listen to me.
Ive tried threatening it, but that hasnt gotten me anywhere.

---

### Post by houseworkshy on 2012-04-19
From that it sounds like a hardware thingy but probably not fatal.  Starting ok then failing after running a bit, especially on various operating systems, is typical heat due to insulating dirt.  One could test this by bunging in lm-sensors during the short window of time before failure and taking several peeks at "sensors" before it goes down.  Maybe you could extend the time window with all sorts of barns wallace type cooling methods but I wouldn't bother.  
Open her up and get busy with the can of compressed air.  Less expensive but apparantly risky methods, so I'm told but have been lucky with, is to get the machine round to a garage and borrow the compressed air hose.  Another, also apparantly risky, is to make a funnel of news paper to concentrate the suction from a vacume cleaner attachment don't physically touch any parts and be earthed just in case.   Use the later methods at your own risk, just because I've got away with it doesn't mean anyone else will, probably better with the can anyway.  Also take off the heat sink and give it a good clean, the slits in the aluminium block often get more clogged than air can blow away especially if the machine has been around smokers or near cooking.
Didn't mean to sound patronising, it was the post count that made me think that you may be a novice.    I sometimes get irked when I see some poor newbie getting high end understandable-only-by-experts replies, seems like I swung too far in the other direction.  Probably done the same with the cleaning the machine advice ah well.....risky or not the air hose thing feels great, perhaps it's because it's so dramatic after all the frustrating careful careful fiddling, amazing how much muck gets blasted out,  swearing at the electronics simultainiously is optional but has got to be theraputically sound.   The post count is a slightly better guide about one thing, barring previous identities,  so ... Welcome to the forums.

---

