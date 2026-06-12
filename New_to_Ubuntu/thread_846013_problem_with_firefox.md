---
title: "problem with firefox"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by xieu90 on 2008-07-01
hi everyone
I'm using Hardy 64 now and I updated my firefox to the newest one, also not the beta
this problem happened long ago with feisty and gutsy too, but now it annoy me so much
I open firefox and use it for a while
sometimes when I close a tab and my screen becomes black like in Dos
and I can read this :
starting anac (h) ronistic cron anacron      OK
starting deffered execution scheduler atd    OK
starting period command scheduler crond      OK
checking battery state                       OK
Running local boot scrpit (/etc/rc.local)    OK

yeah, it is PC and not Laptop, so I don't have any battery.
I had to restart my computer, are there any methods, that I don't have to restart my computer and still can continue to use it (with GUI !) ?

---

### Post by xieu90 on 2008-07-01
no one ?
please !!!!!

---

### Post by ChameleonDave on 2008-07-01
Your X session has crashed.  You can switch between sessions with Ctrl + Alt + function keys.  Can you get to a screen where you can log in?

---

### Post by xieu90 on 2008-07-01
yeah
I pressed CTrl Alt F1 and so on
if I remember well Ctrl Alt F7 is where I have GUI
I can log in by other but without GUI

if I stay by CTrl Alt F7 and press things it will just write what I type and do nothing
except Ctrl Alt Del ----> restart
what can I do to revive X session?

---

### Post by sayakb on 2008-07-01
If you can get into tty1 (to 6) by pressing ctrl+Alt+F1(to F6), type:
```
startx
```
To get into X

---

### Post by xieu90 on 2008-07-01
thank you
now I need to wait till my computer crash
I will give an answer when I can try ^^ 
when will you crash my computer ?
please please! crash ! crash !:lolflag:

---

### Post by ChameleonDave on 2008-07-01
When you get to a tty screen, you will probably have to log in first.

If you find that you are already logged in, you may have to interrupt another command that is running by pressing Ctrl + C.

Either way, the aim is to get a screen that will accept commands, such as "ls".  You can then try stuff like "startx" or "sudo gdm", or indeed "sudo shutdown -h now" or "sudo reboot".

---

### Post by xieu90 on 2008-07-07
finally my computer crashed
I pressed Ctrl C then typed startx or I changed to Ctrl Alt F1 and typed startx 
I dont remember which one but then I heard my music continues to play for around half or 1 Seconds
It sang: what a wonderful world
then ....
nothing will happened, the monitor became total black 
my keyboard and mouse are total dead Ctrl Alt from F1 until F12 doesnt work
even ctrl alt del
and I was forced to press restart button

any other ideas ?
please !!!!

---

