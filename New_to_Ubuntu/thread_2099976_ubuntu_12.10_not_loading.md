---
title: "ubuntu 12.10 not loading"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by julian foster on 2012-12-31
Dear all,

I am a complete novice. I downloaded ubuntu 12.10 and put it on a DVD to boot up a PC with a faulty operating system (Windows xp). However, it gets stuck before completing even the first step of installation. We are hoping to access the hard disk to retrieve data and put it on a new PC. Any suggestions?

Julian

---

### Post by grahammechanical on 2012-12-31
As you do not give any information that gives me a clue as to the point at which the live DVD stops working I will give standard directions.

1) At the first purple screen press Enter.
2) Select the language (default is English) and press Enter.
3) Press F6 and scroll down the list until nomodeset is highlighted. Press Enter.
4) Press Esc to back out of the selection menu.
5) Select Try. Press Enter.

See if that gets you to a live session. You may need to try the other options in the F6 menu or a combination of the  same.

Regards.

---

### Post by audiomick on 2012-12-31
Hi Julian. Follow Graham's advice. I just wanted to ask the neccessary dumb question...
You are sure that the XP machine has a DVD drive? If the thing is running XP, it is possible that it is only a CD drive...

---

### Post by julian foster on 2012-12-31
You're right, but we are using an external DVD drive, thanks anyway!

Happy new year.

Julian

---

### Post by julian foster on 2012-12-31
Graham,

Thank you for your simple and helpful advice, aimed at exactly the right level. Unfortunately, just at the point where it seems to have completed installing (all your 5 steps completed) the screen flashes up a message 'Adjusting' which alternates with blank black and purple screens. It seems to me as if something in the VDU is foxing the final step of installation? Is this possible?

Thanks again, happy new year!

Julian

---

### Post by audiomick on 2012-12-31
> **julian foster said:**
> ... the screen flashes up a message 'Adjusting' which alternates with blank black and purple screens. It seems to me as if something in the VDU is foxing the final step of installation? Is this possible?...

It does indeed sound as if it is having graphics problems. That is the reason for trying to get the "nomodeset" option running. That can help with video problems. You'd best wait for Graham for further advice. I believe, from what I have seen him posting in the past, that he is much better at that then I am.

Do you happen to know what the graphics card in the machine is?

---

### Post by superDave972 on 2012-12-31
I tried to help a friend with a similar problem. He had an old XP machine (Dell Dimension 3000) that he was trying to recover some files from. He had forgotten the passwords to all of his accounts so we had resorted to install Ubuntu to try and access them that way.

Any way, Ubuntu seemed to install fine, but upon reboot, the system would hang after POSTing and never actually boot into the Ubuntu OS. 

I never solved the problem, but I believe I was able to ID the problem. It turns out there must have been some sort of driver issue. The new Ubuntu OS did not support the older (about 10-12 years) hardware. 

I ended up wiping the entire hard drive and installing Vista. The computer has been working perfectly ever since. 

Perhaps your system is too old for Ubuntu to have the proper support for the hardware?

---

### Post by julian foster on 2012-12-31
Cheers. I'll wait for Graham, as you suggest. I'd have to rummage through various booklets to find out what graphics card it has. It's a moderately old PC (7 years?) so it could be a bit dated.

Thanks again.

julian

---

### Post by julian foster on 2012-12-31
You may well be right - it's about 7 years old and showing its age (slow, prone to crash etc). Are there old versions of ubuntu that might work?

Thanks for your help and advice.

julian

---

### Post by audiomick on 2013-01-01
How  much RAM has it got? If there is not enough there, the installer wont be able to run. If you think that might be the problem, the alternate installer, which is text based, might help you.

Have a look here. You might be well advised to run Lubuntu on that machine anyway.
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")



 If you want to try a standard Ubuntu, you could try the 12.04 alternate installer from here. There doesn't seem to be an alternate installer for 12.10
[http://releases.ubuntu.com/precise/]("http://releases.ubuntu.com/precise/")

---

### Post by steeldriver on 2013-01-01
Although I obviously don't want to discourage you from using Ubuntu :D , you might want to look at one of the smaller/lighter distros that are specifically targeted at this kind of thing e.g. systemrescuecd

[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

I've used that a number of times to retrieve Windows data on older XP machines - including my ancient Thinkpad X30 with pesky Intel graphics

---

### Post by julian foster on 2013-01-03
> **audiomick said:**
> How  much RAM has it got? If there is not enough there, the installer wont be able to run. If you think that might be the problem, the alternate installer, which is text based, might help you.

Have a look here. You might be well advised to run Lubuntu on that machine anyway.
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")



 If you want to try a standard Ubuntu, you could try the 12.04 alternate installer from here. There doesn't seem to be an alternate installer for 12.10
[http://releases.ubuntu.com/precise/]("http://releases.ubuntu.com/precise/")
Excellent suggestion! Lubuntu installed very nicely, partitioned off from whatever else is there. Unfortunately, it now won't run! This time we get a blank, dark screen with nothing but a cursor on it alternating with a completely black ('off') screen - no messages at all.

Thanks anyway, the saga continues..

---

### Post by newb85 on 2013-01-03
Forgive me if I'm misunderstanding, but isn't the primary goal here retrieval of your old files?  I would focus on that first.  File retrieval shouldn't require you to install any OS; you should be able to access the files in a Live session of any distro your hardware can support.  (As Graham mentioned, you should click "Try [L]Ubuntu".)

---

### Post by julian foster on 2013-01-04
> **steeldriver said:**
> Although I obviously don't want to discourage you from using Ubuntu :D , you might want to look at one of the smaller/lighter distros that are specifically targeted at this kind of thing e.g. systemrescuecd

[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

I've used that a number of times to retrieve Windows data on older XP machines - including my ancient Thinkpad X30 with pesky Intel graphics
You were absolutely right! I have now successfully used SystemRescue to retrieve many files from my dead PC. Thank you very much indeed.

Julian

---

### Post by julian foster on 2013-01-04
> **newb85 said:**
> Forgive me if I'm misunderstanding, but isn't the primary goal here retrieval of your old files?  I would focus on that first.  File retrieval shouldn't require you to install any OS; you should be able to access the files in a Live session of any distro your hardware can support.  (As Graham mentioned, you should click "Try [L]Ubuntu".)
Quite right - a previous respondent suggested SystemRescue, which worked a treat.

I am not a programmer or enthusiast and have very much used this forum as a means to an end. I would like to express my thanks to you all for your help - all freely given and well meant. This is a very considerate community and I'm seriously considering get a new computer and installing Ubuntu as my default OS.

My wife now thinks I'm a brilliant computer geek and is very grateful to me for retrieving her precious photos - only one of these is true!

Thanks again.

Julian

---

### Post by audiomick on 2013-01-04
> **julian foster said:**
> My wife now thinks I'm a brilliant computer geek and is very grateful to me ...

Well, it was all worth the effort then, wasn't it? :p

Glad you got sorted.

---

