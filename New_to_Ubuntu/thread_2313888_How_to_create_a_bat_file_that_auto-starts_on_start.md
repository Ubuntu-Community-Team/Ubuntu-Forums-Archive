---
title: "How to create a bat file that auto-starts on startup"
date: 2016-02-16
forum: New to Ubuntu
---

### Post by Clifford_Sarokoff on 2016-02-16
In order to calibrate the colors on my monitor I do this:
Open a terminal
enter my correction: xgamma -ggamma 0.9 -bgamma -0.75
How do I create a file (batch file?) to automate this process?

---

### Post by TheFu on 2016-02-16
Steps:
[LIST=1]
[*]Open an editor - any editor you like
[*]Put those commands into it.  Something like:
```
#!/bin/bash
xgamma -ggamma 0.9 -bgamma -0.75
```
The first line tells it which interpreter to use.
[*]Save the file somewhere you can write.  I would put it into ~/bin/ <-- the bin directory under my $HOME. Might have to create this directory if it doesn't exist. This is an unwritten "standard way" of doing stuff like this.
[*]Change the permissions so the file is "executable" - I'd do that with **chmod +x /full/path/to/file**, but most file managers have a "permissions" capability.
[*]Next is the hardest part - for the GUI you run, lookup where the "autostart" folder is and move that file into it (or create either a symbolic link or hardlink from the file into that directory).
[*]Logout to test this
[*]Login to see it work.
[/LIST]
bam, should have worked.  [https://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](https://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login) has more details for the primary Ubuntu GUI (which I do not use).

There are many other ways to run programs at "startup", but you don't really want that - it is important to wait until login to run this, since X/Windows may not be running previously and well there are 50 other reasons NOT to do it elsewhere.  Linux is a multi-user OS and logins don't just happen on the machine directly. Remote connections are also used by many people, plus a running system may not have any end-users logged in for days, weeks, months .... 

BTW, we call "bat files" "shell scripts" in the Unix world. There are 20+ different scripting languages commonly used for this stuff, but bash is fine for something this tiny and for most things like this.  "How to make a script that runs a command after X11 login" is what I would have asked.  Not really THAT different, but technically, extremely different. ;)

Anyway, hope this helps.  If the script doesn't seem to work, change the first line to **#/bin/bash -x **to see what isn't working.

---

### Post by Clifford_Sarokoff on 2016-02-16
Many thanks!

---

### Post by Clifford_Sarokoff on 2016-02-27
> **TheFu said:**
> Steps:
[LIST=1]
[*]Open an editor - any editor you like
[*]Put those commands into it.  Something like:
```
#!/bin/bash
xgamma -ggamma 0.9 -bgamma -0.75
```
The first line tells it which interpreter to use.
[*]Save the file somewhere you can write.  I would put it into ~/bin/ <-- the bin directory under my $HOME. Might have to create this directory if it doesn't exist. This is an unwritten "standard way" of doing stuff like this.
[*]Change the permissions so the file is "executable" - I'd do that with **chmod +x /full/path/to/file**, but most file managers have a "permissions" capability.
[*]Next is the hardest part - for the GUI you run, lookup where the "autostart" folder is and move that file into it (or create either a symbolic link or hardlink from the file into that directory).
[*]Logout to test this
[*]Login to see it work.
[/LIST]
bam, should have worked.  [https://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](https://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login) has more details for the primary Ubuntu GUI (which I do not use).

There are many other ways to run programs at "startup", but you don't really want that - it is important to wait until login to run this, since X/Windows may not be running previously and well there are 50 other reasons NOT to do it elsewhere.  Linux is a multi-user OS and logins don't just happen on the machine directly. Remote connections are also used by many people, plus a running system may not have any end-users logged in for days, weeks, months .... 

BTW, we call "bat files" "shell scripts" in the Unix world. There are 20+ different scripting languages commonly used for this stuff, but bash is fine for something this tiny and for most things like this.  "How to make a script that runs a command after X11 login" is what I would have asked.  Not really THAT different, but technically, extremely different. ;)

Anyway, hope this helps.  If the script doesn't seem to work, change the first line to **#/bin/bash -x **to see what isn't working.

The suggestion work but intermittently.  I found a solution by trial and error.  I added the second line to read "sleep 12"  and it seems to work well.  Again thanks for the help.  I'm just passing along my trial and error solution on the hope that it will help other members.

---

### Post by Clifford_Sarokoff on 2016-02-28
I've noticed that when the screen display turns off on the notebook and I move the mouse to restart the screen the color setting reverts back (to before the shell script).  Is there a suggestion (beside ***not*** letting the display sleep) to solve this annoyance?

---

### Post by coldraven on 2016-02-29
> **Clifford_Sarokoff said:**
> I've noticed that when the screen display turns off on the notebook and I move the mouse to restart the screen the color setting reverts back (to before the shell script).  Is there a suggestion (beside ***not*** letting the display sleep) to solve this annoyance?
I don't know but the man page for xgamma says:
>  Note that the xgamma utility is obsolete and deficient, xrandr should be used with drivers that support the XRandr extension.

and looking at the man page for xrandr
```
man xrandr
```
> --gamma red:green:blue
              Set  the  specified floating point values as gamma correction on the crtc currently attached to this output. Note that you
              cannot get two different values for cloned outputs (i.e.: which share the same crtc)  and  that  switching  an  output  to
              another crtc doesn't change the crtc gamma corrections at all.


So to try it you need to change your script to look like the one in the reply here.  If you only have one screen I'm not sure if you need to specify the output.
[http://www.linuxquestions.org/questions/linux-general-1/setting-gamma-correction-4175546328/](http://www.linuxquestions.org/questions/linux-general-1/setting-gamma-correction-4175546328/)

---

### Post by Clifford_Sarokoff on 2016-02-29
> **coldraven said:**
> I don't know but the man page for xgamma says:


and looking at the man page for xrandr
```
man xrandr
```

So to try it you need to change your script to look like the one in the reply here.  If you only have one screen I'm not sure if you need to specify the output.
[http://www.linuxquestions.org/questions/linux-general-1/setting-gamma-correction-4175546328/](http://www.linuxquestions.org/questions/linux-general-1/setting-gamma-correction-4175546328/)


Thanks for pointing me in a possible solution. 
CliffordS

---

