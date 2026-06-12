---
title: "Great Ubuntu app's anno 2008"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by KS1987 on 2008-08-15
I am sorta new to this os, I've tried a few Linux distributions, for a verra limited time. Now I've decided to go from virtualization to using it on my desktop. I was looking for some app's that really make Ubuntu shine. A Google search brings me to lists from 2006 and 2007, with things like automatix that looks like dead to me. So I was wondering what great app's are there for Ubuntu that make this OS shine.

One thing I got already is my new browser Ephiphany, which I really like because it's so fast and clear. The lack of mouse gestures is a shame, although I have yet to look for additional resources. I tried Beagle too, but it said that already a service like this was running, so maybe in the latest Ubuntu release there is a similar program running, I don't know.

And one last thing, I got to up the brightness of my computer with "xgamma -gamma 1.750", but it resets to default after time. How do I make it stick. These are probally a few newbie questions, but I like to learn. Thanks in advance and I am looking forward to being part of this community!

---

### Post by Perfect Storm on 2008-08-15
Did you installed the extensions of epiphany to get geasture?

---

### Post by LowSky on 2008-08-15
Opera is availible with mouse gestures.

Also try Compiz-Fusion.. its some very fun stuff

and for most basic support for mp3s, java, and flash

look for ubuntu-resricted-extras

---

### Post by Martje_001 on 2008-08-15
> **KS1987 said:**
> And one last thing, I got to up the brightness of my computer with "xgamma -gamma 1.750", but it resets to default after time. How do I make it stick. These are probally a few newbie questions, but I like to learn. Thanks in advance and I am looking forward to being part of this community!
What do you mean with 'after time'. After a reboot or logout/login?

Else, you could do this:
```
#!/bin/bash
while true; do
 xgamma -gamma 1.750
 sleep 600
done
```
and save it as a script and then add it to your 'session' list.

---

### Post by Paqman on 2008-08-15
> **KS1987 said:**
> I tried Beagle too, but it said that already a service like this was running, so maybe in the latest Ubuntu release there is a similar program running, I don't know.


Indeed there is. Ubuntu comes with an app called Tracker, which isn't (IMO) as good as Beagle. Just remove Tracker and install Beagle in it's place if you want.

As for good apps, some of my favourites are:
Compiz-Fusion (installed by default).
Compiz Config Settings Manager, unlocks all the features of Compiz.
Avant Window Navigator (a dock, needs Compiz to work properly)
Amarok, a really good music player.
Battle for Wesnoth, a good single or multiplayer hex-based fantasy wargame.
Simple Backup, does what it says.
Grsync, also good for backups.
Startup Manager, edits GRUB, switches login screens.
NTFS Config, good for newbies wanting to mount their NTFS partitions easily.
VLC, a multimedia player that just plays everything.
Abiword, a much faster word processor than OO.o Writer

---

### Post by KS1987 on 2008-08-15
> **Artificial Intelligence said:**
> Did you installed the extensions of epiphany to get geasture?
I did so now, cheers for the info m8. Although the middle mouse button is a bit more annoying than the usual right one.

> **LowSky said:**
> Opera is availible with mouse gestures.

Also try Compiz-Fusion.. its some very fun stuff

and for most basic support for mp3s, java, and flash

look for ubuntu-resricted-extras
I love Opera, but it's also a resource hog. So that's why I am looking for something less resource heavy. Compiz is nice enough and the rest are stuff I'll look into later. Cheers.

> **Martje_001 said:**
> What do you mean with 'after time'. After a reboot or logout/login?

Else, you could do this:
```
#!/bin/bash
while true; do
 xgamma -gamma 1.750
 sleep 600
done
```
and save it as a script and then add it to your 'session' list.
I did this one and have a problem. When I closed down my session,  my PC didn't want to shutdown. I just got a blank screen where I could type. I then did a forced shutdown. When booting I got the same screen after an error message of "xgamma failed cannot open display". What to do, I know I can go in restore, but what to do from there. Any input is welcome here.

EDIT: I solved it by deleting the file from the command line. I now altered the xorg config file, by adding "Gamma 1.750" to the Monitor section. Hope this helps.

> **Paqman said:**
> Indeed there is. Ubuntu comes with an app called Tracker, which isn't (IMO) as good as Beagle. Just remove Tracker and install Beagle in it's place if you want.

As for good apps, some of my favourites are:
Compiz-Fusion (installed by default).
Compiz Config Settings Manager, unlocks all the features of Compiz.
Avant Window Navigator (a dock, needs Compiz to work properly)
Amarok, a really good music player.
Battle for Wesnoth, a good single or multiplayer hex-based fantasy wargame.
Simple Backup, does what it says.
Grsync, also good for backups.
Startup Manager, edits GRUB, switches login screens.
NTFS Config, good for newbies wanting to mount their NTFS partitions easily.
VLC, a multimedia player that just plays everything.
Abiword, a much faster word processor than OO.o Writer
What a handy list, much appreciated m8!!!

---

### Post by Martje_001 on 2008-08-16
Use Rhythmbox instead of Amarok. It uses much less resources (since it does not use KDE-libraries).

---

