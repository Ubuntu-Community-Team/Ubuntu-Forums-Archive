---
title: "Can't logout or ctrl-alt-backspace"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by TooRight on 2008-05-10
I upgraded to Hardy Heron with no problems at all, even got my compwiz desktop effects going in minutes, but one thing that my system will not do is let me log out properly, or even restart the xserver ( by ctrl-alt-backspace). All it does it turn the open windows black and either stall my machine, or else the entire screen goes black and nothing happens until I unplug my comp and start it up again.


Any ideas as to what could be causing this and how I could fix it?

Thanks in advance!


*** now what it's doing is showing one of the wallpapers in my wallpapers folder and nothing else, it just stalls there on the blank picture.

---

### Post by inportb on 2008-05-10
What video chipset have you got? Is it ATi/AMD, by any chance?
If so, are you using a recent fglrx?

---

### Post by macaholic on 2008-05-10
Just out of curiosity, what kind of graphics card do you have?

---

### Post by TooRight on 2008-05-10
It's an ATI... I had the same problem when I upgraded to Fiesty Fawn, but then it was solved by upgrading to Gutsy--- I'm hoping I won't have to wait for an upgrade to the next one to fix it this time, lol

---

### Post by mister_pink on 2008-05-10
I don't know how to fix your issue, but I can say you really don't want to be pulling the plug on your computer. A better option to safely shutdown is the magic sys rq key combos (google for more info). Basically, press and hold alt and the print screen button, then slowly (one key every 15 seconds maybe) type "REISUB". Youll notice thats "BUSIER" backwards to help you remember it. That will perform a safe reboot.

---

### Post by inportb on 2008-05-10
> **TooRight said:**
> It's an ATI... I had the same problem when I upgraded to Fiesty Fawn, but then it was solved by upgrading to Gutsy--- I'm hoping I won't have to wait for an upgrade to the next one to fix it this time, lol

Yep, I thought so. Try getting rid of atieventsd:

```
sudo update-rc.d -f atieventsd remove
```

Now, you can either reboot or kill all instances of atieventsd.

---

### Post by TooRight on 2008-05-10
Yessssssss, that worked!! Thank you soooooo much!! I rebooted after removing the atievents thingy and then got a blank white screen when I logged in, so I tried the ctrl-alt-delete thing and it worked, as does logging out!! Thanks a million guys... and thanks also for the reisub tip, that worked too!! :D

---

### Post by inportb on 2008-05-10
I'm glad that worked for you. Remember that when a new fglrx hits the repositories and you upgrade, atieventsd might be added again. The bug may or may not be fixed, but if you see the same problem, just remove it as you had just done.

---

### Post by TooRight on 2008-05-10
Thanks, I'll remember that... mannn, it's almost funny how simple that was... God I love this forum!! :D

---

### Post by JillSwift on 2008-05-10
I was having this same issue with my laptop and its Mobility Radeon X1400. I love this forum, too. =^_^=

---

