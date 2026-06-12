---
title: "password not asked when wake up from suspend"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by whizvast on 2008-07-11
hi, i just installed xubuntu and everything is great!!...
except the fact that the password are NOT being asked when
it wakes up from sleep. how do i fix that? i can't find an option
anywhere in settings. thx--

---

### Post by cprofitt on 2008-07-11
I do not use Xbuntu, but in Ubuntu you have to select the option to "lock screen when screen saver is active".

I hope that helps in Xbuntu.

---

### Post by whizvast on 2008-07-17
hello~
i enabled that option, but it's not working...
any other idea? or where to look at?

---

### Post by whizvast on 2008-07-17
hello,

i enabled that option, but it doesn't work.
any other idea? or where to look at?
thx-

---

### Post by jimmy the saint on 2008-07-20
read post #7 here: [http://ubuntuforums.org/showthread.php?p=5424711#post5424711](http://ubuntuforums.org/showthread.php?p=5424711#post5424711)
the problem is that you need to add a program to the autostart menu.  details there.

---

### Post by dizee on 2008-07-20
even with gnome-screensaver enabled, the screen does not lock for me on hibernate in xubuntu.

the way i got around it was by writing a script to lock the screen and then hibernate, i assume it would work just as well for suspend but suspend doesn't work on my laptop.

make sure you have added "gnome-screensaver" to your autostarted applications. log out and log back in to test it (you can add a screen lock applet to the panel to make sure it is running).

first create a text file in your home folder called "locksuspend.sh".
put this in it (copy & paste if you like):
```

#!/bin/bash
gnome-screensaver-command --lock ;
pmi action suspend &
```
save the file. then open a terminal and type:
```
chmod +x locksuspend.sh
```
this makes the file executable. test if it works from the terminal.
```
./locksuspend.sh
```

if all goes well the computer should lock the screen just before suspending and on resume will show your screenlock dialog.

if that works, you can run it when you need to suspend your computer.

---

### Post by Chris H on 2008-07-20
Have a look in /etc/default/acpi-support and edit this line

> # Comment this out to disable screen locking on resume
LOCK_SCREEN=true


Should give you what you need.

---

### Post by dizee on 2008-07-20
> **Chris H said:**
> Have a look in /etc/default/acpi-support and edit this line



Should give you what you need.
yes, this might work, but in my xubuntu system that line is already there, so i'm pretty sure it's a bug of some sort.

---

### Post by jimmy the saint on 2008-07-20
it is a bug.  its apparently been fixed on newer cd images.  you don't need to modify any scripts or anything else.  Once you have the screensaver app running the settings passed through gnome power manager should work.  try installing gconf-editor and running it via the terminal.  under apps>gnome power managre> lock >  make sure that it is set to use the screenaver settings and that the boxes for suspend and hibernat are UNCHECKED.

---

