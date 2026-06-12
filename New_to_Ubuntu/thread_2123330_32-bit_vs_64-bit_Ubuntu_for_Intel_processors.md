---
title: "32-bit vs 64-bit Ubuntu for Intel processors"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by lusbyclark on 2013-03-07
Almost a year ago I purchased a generic PC with an Intel® Core™ i5-2320 CPU @ 3.00GHz × 4 processor on a GigaByte mother board with 8Gbytes of RAM and a 128 Gbyte solid state hard-drive.  When I look at System Settings/Details I see that the operating system is listed as a 64 bit system.

Today I was talking with the guy who built my PC and he told me he was told by* Ubuntu* that the 32-bit version of Ubuntu is some how better than the 64-bit version when hosted by an Intel processor.  *Better *was said to refer to better software compatibility.

Is there any truth in this claim?  I must say I haven't noticed anything particularly adverse going on with my PC.  What's up with all this?

---

### Post by arpanaut on 2013-03-07
Nope, the guy saying that was misinformed.
If you have 64 bit hardware you are best served by using 64bit Ubuntu.

Canonical recommends 32 bit because it will work on either platform and eases confusion for some people as to which to download.
It is a wrong conclusion that AMD64 is just for AMD cpu's. They were the first to implement 64bit so they got that tag.

---

### Post by Cheesemill on 2013-03-07
No truth in that at all.

There's a couple of reasons he may think that's true. First of all the Ubuntu website suggests 32-bit as recommended on the download page (for all machines). This is simply because the 32-bit version will run on all machines whereas the 64-bit version will only run on 64-bit machines. Canonical don't want people to become disillusioned with there first attempt at installing Ubuntu by downloading a file which doesn't work, hence the suggestion for 32-bit.

The other reason people get confused is because the 64-bit download is prefixed with amd64. This doesn't, however, mean that it is only suitable for machines with an AMD processor. Amd64 is the name of the architecture of the CPU, not the manufacturer. AMD were the company who first developed the 64 bit instruction set which is now used on all modern processors and they named this architecture amd64. Intel now license this technology from AMD and use it in all of their processors as well, so the amd64 bit of the iso name simply means 'for all 64-bit processors'.

Edit - Ninja'd by arpanaut :)

---

### Post by craig10x on 2013-03-07
Exactly, the 64 bit version is for amds and intels alike...i guess the "name" can be confusing and makes you think it isn't intel compatible but it is...
I have a current toshiba laptop with intel processor (i3 core) and intel graphics and i run 64 bit version and it's very speedy and works fine...

---

### Post by gifford on 2013-03-07
As for software compatibility, 12.04 is multi-arch and runs many 32 bit applications without a problem.

---

### Post by lusbyclark on 2013-03-09
Well, wouldn't you know it, I just got use to the previous set-up and now with this new set-up, I can't locate the button to mark this thread as solved.

---

### Post by squakie on 2013-03-10
If you look at the top of the page, you first see the Ubuntu area, then the Reply To Thread box, then the following line has the Thread Tools option on the right - click there and mark as solved.

---

### Post by arpanaut on 2013-03-10
> **squakie said:**
> If you look at the top of the page, you first see the Ubuntu area, then the Reply To Thread box, then the following line has the Thread Tools option on the right - click there and mark as solved.

Not Anymore: [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730)

---

### Post by lusbyclark on 2013-03-10
I really do appreciate that you fellows took the time to help me find my way to the "Mark as Solved" button.  I did find the big red "Reply to Thread" button.  I had to click it to get to this page.  I also found the "Thread Tools" button on the next line down and over nearer the right hand edge of the screen.  I clicked on it and found only three options:

 

                            			Show Printable Version

                            			Email this Page...

                            			Subscribe to this Thread...


 			
 I must have done something wrong?

---

### Post by woxuxow on 2013-03-10
I have ubuntu 12.10 32 bit on my 32-bet pc, that is good
i have had installed ubuntu 12.04 64-bit on my aunt and brother`s laptop it was not bad but not excellent just like 32-bit
i think having 64-bit os has its advantages but my 64-bit experience  was awful

---

### Post by Cheesemill on 2013-03-10
> **MustafaJF said:**
> I have ubuntu 12.10 32 bit on my 32-bet pc, that is good
i have had installed ubuntu 12.04 64-bit on my aunt and brother`s laptop it was not bad but not excellent just like 32-bit
i think having 64-bit os has its advantages but my 64-bit experience  was awful

I think what you meant to say was in your experience 12.10 was better than 12.04.

There is absolutely no difference in functionality between the 32-bit and 64-bit versions of a Ubuntu release.

---

