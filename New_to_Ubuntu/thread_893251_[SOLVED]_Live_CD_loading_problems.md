---
title: "[SOLVED] Live CD loading problems"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by pspahn on 2008-08-18
Ordered myself a new system the other night, and plan on using my old system at work. I would like to load Linux on it (at this point, it doesn't matter which flavor), and have had no luck with any of them.

Each different liveCD I've tried fails. The only one I got to actually load up is PartedMagic, though it hard freezes after ~2-3 minutes of uptime.

I've run memtest and have tried several different sticks of RAM. 

P4 3.4
256-1G RAM 
ATI X850 AGP
Gigabyte GA-8VT-800 [http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=1725&ProductName=GA-8VT800]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=1725&ProductName=GA-8VT800")
Several different HDDs
Coolmax CP-500T PSU

I've burned the images at 4x and have checked their integrity.

This is all quite surprising to me, as I was expecting a painless install after installing xubuntu on an old P4 1.4 with 128MB.

---

### Post by Ryadt on 2008-08-18
Try installing with the alternate cd. Download it from the ubuntu homepage. Make sure you check the box where it gives you the option for the alternate version.

---

### Post by nicedude on 2008-08-18
You should try 2 things, first would be to get the Alternate install disk version, it will say alternate in the name. This could work without any further trouble as the alternate disk is not a live disk ( ie it is only for installing and will be a guided text type menu for firing up the install, it is still very easy to use though ). So I would try this first.

Second possibility in my mind is that you may need to add some extra command parameters to the boot command when you are first installing. Foremost in my mind would be noacpi which disables some power management features iin case they cause the disk to not boot up. You will most likely have to do this only to get it installed not once it is installed ( at least that is how it is for my laptop )


You can google search for linux boot parameters to see what I mean

---

### Post by pspahn on 2008-08-18
I was downloading the alt CD as I posted the first time. It seemed to be working, however everything locks up at some point, it's somewhat random, but is always while copying files. 

I went back and tried the liveCD version, setting noacpi (and eventually all the 'other' options), which got me further into the install process, but it still fails at some point, with a hard lock up, no cursor movement, no CTRL-ALT-DEL. 

I've tried running the install from a different optical drive, though it still fails.

I'm now wondering if my image burns, which I wrote to DVDs, has something to do with it. I'm going to burn another image to a CD, and give it another shot...

...losing hope...

At some point, I will try to find some way to update my bios. I'm using version F3, and F6beta is the most recent. The problem is that the bios update requires a floppy drive, which I don't have and am not too keen on putting one in an old Frankenstein computer just to update the silly bios.

---

### Post by Ryadt on 2008-08-18
Follow this guide...[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by pspahn on 2008-08-18
Well I found that Gigabyte has a new bios update utility, which I ran and am now running F5 version.

I made two new images, one live CD and one Alt. Same story. I actually got quite far into the install process with the liveCD, but it hung up while copying files. 

To add insult, my windows install now seems unstable, I've had a few hard locks as well as random reboots. 

I'd imagine someone might think my PSU is suspect, but it's been a solid unit since I bought it about a year ago. It's 500W, so it should be more than adequate for the few devices I'm running (I removed my WinTV card even).

Gonna keep chuggin along... maybe it'll sort out?

---

### Post by pspahn on 2008-08-18
...a thought...

Over the course of switching optical drives, hard drives, etc. I think I may have had my video card plugged into the same power cable as two hard drives and a dvd writer for some time. This could explain the instability...

...going to try another install now.

---

### Post by pspahn on 2008-08-19
SOLVED--

That was the problem. With multiple drives hooked up to the same power rail as my x850, once installation began and all went active, the power to the x850 got dirty.

What I find interesting, is that I tried an older, much less power hungry video card, and the symptoms were the same.

---

