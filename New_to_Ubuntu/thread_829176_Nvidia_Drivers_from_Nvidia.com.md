---
title: "Nvidia Drivers from Nvidia.com"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by FTBPrimeEvil on 2008-06-14
My video is very choppy (8700GT) Laptop vid card, so i down loaded new vid drivers from Nvidia "NVIDIA-Linux-x86-173.14.05-pkg1.run" I opened terminal and used the "sh" command to install this and get an error that X-server must be shut down to install this. When i shut down Gnone it just hangs. What is the best way to install this? Could some one point me in the right direction?

Sincerely,

A Six Day Old Linux NOOB!

---

### Post by dudafmendes on 2008-06-14
I installed this driver by opening a new session and killing gdm

sudo killall gdm

bests d.

---

### Post by FTBPrimeEvil on 2008-06-14
that command takes me to black screen with 4 lines, the last line saying "Running local boot scripts (/etc/rc.local) [OK}"
Then after that is a blinking cursor, i let it set there like that for 10min.
Any Suggestions?

Thanks.

---

### Post by aktiwers on 2008-06-14
This guide I made should work:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

Just remember to rename/change the name in the commands with the driver filename(NVIDIA-Linux-x..blabla.run) to your own driver name.

---

### Post by FTBPrimeEvil on 2008-06-14
when i run this code sudo /etc/init.d/gdm stop, my puter locks up at this line.
"Running local boot scripts (/etc/rc.local) [OK}"
When i run code cat rc.local, this is what it says.
#!/bin/sh -e
#
#rc.local
#this script is excuted a the end of each multiuser runlevel.
#make sure that the script will "exit 0" on success or any other
#value on error
#In order to enable or disable this script just change the
#execution bits.
#by default this script does nothing.

exit 0

what is an execution bit and how to change, since this file is locking up my computer what do i do with it.

Thanks everyone!

---

### Post by aktiwers on 2008-06-14
Does it also lockup when you run it after you hit CTRL+ALT+F1?
Else try ```
sudo killall gdm
```

In that step of my guide instead of the /etc/init.d/gdm stop

---

### Post by FTBPrimeEvil on 2008-06-14
it still hangs on that rc.local file.
:(

---

### Post by FTBPrimeEvil on 2008-06-14
Ok, got it installed. Thanks everyone.

Had to Hit CTRL+Alt F1, then stop gdm, rename nvidia file name to something short, installed fine.

Thanks.
:guitar:

---

### Post by redburton on 2008-06-14
good evening,  this is my first post... it seems I am having the same problem.  I went through everything above and am still hanging at the "Running local boot scripts (/etc/rc.local)"

Not sure if this is important but the five lines (including the above) blinks four times and then hangs there  Any help would be very much appreciated.

---

### Post by dudafmendes on 2008-06-14
I forgot to mention the ctrl+alt+f1.. sorry!

1. ctrl+alt+f1
2. login
3. sudo killall gdm
4. run the setup, might work.

---

