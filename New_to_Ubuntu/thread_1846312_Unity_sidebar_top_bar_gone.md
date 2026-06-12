---
title: "Unity sidebar/ top bar gone"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by kemtnbkr on 2011-09-18
Hi, seeing as I'm a total n00b, I somehow managed to 'break' my Unity desktop environment by switching to Classic, then back. The sidebar never shows up, neither does the top bar.  I can't open any applications now; I got into Firefox by opening a text document on my desktop and going to 'Get Help Online' in gedit.  The Alt+F1 and Alt+F2 method to launch applications won't work either, although other keyboard shortcuts eg. for minimizing, closing, etc. still work.

I also (apparently n00bishly) have my desktop set to log in automatically, so I'm guessing if I could get back to the login screen, I could select 'ubuntu classic' for my session for a temporary workaround.

I'm guessing there's an easy fix to this; I'll supply any additional info as quickly as I can (I'm studying for a major midterm right now too, so I'm a bit busy).

Thanks in advance!

---

### Post by kemtnbkr on 2011-09-18
Oh, and btw, I'm obviously running 11.04, I just haven't updated my profile yet.

---

### Post by philipballew on 2011-09-18
Before I help you with a super technical issue can you run a command into the terminal for me? 
```
unity --reset
``` does that show anything?

---

### Post by kemtnbkr on 2011-09-18
Therin lies the problem- I can get into a terminal prompt with Ctrl+Alt+F1, but I don't know how to return to my current session from that so I've been having to reboot every time I try that.  Is there a way (other than the Alt+F1/F2 method) to open the windowed command prompt that you know of?  I pretty much have Nautilus, Gedit, and Firefox to work with currently.

---

### Post by philipballew on 2011-09-18
to close a terminal type exit. but what did that command do?

---

### Post by Krytarik on 2011-09-18
Please see this troubleshooting guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

---

### Post by kemtnbkr on 2011-09-18
OK, I used the Alt+Ctrl+F1 terminal ( had to re-login, but the music I had going came back as soon as I logged in, so I guess the same processes keep running?)

Anyways, the command yielded:   "unity-panel-service: no process found"

Sorry it took so long, I had to reboot (typing 'exit' brings me back to the login prompt)

---

### Post by philipballew on 2011-09-18
i'd play with his guide and try out ccsm and play with that

---

### Post by kemtnbkr on 2011-09-18
[Krytarik]("http://ubuntuforums.org/member.php?u=1187548"), I'm currently working my way through the troubleshooting guide. 

I should be a bit faster now that I can switch between the GUI and the tty quickly

---

### Post by kemtnbkr on 2011-09-18
Alright, that tutorial got Unity up and running again...  Thanks both of you

I'll mark the thread as solved right now too

---

### Post by technosysind on 2011-09-19
Logout and then login using ubuntu classic

---

### Post by Krytarik on 2011-09-19
> **technosysind said:**
> Logout and then login using ubuntu classic
Meaning? Given that the issue is already solved, and it was about Unity.

---

