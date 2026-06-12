---
title: "Is there a native compression program for Linux?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-05
I needed to make a few back ups of some DVD's I had when I realized I didnt have a compression program. I suppose I could run DVD Shrink with Wine if I had to, but I was wondering if there are any native Linux programs that do the same thing.

It would need to compress the files to be able to fit into a 4.7 DVD and it would need to encrypt into an ISO file.

---

### Post by Monicker on 2008-05-05
Probably the closes thing is gzip, which is often used in conjunction with tar.  You can use if from the command line or the gui.

*EDIT: Disregard above. I was not thinking specifically about DVDS.*


DVDrip and acidrip are good applications for dvd ripping.

---

### Post by legatek on 2008-05-05
Use K9copy, it's in the repositories.

---

### Post by Bigtime_Scrub on 2008-05-05
> **legatek said:**
> Use K9copy, it's in the repositories.


Thanks, I think K9Copy is what Im looking for. I tried it out just now and it spit out some weird ISO that was only 128 MB. Im going to fool with the settings and see what I can get. 


I had to get an update to, so for people that dont know:

System-> Administration->Software Sources->Third Party Software

check all boxes and close

Code:

sudo apt-get update

then:

code:

sudo apt-get install K9Copy

---

