---
title: "Ubuntu 12.04 boot up message"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by steve36plenty on 2014-01-05
Hi to everyone,

Happy new year to you all, I am using Ubuntu 12.04 LTS and when I start up my computer sometimes it dont go to the normal login but it goes to a black screen with my PC name at the top and it is asking me to login by using the command line only??? can this be fixed? please help.......

thank you Steve Plenty:confused:

---

### Post by egeezer on 2014-01-05
At the login prompt, enter your name; it will ask for your password, enter that as well.
Then you are fully running your system, but only at the command-line level.
You might first try:
```
startx
```
If that doesn't give you your full desktop, try:
```
sudo jockey-text --list
```
That will show you what Nvidia driver you are running.  If that is your problem, this thread deals with what might be the same thing (though that one happens every time, not intermittently).
[http://ubuntuforums.org/showthread.php?t=2193029](http://ubuntuforums.org/showthread.php?t=2193029)
The thread is pretty long, but if your problem really is the same, the solution was this:
```
sudo jockey-text --enable (whichever driver you need)
```

---

### Post by steve36plenty on 2014-01-06
Hello egeezer,

Thank you for you help ill try it the next time it happens

steve36plenty

---

### Post by MrMichaelHill on 2014-01-06
I'll subscribe to this, please steve36plenty let us know how you get on, After some xorg or nvidia updates my system has failed to boot, displaying that blank login terminal you've described above! I've usually given in to easily and installed a fresh OS but it would be nice to be prepared if it happens in the future.

Cheers!

---

### Post by egeezer on 2014-01-06
@MrMichaelHill: there's really no need to install a fresh OS.  If you use the jockey-text command I gave above, you'll have access to the full array of available Nvidia drivers (be patient - it takes as long to load as the GUI front-end, Additional Drivers, does).  You can enable one that has worked well for you in the past or disable one that is giving you trouble.

---

### Post by MrMichaelHill on 2014-01-06
> **egeezer said:**
> @MrMichaelHill: there's really no need to install a fresh OS.  If you use the jockey-text command I gave above, you'll have access to the full array of available Nvidia drivers (be patient - it takes as long to load as the GUI front-end, Additional Drivers, does).  You can enable one that has worked well for you in the past or disable one that is giving you trouble.

Cheers buddy! :)

I still try not to look at my monitor as the PC boots because the "login" black screen always briefly appears and I can't bear to see if it will stay!

A few bad experiences haha! :P

---

