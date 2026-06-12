---
title: "HOWTO: numlock activated at startup in login screen"
date: 2005-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by PaDV on 2005-02-24
I find it very annoying that the numlock is not activated at startup in the login screen GDM, especially when using a password that contains numbers. I tried the How To: "Setting up numlock on start up" but noticed that the numlock is activated just after logging in, at the splash screen of Gnome. The following solution solves this problem:

Make sure that the warty universe repository is enabled.

Execute the following commands in a terminal:
1. sudo apt-get install numlockx
2. sudo gedit /etc/X11/gdm/Init/Default
3. Add the following lines at the end before the line "exit 0":
```

if [ -x /usr/bin/X11/numlockx ]; then
   /usr/bin/X11/numlockx on
fi

```4. Put off your numlock and restart X by pressing Ctrl+Alt+Backspace

The numlock should be activated now and every time you reboot!!!

---

### Post by p!=f on 2005-02-24
[http://www.ubuntuforums.org/showthread.php?t=14930](http://www.ubuntuforums.org/showthread.php?t=14930)

---

### Post by macewan on 2005-02-24
nice

---

### Post by ebash on 2005-02-26
Under hoary the path to numlockx seems to have changed to /usr/bin/numlockx.
In such case the correct entries to add to the file /etc/X11/gdm/Init/Default should be :
```
# Set Num Lock
if [ -x /usr/bin/numlockx ]; then
   /usr/bin/numlockx on
fi
```

---

### Post by madtom on 2007-02-24
thanks a lot, exactly what i was looking for :)

---

### Post by setotitan on 2008-03-21
great how to really did the trick! just wanted to put a side note here, if you're using gutsy step 2 is actually:

sudo gedit /etc/gdm/Init/Default

i was beating my head against the wall trying to figure out why i couldn't get it ;)

---

### Post by hazza96 on 2008-03-21
I have not tried doing these suggestions but I found this thread because my num lock **light** is on after boot up but the num lock isn't. I hit the numpad and no numbers are entered.

I have to hit the num lock key three times for it to actually be on.

I will try the suggestion and see what happens.

---

