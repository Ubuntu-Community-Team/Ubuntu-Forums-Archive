---
title: "Upgraded to intrepid, laptop suddenly crippled. Help?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by victorcrane on 2008-11-07
Hey folks, a couple of weeks back I took the opportunity to upgrade to intrepid and did a full clean install on my laptop. Everything went in ok and as far as I could see for the first week everything was pretty smooth, now however I'm noticing some problems. 

About five days ago I noticed the cpu fan getting pretty excited which is unusual so I checked the system monitor and found that the cpu was running between 40 - 50% all the time, even when there were no programs running and everything was idle. I have no idea why this is. 

The next problem is firefox, which when running even static on the google homepage (no animation / flash etc.) causes the cpu to run at 65 - 70%. Using the Facebook chat applet positively cripples it, every message causing a peak to 100% usage and the fan to fire up like a crazy thing.

The laptop is a dell inspiron 1300, 1.6ghz celeron M processor with 1.2gb ram. I know it's hardly top of the range but surely surfing the web should cause absolutely no problems at all. 

I also have a serious crash problem with rhythmbox, as in it just dies whenever it feels like it at random. Is anyone having similar problems? Any advice? This is getting worse by the day and it's making web browsing a real pain in the backside. 

Vic. :guitar:

---

### Post by jago25_98 on 2008-11-07
I don't have ibex... yet. But I'll throw a few points to start as help (not much time here).

Try running `top`, or gnome-system-monitor to see what's eating the CPU. Is it that beagle search thing?

Try disabling graphics, like using no mesa, changing driver in /etc/xorg.conf (backup 1st)

Firefox. Good question. I've seen this before on other releases. Drove me mad, can't say I figured it out completely. But for me, yeah flash was involved so I use flashblock. Also possibily some extention problems too. I can't remember if removing user info in ~/.mozilla/firefox/userWhatever helped to start again as a test

That's all I got for now

---

### Post by philinux on 2008-11-07
Yep. top to see whats going on.
System>prefs>appearance> visual effects choose none for now.

---

### Post by keplerspeed on 2008-11-07
Also system>administration>system monitor for a gui, similar to task manager in win.

Are you using 32 or 64 bit? I have found the 64 bit firefox a little laggy at times.

---

### Post by jaytek13 on 2008-11-07
Did you actually perform an "upgrade" over a clean installation? I know my "upgrade" has caused nothing but problems for the machine I did it on, while a clean install works flawlessly for a different machine.

---

### Post by jpoRS on 2008-11-07
I had the same CPU problem (running +40% even when nothing is running) when I upgraded.  The problem persisted until I fixed several other problems I had with my upgrade ([LINK]("http://ubuntuforums.org/showthread.php?t=968792"), [LINK]("http://ubuntuforums.org/showthread.php?t=968856")).  Once I reconciled these problems my processor dropped back to its normal levels.

Are you having other symptoms which could be the cause of the problem?

Good luck,
jim

---

### Post by LowSky on 2008-11-07
I did the upgrade instead of a fresh install, and I have no issues what so ever. I just want to say that so it doesn't scare any one from upgrading.

I bet your laptop is getting lock up on indexing. My suggestion is you turn it off from starting up when you boot the computer. It should solve your issue of the processor running nonstop.

As for Firefox, Google Firefox hacks, that should help with the memory loads. Also try backing up your bookmarks and deleteing the /home/.firefox folder

---

### Post by victorcrane on 2008-11-07
Hi folks. Ok when I installed I downloaded the iso and formatted for a full fresh install as I was already having some issues with hardy which I couldn't quite figure. Mainly these were affecting media. Rhythmbox would continually crash and whilst browsing some media players for streaming video would be perfectly fine (youtube, google video) and others would just stutter along or become scrambled and in the case of any streaming content on the cnn website it simply came up with 'general error' in the window...

Anyway, I have long been a fan of flashblock so will add that on now, I left it off this installation to see if perhaps it was in any way responsible for the problems I was having with streaming media. I have disabled visual effects and this does seem to have helped a little. The processor is running a little lower and certainly browsing is improved. I notice in the processes field within the system monitor the biggest drain on the cpu is the monitor itself, and aside from that only firefox is pulling any power. I'll follow your advice guys and see how much I can streamline this thing. 

I will say that despite the problems I find the OS very very nice to use and it looks great. Installation was much easier than hardy as it recognised my display and was all set up with the correct resolution unlike hardy which I had to configure manually, quite a feat for a novice like me. The wireless driver was a doddle to find and install too, again with hardy it took me a long time and a lot of digging and advice from you guys to achieve this.

A man can't realistically complain to much about a totally free system like this. 

Many thanks for your help!

---

### Post by Fran89 on 2008-11-08
SAME THING EXACTLY, altho mine runs a bit faster, but this is extremly unusual...

---

