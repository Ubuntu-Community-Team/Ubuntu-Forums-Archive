---
title: "shutdown hanging"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-08-31
shutdown is hanging on a blank black screen

if anyone has a solution, great

but failing that, what is the safest way to shutdown my laptop...a bit wary of continually resorting to hard shutdown

---

### Post by vpharry on 2011-08-31
try reinstalling.... sorry buddy i cant help u coz i dont no anythin much about this problm

---

### Post by flipper T on 2011-08-31
hi vpharry

you should be careful about advising users to reinstall when you > dont no anythin much about this problm

friendly advice & welcome to the forum :)

---

### Post by dino99 on 2011-08-31
you have to know which process is still running/used just before shutting down: use either htop or system monitor (gnome applet) to see them; and check you dont have something plugged and activated on usb (like printer) or a cd/dvd into reader.

---

### Post by Quackers on 2011-08-31
I had this problem for a couple of weeks about a month or so ago, but it appears to have resolved itself.
If your pc is ever stuck you can hold down the Alt Gr and Prt Sc/SysRq keys and whilst they are held down press R E I S U B leaving a second or so between each key.
That will reboot any locked up system safely.

---

### Post by flipper T on 2011-08-31
dino, according to system monitor i have no apps running (cpu%). is there a log i can look at after i have had to hard shutdown that will show cause of the hang.

quackers, very informative, but looking to shutdown, not reboot.

---

### Post by cariboo on 2011-08-31
To shutdown without having to use the power switch, press Ctrl-Alt-F1 and type:

```
sudo shutdown -h now
```

If there is an app/service that isn't shutting down properly, you should get a notification.

---

### Post by MacUntu on 2011-08-31
I've seen this too, not always though. I think the last things I see on screen suggest some power manager related issue.

---

### Post by flipper T on 2011-08-31
cariboo, that worked !

no notifications.

the same command does not work from a terminal though. any ideas ?

> also, can i use sudo shutdown -h 60 for a timed shutdown from ctrl alt f1?

if so, can i return to my desktop gui in the meantime ? how ?

i like to fall to sleep listening to audiobooks & set the laptop to turn off after a hour :)

ignore, ctl alt f7. was being lazy

---

### Post by cariboo on 2011-08-31
> also, can i use sudo shutdown -h 60 for a timed shutdown from ctrl alt f1?

if so, can i return to my desktop gui in the meantime ? how ?

i like to fall to sleep listening to audiobooks & set the laptop to turn off after a hour

It should work, but the last time I tried, my system hung, I was having the same shutdown problem at the time.

**Eidt**: I did find [this]("http://www.ubuntugeek.com/easyshutdown-gui-to-turn-a-computer-off-after-specific-time.html")

---

### Post by flipper T on 2011-08-31
what puzzles me is that "sudo shutdown -h 60" acts differently in terminal(hangs)to console (works fine)

no notifications in either / sys monitor shows no cpu usage

---

### Post by whoop on 2011-08-31
I have had a comparable (not similar) issue: logout would freeze the desktop for me. changing from lightdm back to gdm works for the time being...

---

### Post by flipper T on 2011-09-02
gnome power manager was updated today & seems to have fixed problem.

fingers crossed.

---

