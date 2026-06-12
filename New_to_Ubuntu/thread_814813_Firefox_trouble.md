---
title: "Firefox trouble"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by BlackSwordD2 on 2008-06-01
i have two main issues i need to fix

the first one is that almost 90% of the time i want to watch a video on the internet (such as youtube or collegehumor) it almost always closes


the second which i think may just be my graphics card, but videos that i watch online are blocky and distorted and lags behind whats really happening. why i think this might not be my card, is that videos i have uploaded or downloaded directly to the computer in full screen run flawless

i'd really like to have these fixed, a friend suggested to me that it might just be because of the new version of firefox hasn't worked out all the bugs yet, should that be the case can i downgrade my firefox so i dont beat my head into the keyboard any more?

many thanks

---

### Post by doorknob60 on 2008-06-01
Sounds more like a Flash bug to me. I'd advise removing Flash 9 and installing the Flash 10 beta, which works a lot better for me. [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by sayakb on 2008-06-01
```
sudo apt-get install htop
```
While watching videos, can you post the output of:
```
htop
```

Looks like you are running out of system resources. What are your PC specs?

---

### Post by dracayr on 2008-06-01
If you use gnash, uninstall it and use the adobe plugins instead

```
sudo apt-get remove --purge gnash
```

dracayr

---

### Post by BlackSwordD2 on 2008-06-01
> **LinuxIsInnovation said:**
> ```
sudo apt-get install htop
```
While watching videos, can you post the output of:
```
htop
```

Looks like you are running out of system resources. What are your PC specs?

well some odd reason i cant copy it

but it is running at near 100% cpu and what seems to be taking up the bulk of that is something of the command /usr/bin/X :0 -br where the rest is firefox

---

### Post by dracayr on 2008-06-01
gnash has this bug that it takes nearly 100% cpu. just try the command I posted above.

dracayr

---

### Post by BlackSwordD2 on 2008-06-01
> **dracayr said:**
> gnash has this bug that it takes nearly 100% cpu. just try the command I posted above.

dracayr

i did try the code and it told me that i didn't have gnash installed

---

### Post by BlackSwordD2 on 2008-06-01
> **doorknob60 said:**
> Sounds more like a Flash bug to me. I'd advise removing Flash 9 and installing the Flash 10 beta, which works a lot better for me. [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

well i tried this method and it didn't seem to solve the problem, though it does seem to load my videos faster they are still laggy

---

