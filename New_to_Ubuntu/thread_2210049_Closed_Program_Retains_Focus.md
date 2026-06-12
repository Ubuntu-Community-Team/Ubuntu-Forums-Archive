---
title: "Closed Program Retains Focus"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-03-08
Hi Guys,

I'm running Ubuntu 12.04 and noticed this annoying behavior about a month ago.
I was wondering if anyone knows what I can do to solve the problem.

If, for example, I launch the terminal the name of the active program appears in the upper left-hand corner of the screen.  In the case of the terminal it shows the name of a script I have that runs in the terminal. That is fine.  This could be any program I am just using the terminal as an example.

[IMG]http://screencloud.net/img/screenshots/d17b7c9a3a739be13dcf483b018c12ca.png[/IMG]
*[COLOR=#0000ff]The terminal is the active program and the name Google Tasks List appears in the corner. Not a problem.[/COLOR]*

The annoying thing is that if I close the terminal (I usually click the x in the corner of the terminal.)
the terminal, in this case called Google Tasks List, remains active despite the terminal being closed.

[IMG]http://screencloud.net/img/screenshots/ada871204be399c904db9f7278e1914f.png[/IMG]
[I][COLOR=#0000ff]Here you can see my conky below where the terminal had been open.
Yet, in the corner, Google Tasks List is still shown as active.[/COLOR][/I]

The irritating thing is that I seem to have to click on the desktop to release the focus from the terminal (which has taken the name Google tasks list and is no longer running).

Does anyone know what I need to do in order to have the focus either returned to the desktop or if there is more than one program open moved to the next program in line when I close an active program?  That is, instead of keeping the closed program as the active program and being required to click the desktop.

---

### Post by GrouchyGaijin on 2014-03-12
bump

---

### Post by grumblebum2 on 2014-03-12
Are you running conky on the desktop? Edit...just reread your post and see you are.
 Had a similar problem when running conky and the solution was to give conky "no focus" using ccsm.....see pic.
ccsm > window management > window rules
Enable the plugin and add the following to the "No focus" box.
```
class=Conky
```

Reload your conky....
```
killall -SIGUSR1 conky
```

---

### Post by GrouchyGaijin on 2014-03-13
> **grumblebum2 said:**
> Are you running conky on the desktop? Edit...just reread your post and see you are.
 Had a similar problem when running conky and the solution was to give conky "no focus" using ccsm.....see pic.
ccsm > window management > window rules
Enable the plugin and add the following to the "No focus" box.
```
class=Conky
```

Reload your conky....
```
killall -SIGUSR1 conky
```
Thank you for the reply.
I enabled the ccsm and set conky to no focus as you did in your screen shot.
Do I need to add anything to the conkyrc?
I wonder if that is really the problem though, because in my case I can close just about any program and it will still retain focus.

For example, if I run the terminal and then click the x in the corner of the terminal the terminal window will close.  Yet in the upper left-hand corner of my screen where the active program is listed I'll still see Terminal until I click on the desktop.

We'll see though, I followed your suggestion.  I've been wrong before about what I thought would or would not work. ;)

---

### Post by GrouchyGaijin on 2014-03-13
That doesn't seem to have helped actually.
I restarted my computer and have not started Conky yet.

When I launch the ccsm I get the screen shot below:
[IMG]http://screencloud.net/img/screenshots/cbcc01bd87c38d1ce2196d88721934ee.png[/IMG]

If I close the ccsm I still show it as the active program.
[IMG]http://screencloud.net/img/screenshots/204f5cc4b2bdc66075274fc9425bb1f6.png[/IMG]

---

### Post by grumblebum2 on 2014-03-13
Been a while since I used 12.04...using 13.10 at the moment and see exactly what you describe when I run conky without the ccsm "no focus" setting.
If I don't run conky problem doesn't exist.
Also used to have problems with shortcut keys because the focus seemed to be in some state of limbo...the closed app wasn't focused but neither was the desktop.
I usually use **own_window_type normal** in my conkyrc but you could try **own_window_type override**.
Override windows ignore window manager hints, so if you are already using **override** try **normal**.

---

### Post by GrouchyGaijin on 2014-03-13
OK I'll try playing with the window settings - they were set to own_window no actually

---

### Post by GrouchyGaijin on 2014-03-13
I still have the same problem :-(

---

### Post by grumblebum2 on 2014-03-13
> **GrouchyGaijin said:**
> I still have the same problem :-(
Sorry about that. Can't be of much more help if you have the problem even when not running conky.
Only other thing I would suggest would be to test a new user account to see if the issue exists there.

---

### Post by grumblebum2 on 2014-03-26
See this thread and check your config to see if you have changed **own_window_class** .
[http://ubuntuforums.org/showthread.php?t=2213321&p=12968394#post12968394](http://ubuntuforums.org/showthread.php?t=2213321&p=12968394#post12968394)

---

