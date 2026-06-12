---
title: "Half Screen"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by JChiocca on 2012-12-01
Hello all, this is my first time installing Ubuntu and second time installing Linux so I am pretty much a total newb, forgive my newby-ness.  :)

One of my friends recently gave me his old PowerPC G5. I have been trying unsuccessfully for about three days now to install Ubuntu 12.04 LTS on it. 
I have reformatted it and managed to work out most of the bugs in it but there is one I cannot seem to fix, and that is the screen: when I start the machine, it gets to yaboot then the monitor displays "Input out of range" before I can even see the Ubuntu Logo (As soon as I should start seeing things.) 

I have done some research and found out display problems are pretty common with the G5. I then was lead to try typing in 
"Linux video=TV-1:d" in the yaboot prompt. When I did I was pleased to see everything was normal except one thing, about one half of the screen is not being displayed!!! Does anybody know some commands I could type in to fix this? 

Computer Exact Specs: 

Dual liquid cooled 2.3 GHz PowerPC 970FX G5s 
NVIDIA GeForce 6800 Ultra DDL 
2.5 Gigabytes of PC3200 DDR SDRAM 
250 Gigabyte 7200 RPM harddrive

---

### Post by 2F4U on 2012-12-01
There is a very nice documentation/FAQ on PPC available here:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by JChiocca on 2012-12-01
Thank you 2F4U for the quick reply, I looked on those for a little bit and it said enter to enter on yaboot:"Linux video=ofonly"

This worked however I am still only getting half a screen.  :confused:

---

### Post by JChiocca on 2012-12-01
Also after entering:"Linux nouveau.modeset=0" I got into the Ubuntu but everything was weird colored and ultra low res...

---

### Post by JChiocca on 2012-12-08
UPDATE: entering "Linux video=ofonly" made it work (with half a screen) as well, I changed the conf.org file so I don't have to type it every time and 800x600 res works but is too small can someone please help?

---

