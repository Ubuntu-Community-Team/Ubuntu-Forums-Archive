---
title: "Cant stop wont stop"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by volpne on 2008-09-08
Hi,
Im a recent convert to Ubuntu, but since yesterday Im having problems trying to quit or do a restart.

Symptoms- After calling the quit dialog box, from within the systems drop down menu, the desktop tool bar disappears and the quit box, where you can choose restart, quit etc., never appears, forcing me to press the reset/power off button on the computer.

Is there a Ubuntu equivalent to ctrl + alt + delete?
Why is the desktop tool bars disappearing 


Although this could be a coincidence at about the same time Firefox updated its-self, loosing all my bookmarks and somehow disabling the google search bar also youtube will only play for second before freezing, I only mention this in case theres a clue to the quiting problem.

Thanks in advance
V

---

### Post by tangibleorange on 2008-09-08
i'm afraid i can't help you with the problem, but when the bar disappears, you can try pressing:

Ctrl + Alt + Bksp

this should bring you back to the login screen. failing that, try:

Ctrl + Alt + F1

then login at the prompt and type:

```
sudo shutdown -h now
```

---

### Post by knix on 2008-09-08
Ubuntu uses Ctrl+Alt+Delete, but what it does depends on your configuration. You can use Ctrl+alt+Backspace to restart the xserver (this kills all your processes that you started because it logs you out), the shut down from the login prompt.

---

### Post by Marshal0505 on 2008-09-08
ctrl+alt+backspace closes your gdm session
But the correct procedure for closing a non responsive (freezing) session would be to hold down alt+sysRq and press these keys r s e i u b (raising skinny elephants is utterly boring). I got these from several threads on these forums but i'm feeling lazy atm so i can't find the search function :p

---

### Post by volpne on 2008-09-08
Thanks 
The problem is really the disappearing tool bar not to sure if thats the right terminology. The bar along the top, 
Applications  Places  System, 
also the bar at the bottom where you see all the programs that are running.
So if I minimise a program I cant maximise it back again.
This only happens after I try to quit Ubuntu, the bars disappear but everything keeps running.

---

### Post by tangibleorange on 2008-09-08
> **volpne said:**
> Thanks 
The problem is really the disappearing tool bar not to sure if thats the right terminology. The bar along the top, 
Applications  Places  System, 
also the bar at the bottom where you see all the programs that are running.
So if I minimise a program I cant maximise it back again.
This only happens after I try to quit Ubuntu, the bars disappear but everything keeps running.

hmm well i don't know why its doing that. all I can suggest is that instead of clicking "shutdown" from the menu, you go to a terminal and type:

```
sudo shutdown -h now
```

or replace -h with -r if you want to reboot. You might also be able to press Ctrl + Alt + Bksp, then logout from the login window. the first way is more failsafe, however.

good luck!

---

