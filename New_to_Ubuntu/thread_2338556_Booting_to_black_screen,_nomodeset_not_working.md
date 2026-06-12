---
title: "Booting to black screen, nomodeset not working"
date: 2016-09-29
forum: New to Ubuntu
---

### Post by supadave on 2016-09-29
Hello!

i am a new Ubuntu user and trying to settle this issue that just came up today. Got Ubuntu about 3 weeks ago and installed it on a fresh sad in my old MacBook. Today, after working reasonably well (a few reboots necessary here and there) it stopped booting properly. I dont think there were any updates done in the last day or two, and I can't figure out what would have triggered the problem.

heres what happened, and what I have tried.

1. I was usingen my computer this morning. Closed it, opened it, and the computer was stuck on a black screen. Not blank, the pixels are lit up but black. Restarted several times and got the same thing. Took out the battery and restarted in case that would help.

2. Following this post: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162078#162078](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162078#162078)
i changed quiet splash to nomodeset-- got a screen of code where all the lines begin with something limit ar to this sort of thing, over and over:
[    1.335980] ehci-pci 0000:00:04.1 irq 22, io mem 0x93389200

and then the screen goes nowhere.

tried also replacing quiet splash with no splash and got same screen
same with Radeon.modeset=0

help! My google tolerance isn't so great, and I am just using a cell phone!

---

### Post by supadave on 2016-09-29
[ATTACH=CONFIG]271425[/ATTACH] Here is the screen I get.

---

### Post by supadave on 2016-10-09
The problem solved itself. No idea how/why.

---

### Post by RobGoss on 2016-10-09
Sounds like it fixed it self that's good. Can you mark this thread as solved you can use the **Thread tool **at the top of this post. Thank you

---

### Post by supadave on 2016-10-27
Sure thing, thanks!

---

