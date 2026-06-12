---
title: "[SOLVED] Ubuntu 8.04 crash time"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by P235 on 2008-06-15
Hi, I just recently upgraded to 8.04 by formatting my root partition on my HP Pavilion N5495 laptop.  The installation was smooth and everything works like clockwork.  Unfortunately, I have found that if I let my laptop run overnight it tends to crash.  All I see is a black screen and there is no response from ctrl-alt-backspace or alt-sys rq-r,s,e,i,u,b.  

I tried to review the log for some clues, but I find that there are only records up to the time I stopped using the laptop the last night and when I force boot it the following morning.  I'm guessing some sort of automated task could be crashing my laptop in the wee hours of night, but I'm not sure how to check that out.

---

### Post by spiderbatdad on 2008-06-15
How about Power Management:
On ac power: "Put computer to sleep = never"

---

### Post by P235 on 2008-06-15
Hi, it seems never is the default setting.  Also, my laptop just recently crashed just like it tends to do overnight.  I open up the cover with a black screen and there is no response to the mouse or any of the other commands mentioned above.  Now I'm not sure if it's an automated process or something else.  But, it has consistently crashed overnight for the past three days so I still think there is a clue there.

---

### Post by MasterSander on 2008-06-15
That certainly is weird. What apps keep on running overnight?

---

### Post by waspbr on 2008-06-15
hmmm... I think I know why... I have an HP tx1320us and inherently it has some hibernate/suspend issues with ubuntu. I think that when you leave it running all night it hibernate/suspends and it can't get back. Some people have been trying to fix that (or actually have)  for my laptop so odds are that someone prolly has a solution for your specific laptop somewhere in the forums. 

I haven't really looked very deeply into it so I can't help much. Though one solution would be to tweak your power management settings.

---

### Post by P235 on 2008-06-15
From what I recall, Firefox, gedit, conky were running at the time.  I've left these programs running each night after the first time.  

As for the power management settings, I try to avoid the hibernation and suspension features.  

Perhaps I should run a few memtests, but the RAM is pretty new.

---

### Post by P235 on 2008-06-20
Thanks for the tip waspbr, I followed up with a few searches and found that my crashes were shared with a number of others:

[http://ubuntuforums.org/showthread.php?t=786311&highlight=turn+suspend+hibernate](http://ubuntuforums.org/showthread.php?t=786311&highlight=turn+suspend+hibernate)

Apparently the latest kernel update should fix the problem.

I'm just glad the crashes didn't continue long enough to form errors on the hard drive.

---

