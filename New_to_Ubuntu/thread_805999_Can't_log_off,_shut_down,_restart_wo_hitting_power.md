---
title: "Can't log off, shut down, restart w/o hitting power button"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by IanGT on 2008-05-24
I apologize if this issue has already been brought up, I haven't found it in my searches.

A relatively recent development for me using Ubuntu 8.04 is that when I try to restart, shut down or even log off, everything closes and the screen then hangs with my wallpaper and nothing else displaying. I can get it to shut down from there by hitting the power button (the wallpaper disappears and it goes to the standard shutdown output) but obviously that's a pretty poor fix and I still can't restart or switch user accounts. I'm not sure where to start in tracking this issue down.

Thanks,

-Ian

---

### Post by tamoneya on 2008-05-24
not sure what is causing the problem exactly but a better way to shutdown a frozen linux computer is to hold down ALT-SysReq and type "reisub".  This will properly restart the computer so that you dont get filesystem errors and other nasty things.

---

### Post by alexandremrj on 2008-05-24
In the terminal try entering this command:

gnome-session-save --kill

It's supposed to force gnome to the shutdown screen with all the buttons for shutdown, reset, etc...

If it simply goes to the desktop or freezes try pressing Escape, does it return to normal?

---

### Post by IanGT on 2008-05-24
> **tamoneya said:**
> not sure what is causing the problem exactly but a better way to shutdown a frozen linux computer is to hold down ALT-SysReq and type "reisub". 

I was under the impression that frozen with no programs running, there wouldn't really be any file system activity going on to damage the system. However it's probably best to err on the safe side. Thanks.

alexandremrj >> I can open up that dialogue file, it's when I tell the computer to restart, shut down, etc, and after it closes all active applications, that it locks up. I don't have a problem actually shutting the computer down or starting it up, since I can always hit the power button (or use REISUB as mentioned above); it's getting the switching users, logging off, restarting etc functionality working that's bothering me.

---

### Post by alexandremrj on 2008-05-24
Oh, sorry

Try this thread:
[http://ph.ubuntuforums.com/showthread.php?t=772733&page=3](http://ph.ubuntuforums.com/showthread.php?t=772733&page=3)

---

### Post by IanGT on 2008-05-26
I've made all the changes recommended in that thread - removed/replaced the line portions in the login manager and changed my login screen from themed to standard - and I still get the hang at desktop after everything closes :(

---

### Post by arcarsenal on 2008-05-27
I'm having the same problem now... 

Only today has this become an issue and I didn't really change anything noteworthy. I hit the restart button and nothing happens. The only way to power down my computer is to hold the power button on the tower. Why is this happening?

---

### Post by IanGT on 2008-05-28
I don't know... if it helps anyone, my startup programs:

Bluetooth Manager
Check for new hardware drivers
Compiz-Fusion
Network Manager
Power Manager
Print Queue Applet
PulseAudio Session Management
Tracker
Tracker Applet
Update Notifier
User folders update
Visual Assistance
Volume Manager

I'm running on AMD Athalon X2 4400+ Brisbane on a VIA nForce 405 mobo. Other specs if they might be relevant. Hardware seemed to be a factor in the thread that was linked to...

---

### Post by Bigtime_Scrub on 2008-05-28
Try shutting down from terminal.

```
 shutdown -h now 
```

---

### Post by IanGT on 2008-05-28
That works. If that could be translated into the standard shutdown command working, that'd be perfect...

---

