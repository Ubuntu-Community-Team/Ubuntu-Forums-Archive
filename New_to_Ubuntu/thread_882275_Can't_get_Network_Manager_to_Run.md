---
title: "Can't get Network Manager to Run"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by duckfeet on 2008-08-06
Running Ubuntu 8.04...after a 3day struggle, was able to connect wireless on my Dell Inspiron laptop, USB Netgear WG111v3 ... a little slow, compared to wired, but I'll get to that later: my biggest beef is I can't get Network-Manager to run: the gnome applet, that is...I can run, say, alt-F2 on here, and plug in "nm-applet --sm-disable" and it will run fine, it comes up w/start-up, actually.

But on my laptop, it's there, in System - Preferences - Startup ... but doesn't run...

I know it's something really beginner, which is what I am, so I posted it here...I have been doing my homework, and searching, but can't seem to find anything past what I'm doing...

Appreciate any help, no matter how basic...

Thanx in Advance...

geff

---

### Post by anewguy on 2008-08-06
If you open a terminal window and just type in nm and press enter, what happens?

Also, have you tried wicd? (I think that's what it's called - it will remove network manager and install instead).

---

### Post by duckfeet on 2008-08-06
says: nm 'a.out'" No such file


> **anewguy said:**
> If you open a terminal window and just type in nm and press enter, what happens?

---

### Post by anewguy on 2008-08-06
I guess that definitely wasn't what I thought (I looked at the man page - I was way off!).  Sorry about that!  I'm going to have to do some thinking to try and remember what it was - I remember when I was first starting out someone had me do it via the command line, but I don't remember how right now.

---

### Post by anewguy on 2008-08-06
In a terminal window, what happens if you type nm-applet and press <enter>?

EDIT:  A DUMB question, so bear with me:  did you install network-manager and network-manager-gnome packages via synaptic?

---

### Post by duckfeet on 2008-08-06
Yep, what puzzles me, i--like other rookies, it took a lot of loading, and reloading before the wireless Netgear wg111v3 actually worked, but for some reason, at the same time, the little network-manager applet, that always comes up on *this*, my main computer, just doesn't come up on my laptop, and they both have the same ubuntu version loaded: I even plugged in an ethernet cable, thinking maybe it had something to do w/wired connection, but that didn't help, and it does seem to be installed...

Well, I'll keep searching, and if you think of something, please post...I do appreciate the help, and thank you....

---

### Post by duckfeet on 2008-08-06
> **anewguy said:**
> In a terminal window, what happens if you type nm-applet and press <enter>?

EDIT:  A DUMB question, so bear with me:  did you install network-manager and network-manager-gnome packages via synaptic?

Actually, when I type in 'nm-applet', *nothing* happens...my cursor just sort of bounces away, like it's searching, but not finding, or something, and yes, even tho they were already installed, I reinstalled them "just in case" and even rebooted, so they are in my system...just not hooking up...

---

### Post by anewguy on 2008-08-06
I just started looking through the results of a Yahoo! search with ubuntu network manager not starting, and found this in one of the replies.  It is old, but it can't hurt to try!

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/


BTW - do you get any error messages?  If you do dmesg and scroll through it do you see anything regarding network manager?  You may want to try the nm-applet via a terminal window right before doing this, as then any errors should be at the end of the dmesg output.

Meanwhile, I'll keep looking!

---

### Post by duckfeet on 2008-08-06
Typed sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/ and it came back with "If you really want to create an icon cache here, use --ignore-theme-index."

Thanks again, I'll keep looking too, I think it's probably just some link I need to make: everything is installed alright, it's just not coming up, and it's a handy applet, and also, *then* I could concentrate on why my wireless setup on linux, is so much slower, than it is on any other machine, using same router, same USB device...we'll see, I'll be back in a few minutes, off to search...

> **anewguy said:**
> I just started looking through the results of a Yahoo! search with ubuntu network manager not starting, and found this in one of the replies.  It is old, but it can't hurt to try!

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/


BTW - do you get any error messages?  If you do dmesg and scroll through it do you see anything regarding network manager?  You may want to try the nm-applet via a terminal window right before doing this, as then any errors should be at the end of the dmesg output.

Meanwhile, I'll keep looking!

---

### Post by drs305 on 2008-08-06
After you try to run nm-applet, do you know for sure it isn't running? You can use this command to check. Does it show the results posted in the second window?
```
ps aux |grep NetworkManager
```
Edited, but generally:
```
root  /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root  /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkMana
```

**If it displays something similar to the above, do you have the Netwok Monitor icon enabled in your panel (Rt Click, Add, Network Monitor -- or -- Notification Area).**

---

### Post by duckfeet on 2008-08-06
Yes, generally, shows the root, then the NetworkManager, then the NetworkManagerDispatcher...so yeah...but no icon....and yes, I can get the Network Monitor...but I have a totally different applet, the NetworkManager, which gnome says is in my system, has different properties and such, and doesn't come up...the command for the one that *does* come up, is "Network-admin"


> **drs305 said:**
> After you try to run nm-applet, do you know for sure it isn't running? You can use this command to check. Does it show the results posted in the second window?
```
ps aux |grep NetworkManager
```
Edited, but generally:
```
root  /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root  /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkMana
```

If it displays something similar to the above, do you have the Netwok Monitor icon enabled in your panel (Rt Click, Add, Network Monitor -- or -- Notification Area).

---

