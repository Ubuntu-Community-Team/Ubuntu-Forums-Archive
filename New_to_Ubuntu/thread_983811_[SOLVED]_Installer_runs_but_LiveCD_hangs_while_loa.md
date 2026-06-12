---
title: "[SOLVED] Installer runs but LiveCD hangs while loading"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by cshard on 2008-11-16
How long on average does one have to wait when installing either Ubuntu 7.10 or 8.04 LTS? 

I'm currently using a Asus P5K Pro Motherboard with an Intel Quad Core Q6600 CPU, 4 x 1 GB 800mHz Ram, Asus GeForce 8500GT, and a LG Super MultiDrive DVD RW/RAM with LightScribe. The HDD is question is a Seagate 320GB Barracuda.

Yesterday and today, I attempted to install Ubuntu 8.04. Although it took a long time to get to the install screen, it eventually arrived there and I followed all the steps presented to me. However, shortly after starting the install, the program reported that the CD or the HDD was faulty and the installation could not proceed. It then loaded up the LiveCD and allowed me to use the barebones version of Ubuntu, as well as attempt the installation again. I attempted to install an additional 2 more times, both with the same result, and in frustration, I decided to start from the beginning again by shutting down and restarting the PC.

That was apparently a bad decision, because since then, I have not been able to load back Ubuntu 8.04 again. I checked the integrity of the CD twice, I loaded up win xp on the same PC and confirmed that the HDD was not faulty, was running fine, and could still be reformatted back to NTFS. I've attempted to start the LiveCD by turning on noapic and nolapic under F6 options, all with no success. In all attempts, the PC will hang at a bright pastel orange screen, or will load into Terminal/MS-DOS and remain stuck there for a long time. I've recorded times of about 1 hour or so, after which I reset my PC and attempted again.

Besides hanging at a orange screen, as the Linux modules are loaded, I've noticed quite a number received a SQUASHFS error and the system cannot load certain modules properly due to this. I can't take a screencap of this unfortunately, but I'll see if I can get a photograph of it.

As of now, I have burned a copy of 7.10 that I made quite a long time ago as well as burned a fresh copy of 8.04 LTS. I'm still getting similar problems, which makes me think that something else is still causing the problems. At last count, I started Ubuntu in Safe Graphics Mode, and made a bit of progress - now the computer hangs with the desktop image loaded. The mouse cursor indicates something is loading and the screen will black out if I leave it alone too long, but the CD drive and HDD indicator no longer flicker.

---

### Post by bumanie on 2008-11-16
Best thing to try would be to install via the alternate cd which is a text-based installation. It usually works if the live cd won't. Would use 8.04 or 8.10 - 7.10 has less than 6 months until there is no longer any official support.

---

### Post by cshard on 2008-11-16
Noted, I've started downloading the alternate as well as another copy of the original iso. I've seen quite a few threads mention the alternate iso, but no mention specifically about what was the difference between the two. I'll test it out and see if there's any difference.

Any idea why the graphical installer can't function? I doubt it's a RAM issue and the only thing that comes to mind is a mobo incompatibility. I'm still a Linux newbie and it'll be handy to have a better understanding of why something isn't working.

Forgot to mention that although the HDD I am using is a blank, it's not a factory fresh one as it was formatted into an NTFS drive. When I first started, it was holding some files from a previous RAID 1 configuration. Could that be an issue when using the LiveCD?

---

### Post by bennachie on 2008-11-16
A lot of people seem to have had trouble with the 8500GT graphics card. You might want to Google "ubuntu geforce 8500GT" to get the picture. 

There is a (small) chance that an 8.10 LiveCD might do a better job. Another possible solution might be to remove the graphics card, install Ubuntu relying on your onboard graphics chipset, locate and install the proprietary driver (which will not be included in your LiveCD - a "generic" driver is included and is normally sufficient to get the show on the road) then replace the graphics card (shutting down at the appropriate stages, then rebooting, of course).

I've never tried this manoeuvre (my own Ubuntu system is six years old, with much more modest specifications, and I had no trouble installing either 8.04 or 8.10), so please accept my apologies in advance if you have no luck!

---

### Post by cshard on 2008-11-16
Hmm, no can do. My motherboard doesn't have an onboard GPU from what I remember, so the 8500GT is all it has. Oh well. I'll go read up a bit more about compatibility issues anyway. Guess it'll become clearer after I check the text based installer out later.

Thanks for taking the time to reply. ^_^

---

### Post by cshard on 2008-11-16
Well, looks like the alternate install CD works... now to figure out why my network connection is intermittent and extremely slow. Meh, one issue after another.

---

