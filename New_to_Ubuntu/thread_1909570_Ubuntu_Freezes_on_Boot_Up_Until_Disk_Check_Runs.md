---
title: "Ubuntu Freezes on Boot Up Until Disk Check Runs"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by cyanidearsenic on 2012-01-15
Hello,
I have technically had Ubuntu installed (dual boot with Windows XP) for a while but had stopped using it until recently. Then I saw 11.10 and thought it looked cool so I booted up to update and play around.
All updates went fine (and there were at least 4) and the computer worked fine for about three days (not sure if that is the exact number).
Then I started having problems.
It's basically as the title says, when I try to boot the computer up it freezes, generally at the login screen or as the desktop is loading, and must be restarted. It does this repeatedly until (and this is a tentative guess) the disk check runs. A tentative guess because I've had the problem only about two days but it's done it both times.
After disk check it boots up fine. It's a little slow loading at the beginning and picking up my internet but it comes on and works fine for the whole day.

I'm not sure what info you guys would need (I'm posting in the absolute beginners forum for a reason!) so if you want to know something just ask (and possibly tell me how to obtain the info). 

Oh, and when I say repeatedly about it restarting, I mean repeatedly. I made a chart in LibreOffice. Yesterday, it took 17 restarts then disk check ran and it came on. Today it took 25. I intend to keep marking these on my chart (I like charts) either until the problem is solved, or until the 20th (eight days seemed like a decent sample size).

I actually had two other weird but not as bad as that things but they don't exactly belong in this specific thread. Should I mention them here or make new threads for them?

I appreciate the help. I need my computer for school and taking nearly an hour to turn it on is far from pleasant but I really like ubuntu and was actually considering getting rid of my Windows in favour of it.

Thank you for your time, patience, and any offered assistance,
Alexander

---

### Post by cryptotheslow on 2012-01-16
It sounds like you have some filesystem corruption happening. The large number of restarts to resolve the issue each time is due to the fact that every 30 (I think) times Ubuntu is configured to automatically check the filesystem for errors and fix them.

Which option are you taking to sleep, hibernate or power off when you close down normally?

Also - when starting up and you find yourself in the "frozen" state can you press Ctrl Alt F1 (together) and get to a tty (a white text on black background login prompt)?

---

### Post by cyanidearsenic on 2012-01-17
Hello,
Thank you for your reply. Yesterday I installed rkhunter and NoScript on Firefox and the computer came on the first time I tried without disk check today but I'm not getting my hopes up in case it was a fluke. 
To reply to what you said, when I close down normally I use the 'shut down' option listed in the drop down with system settings and software updates. 
As for a 'tty', I don't know, I've never heard of that. I've written it down for tomorrow in case it doesn't come on right away and will let you know then.
Thank you again!

---

