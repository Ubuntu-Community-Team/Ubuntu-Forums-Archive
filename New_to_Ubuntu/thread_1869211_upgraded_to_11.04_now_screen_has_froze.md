---
title: "upgraded to 11.04 now screen has froze"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by mushy365 on 2011-10-25
this is the third time i have upgraded or at least tried to upgrade to the new layout of ubuntu, everytime the same thing happens. it upgrades, when i restart i can log in with my uname and password then the new layout screen appears and the whole thing freezes, i cant click on any icon or the taskbar, i cant right click, i can move the mouse around clicking has no acting, no short keys work, ctrl atl t does not bring up a terminal etc... the first two times i just reformated back to old version, this time i got stuff i dont want to lose, i cant even shut down the pc without hitting the power button on the box.

---

### Post by cryptotheslow on 2011-10-25
What graphics card do you have in the machine?

And when you get to that useless desktop can you press Ctrl-Alt-F1 (all 3 together) to get to a basic tty (text) login? If so if you login you should be able to do a:
```
 sudo shutdown -P now 
```

command to at least shut down cleanly.

Also - have you tried using the other desktop option from the login screen? Can;t exactly remember what it is called on 11.04 (maybe Gnome Failsafe??), but from the login screen you should be able to choose between full blown Unity and a fallback option.

If it comes to it - you can download and burn a 11.10 LiveCD / USB - boot from that - take the "Try Ubuntu" option (_**do not Install**_) and use that to rescue your home directory and other files off to an external drive etc. before nuking your install on the internal drive and reinstalling from scratch with w/e version.

---

### Post by mushy365 on 2011-10-25
thanks at the login screen choosing log in with no effects classic, allows everything to go back to normal. I guess its a graphics card problem them? i know compiz used to freeze my desktop when i put advanced effects on

---

