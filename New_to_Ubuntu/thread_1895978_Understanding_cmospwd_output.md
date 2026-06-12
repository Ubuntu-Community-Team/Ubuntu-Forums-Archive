---
title: "Understanding cmospwd output"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by elgordodude on 2011-12-15
I'm helping a friend fix his daughter's dell/toshiba laptop that suddenly started asking for a bios password.

Already tried removing the cmos to no effect. 

Tried a couple of other things on the internet to no avail so I yanked the hard drive and ran cmospwd Which gave me the following output:

Award 6.0                    [ A  fjG ][][T b  F ;][]Award backdoor [        ]

Which leads me to my question. What's up with the brackets? Are these three different passwords? I'm doubtful about the backdoor, but what's up with the other two? Anyone with a little more experience able to help before I put the machine back together, because it is in a lot of pieces at the moment...

---

### Post by yiannis66 on 2011-12-16
The eazy way for the most of compiuters is to remove the battery for a few minutes .[IMG]http://img97.imageshack.us/img97/7473/c01357128.png[/IMG]

---

### Post by elgordodude on 2011-12-16
> **elgordodude said:**
> 
Already tried removing the cmos to no effect. 


Thanks for the picture, it's time for the command line.

---

### Post by anewguy on 2011-12-16
If that doesn't work, try to get hold of a copy of the resource CD from Dell.  It include a utility (I can't remember the name at the moment) that will do things like reset the BIOS master password, the BIOS password that allows changes to be made to the BIOS, etc.. There are also a few "master" passwords that you can find on the net for Dell, but in my experience they don't work.

Best of luck!

Dave ;)

---

### Post by elgordodude on 2011-12-19
Ultimately I had to jump a pair of pads on the motherboard, strange because it was one of the things I tried before cmospwd, but at around the 12th time it decided to work.

---

### Post by anewguy on 2011-12-20
That's another way to do it ;)  Glad you found that and that it worked.  I've tried that on a couple of Dell's in that past and never got it to work - I think I might even have blown the IC when I did so on one of them as I had to replace it and didn't know about everything tied to that one little chip.

Anyway, I'm glad you found your solution.  The levels of passwords that Dell has, at least on some of their older systems, can make getting into the BIOS or even just booting the system a real challenge.  Some people buy cheap Dell's (as I'm sure others - I'm not a Dell basher) on EBay without realizing they can be locked out at various levels - refusing to boot, not able to change anything (including boot order) in the BIOS, etc..  It can be an expensive and frustrating experience for those who aren't aware and prepared for what they might receive.

---

