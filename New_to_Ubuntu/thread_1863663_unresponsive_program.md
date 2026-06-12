---
title: "unresponsive program"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by d_stroyer on 2011-10-18
ok i just made the switch from windows to linux. i have a program that froze up..is there a way to force it to close (i.e. ctrl+alt+del in windows)? thanks.

---

### Post by Quackers on 2011-10-18
Which program is stuck?
Open system monitor (if you haven't already).

---

### Post by sepo on 2011-10-18
This is the way I do.....
*) Switch to (the first) console with **Ctrl**-**Alt**-[B]F1
[/B]*) login with your user and password :)
*) if you know the name of the program stuck you can try to use
```
pkill <programname>
```example (I'll kill vlc, the video player):
```
pkill vlc
```*) if you don't know exactly the name of the program you have to find it in the active processes; I usually do
```
ps -ef|grep <knownpartoftheprogramname>
```example (wanna kill firefox):
```
ps -ef|grep firef
```In the last column you have the program name (with all its parameters, that in this case are useless). Now you can pkill it.
*) Switch again to your desktop with **Ctrl**-**Alt**-[B]F7

[/B]One note: if the program is HEAVILY locked you I prefer to use kill, instead of pkill. Kill takes the PID (program ID) instead of its name. If you use the ps command as shown above, the second column shown is the PID. 
So you can do:
```
kill -15 <PID>
```or if this will not work (and as last chance!):
```
kill -9 <PID>
```That's all man
:)

---

### Post by d_stroyer on 2011-10-18
ill check it out. i'm new to linux so i'm still figuring it all out. and dvdstyler is the program thats not responding.

---

### Post by d_stroyer on 2011-10-18
ok i will try that if it happens again. i ended up just restarting my computer.now a follow up n00b question...how do i get back to my desktop from the console?

---

### Post by Carborundum on 2011-10-18
> **d_stroyer said:**
> ok i will try that if it happens again. i ended up just restarting my computer.now a follow up n00b question...how do i get back to my desktop from the console?
ctrl+alt+f7.

---

### Post by 3rdalbum on 2011-10-18
For GUI programs, it might be easier to go to the terminal and type:

```
xkill
```

and then click on the window of the program you want to kill.

To cancel Xkill, press Escape.

---

### Post by d_stroyer on 2011-10-28
ok thanks. i will try these next time.

---

