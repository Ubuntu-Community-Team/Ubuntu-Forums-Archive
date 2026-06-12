---
title: "Desktop partly missing and not responding"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by AndyN01 on 2012-04-21
Hello everyone,

First post as I've been able to use your combined knowledge to get to grips with anything I've needed - thanks - up to now!

I think the problem started after installing the last update a few days ago.

The log in screen comes up as before but the next stage is taking ages - even slower than Windoze....

Then the desktop is missing the "top line" (the one with Go etc. on the left hand side and date, time etc. on the right).

Also if I hover over the "icons" down the left hand side there isn't the "text" that tells you what it does and clicking on them does nothing at all.

So, eventually, I have a desktop to look at but zero function.

Help!

Thanks in advance.

Andy.

---

### Post by NikTh on 2012-04-21
Hi , 
if i understood correctly you use Unity ? If yes then open a terminal and try this command 
```
unity --reset
```

---

### Post by AndyN01 on 2012-04-21
Thanks

Tried that using "Ctl+Alt+T" to access the terminal as clicking on the desktop has no effect (Left or Right click makes no difference).

Lots of lines of text then stops.

Re booted but no joy I'm afraid. Still nothing works, no internet, no Libre docs and no "top bar".

I'm using 11.10 and at boot I see version ...3.0.0-17-generic.

I get the password screen, can login, then comes the "music" and the tiles down the left hand side but then nothing works and no date or time etc.

All other ideas very welcome.

Andy

---

### Post by emma157 on 2012-04-21
thanks i was facing the same problem :confused:

---

### Post by NikTh on 2012-04-22
> **AndyN01 said:**
> Thanks

Tried that using "Ctl+Alt+T" to access the terminal as clicking on the desktop has no effect (Left or Right click makes no difference).

Lots of lines of text then stops.

Re booted but no joy I'm afraid. Still nothing works, no internet, no Libre docs and no "top bar".

I'm using 11.10 and at boot I see version ...3.0.0-17-generic.

I get the password screen, can login, then comes the "music" and the tiles down the left hand side but then nothing works and no date or time etc.

All other ideas very welcome.

Andy

Hi , 
When login screen comes up hit Ctrl+Atl+F2 for a Virtual Terminal (or console , i don't now the correct name  :rolleyes:  ) 
Then login with your username & password and give the following commands one by one : 
```
sudo service lightdm stop
sudo apt-get update ; sudo apt-get upgrade 
sudo apt-get autoremove ; sudo apt-get autoclean 
sudo apt-get install -f 
sudo dpkg --configure -a 
sudo service lightdm start
```Write them down to a paper if you want because no desktop environment will be present.

---

### Post by carrucha on 2012-06-28
Had a similar problem after a power failure.  This fixed it, thanks

---

