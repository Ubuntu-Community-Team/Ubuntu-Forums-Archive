---
title: "Missing menu bars on windows"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by card_ace on 2011-11-07
So recently I've noticed that the menu bars on the tops of my windows aren't there anymore.  Not sure if this is a part of 11.10 or if I disabled something without realizing it.  Its like whatever I'm looking at just stops, there's no menu bar on top.  And I know that the "File - Edit - Tools" and all that is along the top of the screen.  When windows aren't full screen there's nothing on top.  I've attached a screenshot for clarification.  The only way to maximize windows is to use a keystroke or to use my desktop bar at the top, right click on the application, and choose maximize.  I would love to have my menu bars with the "close-resize-minimize" back

---

### Post by wildmanne39 on 2011-11-07
Hi, you will need to do this to get them back.
```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```
Then reboot.
Thank you

---

### Post by Miljet on 2011-11-07
I was rather confused about this too. I finally realized that the "disappearing" menu at the top of your screen IS the menu for whichever window currently has focus.

Unconvinced? Open three applications in the same workspace. Check the top menu. Then move focus to another application and check again. You will see that the menu changes with the application that has focus.

---

### Post by stinkeye on 2011-11-07
He's talking about the title bar missing for unmaximized windows 
and it could be the window decoration plugin has become disabled.
Before using ccsm, try restarting compiz to see if it fixes it.
alt+F2 and enter
```
compiz --replace
```

---

### Post by card_ace on 2011-11-08
I believe stinkeye is right.  It doesn't happen all the time, for example right now I have title bars on all of my windows.  but often after its been running for a long time and I've put it to sleep several times and woken it up again they aren't there.  So I'm guessing that plugin simply doesn't get restarted correctly

---

### Post by stinkeye on 2011-11-08
Sounds like it's just a matter of running **compiz --replace**
when your title bar disappears.

---

### Post by card_ace on 2011-11-08
That's what I'm thinking.  Next time they disappear I'll test it and get back to post the results.  Thanks!

---

### Post by card_ace on 2011-11-15
So its been about a week and my menu bars haven't disappeared again.  maybe my latest batch of updates fixed it?  Gonna mark this one as solved since the problem has ended.  Thanks!

---

### Post by donaldt on 2011-11-15
I am still running 11.04, but recently my title bars went missing.  No increase, decrease or X,  I suspect it is because I was messing about in Compiz and it is my fault.

I tried the compiz --replace.  Nothing happened.  I also tried the terminal with sudo apt-get (etc.) but got a reply that GTK-3 file was missing.

Anything else I can do to get them back again?  I've been afraid to upgrade to 11.10 because I hear there are other problems there that are worse than this.

Thanks if you can help!

donaldt

---

### Post by card_ace on 2011-11-16
I'd recommend starting a new thread.  You're more likely to get a response that way.  Good Luck!

---

### Post by uniomni on 2011-11-17
> **stinkeye said:**
> he's talking about the title bar missing for unmaximized windows 
and it could be the window decoration plugin has become disabled.
Before using ccsm, try restarting compiz to see if it fixes it.
Alt+f2 and enter
```
compiz --replace
```
:p

---

### Post by uniomni on 2011-11-17
Perfect, thanks

---

### Post by rburkartjo on 2011-11-18
this will work have the same problem when i log into a xfce session
put a shortcut to the compiz fusion icon on your desktop or toolbar.
then after you log in click on the icon and click on reload windows manager.

---

### Post by Crysius on 2012-02-13
> **stinkeye said:**
> He's talking about the title bar missing for unmaximized windows 
and it could be the window decoration plugin has become disabled.
Before using ccsm, try restarting compiz to see if it fixes it.
alt+F2 and enter
```
compiz --replace
```

Thank you for this very quick solution. I am in your debt.

---

