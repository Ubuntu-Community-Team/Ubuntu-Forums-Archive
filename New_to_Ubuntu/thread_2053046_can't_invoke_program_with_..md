---
title: "can't invoke program with ./"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-04
Hello everyone,
 
I completed a successful program installation in  usr/local/bin (using autotools).  If I go to the /usr/local/bin directory and type ./proggy the program runs fine.   However, if I go to ~/proj and key in ./proggy the program doesn't run.  I checked env and the PATH includes /usr/local/bin.  So, I am puzzled...  
 
Any help would be great!
 
Thanks,
Mark Allyn

---

### Post by LiamOS on 2012-09-04
Are you running a 64 bit kernel?
If so, it might be that it's a 32 bit binary.

EDIT:

I should probably expand this out. use 
```
uname -m
```
to check your architecture. If you get 'x86_64', it might be that you have a binary that was build for an 'x86' target. You could possibly solve this by using 
```
apt-get install ia32-libs
```

---

### Post by Bashing-om on 2012-09-04
mark;
 Consider this.... the designation ./ says this directory only, right ?

As the program you want to run is in your path, will not just invoking the program with it's name not start it ?

[INDENT]regards <==BDQ


[/INDENT]

---

### Post by mark allyn on 2012-09-04
Hi Liamos and Bashing-Om
 
No, I'm running the 32 bit kernel.  Using 12.04.  If you have surmised that I am new to LINUX/UBUNTU you would be correct.
 
[LEFT]Now as for the idea from Bashing-Om...I shall test it out forthwith.  And of course let you know.
 
Thanks,
Mark [/LEFT]

---

### Post by mark allyn on 2012-09-04
Bashing-Om and Liamos
 
Bashing-Om was right!  Program ran.  Case closed.
 
Thanks,
Mark

---

### Post by marlow59 on 2012-09-04
please mark the thread as solved by using the Thread tool menu. Thanks

---

