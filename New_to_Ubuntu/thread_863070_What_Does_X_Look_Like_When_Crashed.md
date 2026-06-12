---
title: "What Does X Look Like When Crashed?"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Webby437 on 2008-07-18
Yea, I know it sounds dumb. Does the screen fill with a couple colors with lines up and down or does it go blank? Does Ubuntu lock up like windows? Do you get a BSOD with what looks like random numbers and letters? If the system locks up, is pushing the reset button the only way to reboot? If X crashes shouldn't Ctrl+Alt+Bksp restart it or is that only sometimes it works.

Im sorry to ask so many questions in one thread but I figured it was easier than making threads for all of them.

Thx

---

### Post by jordanmthomas on 2008-07-18
Depends, usually when X crashes for me it'll just stop responding altogether, so ctrl-alt-backspace doesn't work.

In the past, I have got a couple of colored lines as it crashed and it becomes unresponsive.

Hard resets aren't the **only** way to get out of it usually.  For example, I usually have ssh running and if X locks up, I can kill it from another computer and all is well.

Honestly, though, X rarely crashes for me.  Does it crash often for you?  If so, then there's a problem.

---

### Post by schauerlich on 2008-07-18
X crashes can be caused by a number of different things and therefore look like a number of different things. Just Ctrl+Alt+Backspace and you'll be fine. Most of the time that will fix your problem. However, if something that's more deep down in the system that locks up, a hard reboot may be in order. It should only be used as a last resort, as it can lead to all sorts of problems with your filesystem.

---

### Post by hansdown on 2008-07-18
> **EDavidBurg said:**
> X crashes can be caused by a number of different things and therefore look like a number of different things. Just Ctrl+Alt+Backspace and you'll be fine. Most of the time that will fix your problem. However, if something that's more deep down in the system that locks up, a hard reboot may be in order. It should only be used as a last resort, as it can lead to all sorts of problems with your filesystem.

Hi EDavidBurg. Joordanmthomas just posted that ctrl+alt+backspace did't work.

---

### Post by Webby437 on 2008-07-18
Well with all that said, I think I'm in trouble. I just crashed or locked up or something. Ctrl+Alt+Bksp didn't work and I had to press reset on the tower. I have everything backed up to a external drive so Im not worried about the data atm. Im just wondering why its doing this. If I reinstalled Ubuntu, would it format the disk like windows does or does it just write to that first section where its files are. I'm new to the swaps and dev1's and all that and I know its a different format than ntfs. The drive thats in the system now is brand new 160 gig fresh from the box. So Im thinking i might have downloaded something I shouldn't have. = \

---

### Post by schauerlich on 2008-07-18
You could try the "skinny elephants" trick. Basically this will reboot your system in the nicest way possible once everything locks up and Ctrl+Alt+Backspace won't respond. Here's a guide: [http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

---

### Post by schauerlich on 2008-07-18
> **Webby437 said:**
> Well with all that said, I think I'm in trouble. I just crashed or locked up or something. Ctrl+Alt+Bksp didn't work and I had to press reset on the tower. I have everything backed up to a external drive so Im not worried about the data atm. Im just wondering why its doing this. If I reinstalled Ubuntu, would it format the disk like windows does or does it just write to that first section where its files are. I'm new to the swaps and dev1's and all that and I know its a different format than ntfs. The drive thats in the system now is brand new 160 gig fresh from the box. So Im thinking i might have downloaded something I shouldn't have. = \

More than likely it was just a hiccup in the system. And yes, when you reinstall Ubuntu, it will format the the disk and erase your data, unless you have a separate /home partition.

---

### Post by Webby437 on 2008-07-18
I didn't get too crazy with the install from the cd. Just hit next a couple times, came back in and it was done. So Im guess no different /home location. Like I said no big deal with the data I have it saved. Just makes me mad to go from a windows machine that Hasn't crashed in a couple months to Ubuntu and crash 5+ times in two days. I'm looking at the guide now. Thank you.

---

### Post by Webby437 on 2008-07-19
Im stumped people! Read some more posts about codecs and SPM. Uninstalled somethings and still Ive crashed. So I started over. Wiped the WD 160 gig drive clean. Fresh install of Ubuntu 8 via live cd. Used entire hard drive for the install. Everything worked fine on install, loaded up to U:P, logged in. Opened Firefox, downloaded the flash player(First choice that came up of the 3). Watched a Youtube video and opened the updates console to download the 240+ updates. It starts downloading and Bamn, Funky colors and lines up and down on the screen. Nothing else had been installed yet. Ram test's fine, Board is working and not overheating. Poked around google and found that some of the WD Caviar SE drives have been bad, wouldn't install the os or setup as storage drives. Mine loaded up fine and took the os the first time. I did not have a single crash when I was using a 10 gig drive in the same box, same hardware, same cd version of Ubuntu. The 160 gig drive test's fine using the WD software and SMART HD tester I have on a pc test cd. My question is "Where do I go from here?". Could this be a bug with Ubuntu?(surely not cause others have 160's) Is the drive causing the problems and its just early warning signs that I need a new drive? (I bought the drive 3 weeks ago, Retail box) Is there a program that I can install to make a log file of everything that is going on in the system and can maybe log the crash or show me the faulty program or hardware? I guess I will put the 10 gig back in and load up till something better comes along.  I'm sorry this was so long and drawn out, but there are far more people on this forum that know more about linux and computer hardware than I do.

Any suggestions would be helpful, 

Web

---

