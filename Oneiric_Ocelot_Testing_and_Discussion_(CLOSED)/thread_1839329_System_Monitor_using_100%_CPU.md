---
title: "System Monitor using 100% CPU"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alexvy13 on 2011-09-05
so everytime i try to open system monitor it freezes up the whole system [SIZE=-1]and uses 100% CPU. It only st[/SIZE][SIZE=-1]arted doing this tod[/SIZE][SIZE=-1]ay.
I h[/SIZE][SIZE=-1]ad the system monitor indic[/SIZE][SIZE=-1]ator [/SIZE][SIZE=-1]and i thought m[/SIZE][SIZE=-1]aybe it w[/SIZE][SIZE=-1]as conlficting so i exited it [/SIZE][SIZE=-1]and then tried the [/SIZE][SIZE=-1]app but it still froze up. 
I uninst[/SIZE][SIZE=-1]alled it, [/SIZE][SIZE=-1]and it would still freeze.
I then inst[/SIZE][SIZE=-1]alled the system lo[/SIZE][SIZE=-1]ad indic[/SIZE][SIZE=-1]ator (the one th[/SIZE][SIZE=-1]at uses colorful gr[/SIZE][SIZE=-1]aphs) [/SIZE][SIZE=-1]and it would still freeze up
The f[/SIZE][SIZE=-1]an is [/SIZE][SIZE=-1]also running [/SIZE][SIZE=-1]all the time, loud, [/SIZE][SIZE=-1]and[/SIZE][SIZE=-1] it doesnt stop even if stop using the computer for [/SIZE][SIZE=-1]a while.
Could zeitgeist (before i downgr[/SIZE][SIZE=-1]aded it) h[/SIZE][SIZE=-1]ave messed up some h[/SIZE][SIZE=-1]ardw[/SIZE][SIZE=-1]are [/SIZE][SIZE=-1]and th[/SIZE][SIZE=-1]at's why the f[/SIZE][SIZE=-1]an won't stop?
[/SIZE][SIZE=-1]and why is system monitor using so much CPU? When i don't h[/SIZE][SIZE=-1]ave it open i h[/SIZE][SIZE=-1]ardly go [/SIZE][SIZE=-1]above 5% CPU [/SIZE][SIZE=-1]and my memory is low too. 
[/SIZE][SIZE=-1]any ide[/SIZE][SIZE=-1]as?[/SIZE]

---

### Post by Script Warlock on 2011-09-05
check your processes with "top in the terminal and see the culprit.. there's a discussion regarding to [zeigeist]("http://ubuntuforums.org/showthread.php?t=1837836") maybe you can check it out.

---

### Post by alexvy13 on 2011-09-05
ive dont top before and it says my CPU is low. it only freezes when i open system monitor and thats when my CPU spikes.

and i've read the zeitgeist thread but my cpu went low again after downgrading it, and it is low, except for when i open system monitor.

but i think it may have messed some hardware :/ i just logged on to windows and im still getting the high fan speed with low CPU D:

is there a way to lower the cpu fan speed? i know in windows if you change power options this will usually work but its not! :(

---

### Post by dino99 on 2011-09-05
sudo apt-get install fancontrol

sudo sensors-detect

sudo pwmconfig

---

### Post by alexvy13 on 2011-09-05
won't do sensors detect :/

---

### Post by alexvy13 on 2011-09-05
problem seems to be fixed; the batter went low and went to sleep and two seconds later when i pushed a button the fan was back to normal! :D

and now system monitor won't freeze! so it was like a random weird fix haha

but software center crashes on trying to install google chrome deb -_- oh well i guess ill just use chromium instead

---

### Post by alexvy13 on 2011-09-05
nvm its back -_-

---

### Post by mc4man on 2011-09-05
> **alexvy13 said:**
> 

but software center crashes on trying to install google chrome deb -_- oh well i guess ill just use chromium instead
Both S-C & gdebi will not install google-chrome atm, though dpkg will.
If using dpkg then better to install the add. deps 1st rather then fix broken packages later (that way your sources will get updated for google/chrome
```
sudo apt-get install libcurl3 libnspr4-0d libxss1
```
Then 
sudo dpkg -i /path/to/your/google-chrome.deb

There is a current bug on this S-C crash but it's private so not generally viewable
[https://bugs.launchpad.net/bugs/839113](https://bugs.launchpad.net/bugs/839113)

---

