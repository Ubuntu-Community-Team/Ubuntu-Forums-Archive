---
title: "lxqt-config-monitor SEGFAULT (my workaround) on lubuntu for 2-monitor setup"
date: 2020-12-16
forum: New to Ubuntu
---

### Post by moan-chomsky on 2020-12-16
My big question is; where do I submit little helpers like this so other people don't have to cludge around like I did? >>> pasting:


Normally when I use lxqt-config-monitor it results in a SEGFAULT when I try to make a change to my existing setup, or even save my current configuration.  If you want, I can ltrace or strace it for you.  I assume lots of other people are running "dual head" with 2 monitors connected to a laptop, like I do.   I think its a limitation of the laptop that makes it such  that I can't run all 3 at once- so I disable my laptop's display because it is the smallest.  Anyway, my workaround is to use a different program altogether to achieve changes in display configuration.  Namely, I use this approach:


 kscreen-doctor output.VGA-0.position.0,1080 output.HDMI-0.position.0,0

And it works flawlessly.  I've already submitted my crashdumps via ubuntu-bug

Thanks!

---

### Post by guiverc on 2020-12-16
> **moan-chomsky said:**
> My big question is; where do I submit little helpers like this so other people don't have to cludge around like I did? >>> pasting:



Welcome to Ubuntu Forums.

Where you submit little *helpers* is up to you.  I'll suggest

- Lubuntu's discourse ([https://discourse.lubuntu.me/](https://discourse.lubuntu.me/)) 
- Ask Ubuntu ([https://askubuntu.com/](https://askubuntu.com/))
- Ubuntu Forums (here, I'm betting you don't need a link).

Each has it's *pros* & *cons*. 

Ask Ubuntu is a *Question & Answer* site, so you ask a question (ie. outline your problem) and then propose your own answer as a fix. Other users can ask questions (made in the form of *comments*), before a time-elapsed is reached allowing the OP (*original poster*) to decide which is the best answer & accept it (the person who accepted answer gains SE *rep* points).  The primary benefit here is this site is designed so search engines find the results, which may mean its easier to find for others having the same problem.

Lubuntu's discourse allows Lubuntu *developers* to see it, comment or note it, where it may make as a goal for the *development* release. A fix for the existing release is also possible, but fixes for future releases are more probable.

This site, we can just comment. Solved answers too may make it into search results like askubuntu (I suspect more so if marked as SOLVED; though same applies with askubuntu too)


I would also include your release details.. Even if I'm not using your release, if I read the issue occurred with a specific release that may not be my own, I can consider the differences that occurred between your release and my own..  *Even without technical knowledge of changes, I can with a command know my package version, a search online using packages.ubuntu.com will tell me the package on the release you talk about.. and just the difference between those package version numbers is a pretty big clue; a online search will confirm or I can view the changelog quickly to see from the latest to the oldest of those two*.  Even if I lost you with this explanation, release details are useful just by date alone (*groovy* is 20.10 so I know the year & month.. that's not my release.. but the number of months from 20.10 to my release gives me a quick easy clue)


From your description of the issue, I'd check your file ownership of config files, esp. if you've ever run a GUI program with elevated privileges (eg. `sudo pcmanfm-qt`).

*I had a quick look for the bug report, I didn't find it (I assumed lxqt-config package)*

---

