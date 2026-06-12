---
title: "Using Lubuntu, cpu clock is locked at 600 mhz"
date: 2015-08-11
forum: New to Ubuntu
---

### Post by patrick101 on 2015-08-11
Not sure is this is the place to post this, but ill explain anyways.  I installed lubuntu onto my dell inspiron 8600 today, first time using any OS besides windows, so i am not too familiar with linux based systems, but i do have a good breadth of knowledge about computers in general.  I have gotten wifi working, and lubuntu is running, but it is running slowly.  after benchmarking the cpu i noticed i am at 600 mhz, and after extensive googling, found that many users come across the same problem, i have tried many solutions from others in diffirent forums with no results,  with cpufreq-info,  policy is at 600mhz - 600mhz and i cannot for the life of me change it to 600mhz - 1.5Ghz that my pentium M is rated for,  any help will be greatly appreciated,  as i am new to linux, any commands you ask me to do will need to be spelled out for me to copy/paste to the terminal, any explanation of what the command does would also be appreciated to help me understand more, but not necesarry, thanks for the help in advance!

Keep thinking of stuff to add, additional info will go here:
-battery is shot, so laptop is hooked up directly to ac adapter, i know some forums said this was a reason for causing th cpu downclock, but i couldnt fix the problem with the solutions given there
-distribution Ubuntu 15.04, Desktop environment LXDe (Lubuntu)
-forcepae was used to install from flash drive

---

### Post by kerry_s on 2015-08-11
since it's going to be plugged in, i would suggest you go into the bios & disable cpu scaling. just let it run at 1.5 all the time.

---

### Post by patrick101 on 2015-08-11
that sounds like a pretty good idea, however, i went into the f2 dell bios setting on reboot, and saw nothing pertaining to cpu scaling, i also held shift during reboot and went through pages 1-7 and found nothing for cpu scaling, how can i disable cpu scaling?

---

### Post by patrick101 on 2015-08-11
think i may hav solved problem, added cpu freq front end to panel with a right click, add / remove panel items, panel applets,+add, CPUFreq frontend. Is running at 1.50-1.50 Ghz now,

---

### Post by mörgæs on 2015-08-11
Good, then please mark the thread 'solved'.

---

