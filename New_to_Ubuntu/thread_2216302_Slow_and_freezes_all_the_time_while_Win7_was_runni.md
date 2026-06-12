---
title: "Slow and freezes all the time while Win7 was running okay"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by melarish on 2014-04-11
Hi! I've just installed Ubuntu 13.10 32bit (from CD). Clean install, deleted the 3-year-old Win7 it previously had. It was getting a bit sluggish but even then, ran mostly fine and had no problem with 20 open tabs + music playing + a download or file transfer. So I decided to try Ubuntu, which is supposed to be faster than Windows.

Except, it's worse than anything I ever had.

The moment I start opening a few things at a time, it goes to hell - gets really slow and eventually freezes completely. I don't even know what specifically causes this, because I give up on waiting and press the OFF-button (trying to open system monitor would be futile - I would wait forever). I think it's especially bad with Facebook open (it was absolutely unusable before I installed Adblock).I searched around a bit and found a few suggestions. However, there are no driver updates available in Software and Updates and I also don't want to downgrade to a lighter version when my laptop should be perfectly fine with a regular OS.

My laptop has 2GB of RAM (usable 1.8). Graphics driver says Gallium 0.4 on ATI RS690.System Monitor shows 380MB usage for Opera with one tab and one download (Firefox used around 250 with just one tab open), 58 for compiz - it's not much but anything I add to it, becomes ridiculously slow. On Windows, it would often have close to 1GB used and still be okay with opening new things.

Any more suggestions before I give up and reinstall Windows?

---

### Post by toms3d on 2014-04-14
my linux   I am running 64bin installed from amd 64-bit iso.    I have had the same problem.   I use fvwm as window manager. should make no diff.   firefox about says 28.0 rev.   I  have found if it crashes and I restore, often it keeps crashing.   The problem is so bad and it seems no one is looking at it.   So I am using google-chrome to browse.

I use multiple personalities of chrome of firefox  for different tasks.   Currently running 4 or 5 independent chrome for the last few days and no problems.   I prefer firefox but untill it's fixed I am using chrome.
 
The way I look at who is doing what is this ps command.   It's ps used twice on one command line.  First time is just for the data field labels.   You can see top twenty CPU processes.

ps aux |head -1;ps aux | sort -r -n -k 3 | head -20

---

### Post by aeyeaws on 2014-04-14
try running memtest and prime 95 stress test to make sure you dont have hardware problem, then try fedora debian knoppix live cd before you decide ubuntu cant run your box ok beavis

---

### Post by melarish on 2014-04-16
Alright, after switching back to Firefox, it seems to run alright (I think Opera's Adblock didn't work properly and Facebook totally killed everything). It still freezes occasionally when I have browser+PyCharm+Rhythmbox open and try to do something else but it seems adding more tabs and addons to Firefox doesn't make much of a difference. I'll try the stress test sometime and see what it says.

---

### Post by war28 on 2014-04-16
Hi melarish!

That graphics card is not a very good one I have a similar one myself, also with a 2Gb ram and a 1.8Ghz amd processor. Have you ever considered trying Xubuntu? Or another Desktop Environment?

---

### Post by jbaerboc on 2014-04-16
Ubuntu does use Compiz for fancy effects out of the box and depending on graphics card / card drivers combination you have going it can seriously mess with you. Even though my Nvidia 9600 GT handles it ok with the lates proprietary drivers I turn those effect off which does make the system more snappy. Also if a specific browser is giving you problems you can always try a different one and see if there's a difference. For instance in some Linux distributions I find Google Chrome to work best where as in this 14.04 LTS Beta I'm running firefox better than chrome.

---

