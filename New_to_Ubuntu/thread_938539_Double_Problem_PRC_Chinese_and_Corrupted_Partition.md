---
title: "Double Problem: PRC Chinese and Corrupted Partition"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by V8VN7V on 2008-10-05
Its like Microsoft was watching and waiting for the termination of my warranty on Vista.  No matter.  Test driving Ubuntu to see if this is really all I will need.  However, 2 problems immediately emerge!

1) This may sound crazy, but I need to open old .doc files that contain mixes of simple and traditional PRC Chinese and English.  For some reason Ubuntu seems to have a monolingual mindset going.

2) Also, I was going to set aside a whole gigabyte of partitioned space for swap area but alas it was corrupted after I waited all that time.  What's to be done with it then?  Don't worry, I still have a whopping 10 gigs set aside for Ubuntu.  

Maybe you don't know the answer to this question, just leave tips or something.  I'd love to hear from everybody who reads this really.  I have no bloody idea what I'm doing but on the sage advice of many including Timo, here I am at last jumping into the fray!  Its kind of scary thinking about slicing my hard drive into subdivisions with not so surgical precision and the possibility of not being able to play World of Warcraft unless I reboot back into that land of fail that is Vista.  Moral support is much appreciated!

Oooh, also how to I get that neat cubed workspace effect?  I seem to remember that being the most endearing feature.  

10 PRINT HELLO UBUNTU;

---

### Post by ibuclaw on 2008-10-05
Upon which part of using/installing Ubuntu did you get a corrupted partition error?

If you are still in the LiveCD, you can use the Partition Editor to set the partitions the way you want, then install ontop of them.

Although, I recommend that you defrag your Window NTFS partition first. And if possible, shrink the size of it using Vista (if that is possible).

Regards
Iain

---

### Post by bumanie on 2008-10-05
Hello, and welcome.
1) To enable chinese System --> Administration --> Language support and install asian language pack (I think it's called). Then System --> Preferences --> SCIM input method needs to be enabled. Chinese should then be available in open office.
2) Choose manual at the partitioning stage of the ubuntu install and you should be able to format the same 1gb area to be used as swap. 10gb is not a lot of space for ubuntu, it's adequate, but by the time one installs programs coedecs etc, / will use 4-5gb.
3) This is a bit old, but should give you an idea re [desktop effects]("http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion"). It is going to be enabled as default in Itrepid Ibex due for release October 30th.

---

### Post by V8VN7V on 2008-10-05
> **tinivole said:**
> Upon which part of using/installing Ubuntu did you get a corrupted partition error?

If you are still in the LiveCD, you can use the Partition Editor to set the partitions the way you want, then install ontop of them.

Although, I recommend that you defrag your Window NTFS partition first. And if possible, shrink the size of it using Vista (if that is possible).

Regards
Iain

Already installed it in the partition that worked.  The partition originally set aside for swap was "unusable".  You're right, I should have run defrag.  Oh well, next time for sure!  This is the test run for the real project which is to wipe my other laptop completely and install Ubuntu exclusively.

---

### Post by V8VN7V on 2008-10-05
> **bumanie said:**
> Hello, and welcome.
1) To enable chinese System --> Administration --> Language support and install asian language pack (I think it's called). Then System --> Preferences --> SCIM input method needs to be enabled. Chinese should then be available in open office.
2) Choose manual at the partitioning stage of the ubuntu install and you should be able to format the same 1gb area to be used as swap. 10gb is not a lot of space for ubuntu, it's adequate, but by the time one installs programs coedecs etc, / will use 4-5gb.
3) This is a bit old, but should give you an idea re [desktop effects]("http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion"). It is going to be enabled as default in Itrepid Ibex due for release October 30th.

AHA! Many thanks!  My basic computing needs are now realized.  Time to go find plugins and what-not to spiff this up a bit.  The lost partition DID happen in manual.  Sadness.  Good thing I didn't make it too big. Thanks again.

---

