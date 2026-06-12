---
title: "Auto Shutdown tool"
date: 2005-05-10
forum: Programming Talk
---

### Post by oldblue on 2005-05-10
Not sure where to mention this, but I thought here would be a good place, since most of you are programmers (I assume)  :) .  I can't seem to find an auto-shutdown tool for linux.  The idea would be an applet to monitor cpu load, or network traffic, or whatever else, and then shutdown when the levels drop below a particular number for X amount of time.  I thought it would be useful when downloading large files at night or when compiling a large program when going out, since most programs don't include this as an option.

Anyways, I was hoping maybe someone here knows of such a program.  I think it would be amazingly useful, too.  And yes, I know I'm going to get the usual comments that I should learn how to program and do it myself.  In fact, when I have the time (which won't be for another couple months) I'll sit down and learn python and give it a shot.  But I thought I'd throw the idea out there for anyone who has a similar itch and the means to do something about it (or knows of such a program).  ;-) 

Thanks

---

### Post by nemin on 2005-05-10
[QUOTE=oldblue]Not sure where to mention this, but I thought here would be a good place, since most of you are programmers (I assume)  :) .  I can't seem to find an auto-shutdown tool for linux.  The idea would be an applet to monitor cpu load, or network traffic, or whatever else, and then shutdown when the levels drop below a particular number for X amount of time.  I thought it would be useful when downloading large files at night or when compiling a large program when going out, since most programs don't include this as an option.
[/QUOTE]
I don't know really much about shell scripting, but something like:
```
wget <the file you want> && poweroff
```
will shutdown your computer after the file is downloaded, won't it? You could use this tric for all programs. Not exactly what you're looking for, but I hope you'll find it usefull :)

---

### Post by nocturn on 2005-05-10
[QUOTE=nemin]I don't know really much about shell scripting, but something like:
```
wget <the file you want> && poweroff
```
will shutdown your computer after the file is downloaded, won't it? You could use this tric for all programs. Not exactly what you're looking for, but I hope you'll find it usefull :)[/QUOTE]

This will only work when run as root AFAIK...
You could use sudo, but it prompts for a password.  Or just put a line in sudoers allowing /sbin/shutdown without password.

---

### Post by nemin on 2005-05-10
[QUOTE=nocturn]This will only work when run as root AFAIK...
You could use sudo, but it prompts for a password.  Or just put a line in sudoers allowing /sbin/shutdown without password.[/QUOTE]
Hmm you're right, forgot that :p But what about:
```
wget <the file you want> && echo <your password here> | sudo -S poweroff
```

---

### Post by LordHunter317 on 2005-05-10
That's not a good way to do things as it risks password compromise.  Plus, IIRC, sudo will only read the password off a terminal, so doing that will fail anyway.  The correct thing to do is enable the user to run /sbin/shutdown without a password in /etc/sudoers:```
user ALL = NOPASSWD: /sbin/shutdown
``` and then make your script like so:```
wget [file] && sudo /sbin/shutdown -h now
```

---

### Post by oldblue on 2005-05-10
Thanks for the reply's.  I was hoping someone knew of a GUI app for something like this, but hey, those are overrated anyways right? :)  I'll probably try my hand at some bash scripts to run in the background that check info in /proc.  That way if I'm converting a whole bunch of CD's to mp3 (and I have a lot), I can have it shutdown when done.  Or if I'm downloading from newsgroups with Klibido I can have it shutdown, etc, etc.   
Thanks for the tips, and thanks for sudo/shutdown tip LordSlayer.  That one will definately come in handy.

---

