---
title: "Installing any ubuntu on a very old PC? Having problems???"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Pascal11110 on 2008-11-29
I have a very old computer that someone gave me with a 6.4 gig hard drive, I upgraded the ram to 512 mb PC100 sdram (two sticks of 256) a P3 processer that's around 700 or 800 Ghz, and a junk video card (can't remember which). I tried installing regular ubuntu but it said I had an error with many words flashing very fast, and it does the same thing if I tried using it without making changes to the hard drive. I then tried using xubuntu and if I installed it or tried without changing my hard drive, it got the xubuntu screen where it shows the desktop and the icons that come on it, but it wouldn't come up with any menu bars. Then I tried installing it again, and now every time I boot the computer up, right after the hewett-Packard screen it just says press r to reboot before it even has a chance to boot from a disk. Will taking out the Cmos battery and putting it back in solve this Press R problem, or is that hard drive, and do you have an idea on how I can get an Ubuntu to work? (this computer had working windows 2000 before I started screwing with it so I know it works fine. If you need anymore info just respond and I'll keep an eye on this and reply to you in less than 15 minutes.

Thanks a lot.

---

### Post by jimmy the saint on 2008-11-29
I doubt it is a bios issue, but you could try removing the battery.  I would try a memory check.  If you can get the cd to boot, don't go to the full OS on the live cd.  Just select memory test and see what it kicks out.  Often, old memory is bad so upgrading causes issues.  You could also try to remove the new stick and see if it works, but a memory test would be more informative.

---

### Post by rhcm123 on 2008-11-29
> **Pascal11110 said:**
> I have a very old computer that someone gave me with a 6.4 gig hard drive, I upgraded the ram to 512 mb PC100 sdram (two sticks of 256) a P3 processer that's around 700 or 800 Ghz, and a junk video card (can't remember which). I tried installing regular ubuntu but it said I had an error with many words flashing very fast, and it does the same thing if I tried using it without making changes to the hard drive. I then tried using xubuntu and if I installed it or tried without changing my hard drive, it got the xubuntu screen where it shows the desktop and the icons that come on it, but it wouldn't come up with any menu bars. Then I tried installing it again, and now every time I boot the computer up, right after the hewett-Packard screen it just says press r to reboot before it even has a chance to boot from a disk. Will taking out the Cmos battery and putting it back in solve this Press R problem, or is that hard drive, and do you have an idea on how I can get an Ubuntu to work? (this computer had working windows 2000 before I started screwing with it so I know it works fine. If you need anymore info just respond and I'll keep an eye on this and reply to you in less than 15 minutes.

Thanks a lot.

Try reformatting your hdd and repartitioning it manually (read: delete all the old partitions and make new ones). Also, for faster installs, don't use the live cd, use the alternate install cd. I never use the live cd cause the alt cd boots so much faster.

---

### Post by cmay on 2008-11-29
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

i would suggest if possible to use this cd or any other light linux live distro to see if you can have it running. i guess from out of this that the video card is not so good. maybe debian or puppy linux would be more suitable. i fix those old computers also and it should be able to run ubuntu flat out with out no problems. even that its old. 
but one thing i believe to be true is that if a distro like debian cant run on there can be hardware issues. maybe try do a debian lenny or debian etch.  try knoppix puppy linux or damn small linux on live cd to see if it can run that with a reasonable speed. 

and anohter thing is that maybe the ram blocks should be paired and have the same specs as the old ones. as try to see if the mother board can actually use the ram you put in it. i had one stable one that had  one 255 mb ram and ran ubuntu still very fast. then i upgraded to two 225 mb blocks and the system got really really unstable but i found out that the mother board in it self could not use more than the 300 of ram. 

good luck and i hope it works out for you.

---

### Post by baruch60610 on 2008-11-30
My guess would be the memory.  I don't know what memory you had before, but I was easily able to install Xubuntu on an old laptop with 128 Meg of memory.  It runs very slowly - but it runs.  That's more than it was doing before.

You might try going back to the original memory configuration.  Another possibility could be that this memory upgrade confused the computer.  Did you tell the BIOS that it now has 512 Meg?  If I recall correctly, some of the older computers needed to be told about upgrades like that.

I know that on my old laptop, when I tried to upgrade to 256 Meg, it just choked and died on me, wouldn't install or do anything.  That's why I suspect that your problem is the memory.

Hope this helps...

---

### Post by cmay on 2008-11-30
any progress ?

---

### Post by Pascal11110 on 2008-11-30
Sorry, I fell asleep. Anyway, it had two sticks of 64 mb before I upgraded it, and I checked the system specs online and it said that it could handle up to 512 mb of pc100 sdram (it's a HP Brio) and since I have a box of thousands of sticks of ram I found those sticks, but I have more so I'll try changing out the ram, but I tried installing ubuntu before the memory change, sorry forgot to note that. I'll also get the alternate install and see if that works. Thanks a lot for all your help.

---

### Post by rhcm123 on 2008-11-30
> **Pascal11110 said:**
> Sorry, I fell asleep. Anyway, it had two sticks of 64 mb before I upgraded it, and I checked the system specs online and it said that it could handle up to 512 mb of pc100 sdram (it's a HP Brio) and since I have a box of thousands of sticks of ram I found those sticks, but I have more so I'll try changing out the ram, but I tried installing ubuntu before the memory change, sorry forgot to note that. I'll also get the alternate install and see if that works. Thanks a lot for all your help.

Judging by the age of your computer, it sounds like it isn't able to handle the power demands of the liveCD. I have several old computers (a 90 megahertz, 75 mb ram box) that didn't support the live cd, so i got the alt cd and it worked fine. (For xubuntu). However, i later deleted xubuntu and put on ubuntu server 8.10. GO COMMAND LINE!!!:guitar:

---

### Post by Pascal11110 on 2009-12-31
Wow, I hate to bump this old thread but I just wanted tot tell you guys the alternate worked fine so the brio just couldn't handle the live cd. Thanks for all the help.

---

