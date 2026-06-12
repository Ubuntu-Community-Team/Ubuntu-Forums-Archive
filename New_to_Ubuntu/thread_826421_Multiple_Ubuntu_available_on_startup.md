---
title: "Multiple Ubuntu available on startup"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Just-trevor on 2008-06-11
When I boot up my computer it runs through everything, like normal, and gives me the list of OS's that I can use

For some reason, there are like, five ubuntus in that list, each with a recovery mode
Each one is different, like 8.05 & 8.06 and whatever.

I had two pairs a while ago, and they were both fiesty until I upgraded to gutsy, when they were both gutsy, but now with hardy there are like way too many.

I think they are using up hard drive space, because it shrank from like 50 gigs or something to 8 over time, and I have just sorta recently noticed.

I have booted off a different one other than the top one that it boots from if 15 seconds pass without me selecting another one, and they are the same, as far as I can tell

I also have a debian option but it doesn't do anything when i use it, i have to restart my comp again and select something else.

I'd take a screenshot, but i can't, which defeats the purpose of mentioning that in the first place...

Does anyone have a similar set-up?

Do the extra Ubunti take up space?

Is there a way to get rid of them, safely?

I would put all the stuff on my comp on my zune and just wipe it, but i need more disk space to download xp to get my zune to work on linux

yes I know Zune is microsoft, but its better than apple and i couldn't find anywhere to get a zen at a reasonable price

---

### Post by wannadumpwindows on 2008-06-11
Each one of those is just a different kernel. Next time you boot, take note of the version numbers. Then just use synaptic package manager to delete the old ones. 

It's also always a good idea to keep one extra around, just in case.

---

### Post by powerpleb on 2008-06-11
It's normal, there were some kernel upgrades recently and GRUB is giving you the option to boot into the old kernels if you need to.

---

### Post by Victormd on 2008-06-11
That's because of the kernel updates in Hardy. You can get rid of them by editing the /boot/grub/menu.lst and either deleting or commenting out (with #)...

---

### Post by lisati on 2008-06-11
> **powerpleb said:**
> it's Normal, There Were Some Kernel Upgrades Recently And Grub Is Giving You The Option To Boot Into The Old Kernels If You Need To.
+1

---

### Post by Raistlin82 on 2008-06-11
Another curiousity satisfied, thanks, been wondering about that myself :)  Gotta be said that so far my Ubuntu experience has been great, and the forum has been awesome!:guitar:

---

### Post by drs305 on 2008-06-11
Here is a pretty complete explanation of the kernel displays in grub and some of the options available to modify the menu via StartUp-Manager:

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Just-trevor on 2008-06-11
Cool
thanks drs305
awesome howto

This forum does rock:guitar:

... I'm not sure if I should just start a new thread or not, but related kinda,
this doesn't solve my hard drive space problem

 I installed a backup version of xp but i need to register it for it to work, but my dad's comp is running the original, so i can't use it.

how do I uninstall that with ubuntu?

I'm already gettin rid of thunderbird and evolution and whatnot

it is related

---

### Post by stalkier on 2008-06-11
> **wannadumpwindows said:**
> each One Of Those Is Just A Different Kernel. Next Time You Boot, Take Note Of The Version Numbers. Then Just Use Synaptic Package Manager To Delete The Old Ones. 

It's Also Always A Good Idea To Keep One Extra Around, Just In Case.

+1

---

### Post by Frenske on 2008-06-13
So what is the recovery mode for? Is that a different kernel with less options or the same kernel with various options switch off.

I have now 5 options. Latest kernel + latest kernel (recovery mode) + previous kernel + previous kernel (recovery mode) + Windows XP.

I guess the previous kernel (recovery mode) is a bit redundant.


By the way after I select the Windows XP (yeah I know boooo) I am getting another grub menu with the option to select Windows or Ubuntu. This is a result of option I was given when I tried the live CD but it failed to boot into ubuntu live CD. I want to get rid of it but how?

---

### Post by Joeb454 on 2008-06-13
It puts you into a command line as root, so you can try and recover the system :)

---

### Post by kaboodle_fish on 2008-06-13
> **Frenske said:**
> 
I guess the previous kernel (recovery mode) is a bit redundant.


Fubar something and you'll realise just how useful the recovery mode is

---

### Post by philinux on 2008-06-13
> **Frenske said:**
> So what is the recovery mode for? Is that a different kernel with less options or the same kernel with various options switch off.

I have now 5 options. Latest kernel + latest kernel (recovery mode) + previous kernel + previous kernel (recovery mode) + Windows XP.

I guess the previous kernel (recovery mode) is a bit redundant.


By the way after I select the Windows XP (yeah I know boooo) I am getting another grub menu with the option to select Windows or Ubuntu. This is a result of option I was given when I tried the live CD but it failed to boot into ubuntu live CD. I want to get rid of it but how?

Sounds like you installed ubuntu within xp via wubi as well. If you like you can , in windows, use add remove to uninstall it. See the wubi home page for info, just google wubi.

---

### Post by housam on 2008-06-13
> **Just-trevor said:**
> Cool
thanks drs305
awesome howto

This forum does rock:guitar:

... I'm not sure if I should just start a new thread or not, but related kinda,
this doesn't solve my hard drive space problem

 I installed a backup version of xp but i need to register it for it to work, but my dad's comp is running the original, so i can't use it.

how do I uninstall that with ubuntu?

I'm already gettin rid of thunderbird and evolution and whatnot

it is related

If you have this backup installation on a separate partition, just delete this partition using the partition editor on Ubuntu live CD.and add this space to Ubuntu partition. by the way do you have a dual boot ubuntu/windows ?

---

### Post by Just-trevor on 2008-07-01
yes i do have a dual boot of ubuntu/windows

sorry for not responding for two weeks, I checked a couple of times a couple of days after i replied last to see if anyone else had replied but there weren't any, so i stopped checking

---

