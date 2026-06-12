---
title: "Where to disable &quot;Suspend to ram&quot; aka &quot;Suspen"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lprofil on 2011-09-30
Hello,

i am using the "GNOME Classic (no effects)" windowmanager in oneiric. Where do i find the option to turn off "suspend to ram" aka "Suspend"?
My machine suspend after 10min or so if i'm not busy with the mouse or keyboard.

Any suggestions?

Thanks in advance!

/lprofil

---

### Post by nidzo732 on 2011-09-30
Try looking for power settings or something like that in system>>preferences

---

### Post by sgage on 2011-09-30
> **nidzo732 said:**
> Try looking for power settings or something like that in system>>preferences

I'm running Gnome Shell, and I have set my system to never suspend when plugged in. Just recently, it seems to be going to sleep after a while regardless. 

I'd like to disable it, but the Power Manager doesn't seem to do it properly these days. Never had a problem before.

---

### Post by lprofil on 2011-09-30
Thanks nidzo732,

i go on Appliccations -> System Tools -> System Settings -> Power
but all i find there is 

Suspend when inactive for: Don't suspend <- which i just can change to different time from 5min to 1 hour

When power is critically low: Hiberate <- which i just can change to Shutdown

This doesn't do the trick.
And this is not a notebook i am useing but a Desktop PC.

Cheers lprofil

---

### Post by cariboo on 2011-09-30
Try the solution [here]("https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485/comments/15"), it worked for me, on my desktop system.

---

### Post by sgage on 2011-09-30
> **cariboo907 said:**
> Try the solution [here]("https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/860485/comments/15"), it worked for me, on my desktop system.

I've done the edit, we'll see what happens...

---

### Post by lprofil on 2011-10-01
Hello Sgage,

that fix seemsto do the trick.

Thanks for that.

/lprofil


edit: thanks to Cariboo ;)

---

### Post by sgage on 2011-10-01
> **lprofil said:**
> Hello Sgage,

that fix seemsto do the trick.

Thanks for that.

/lprofil

The tip came from Cariboo - It seems to work for me, too. Thanks!

---

