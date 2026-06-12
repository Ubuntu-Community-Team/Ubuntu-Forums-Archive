---
title: "[SOLVED] Gnome GUI as Root?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by mapes12 on 2008-11-11
I just created a tar ball of my system files using a HowTo off the Forums. I had to do this as /(root). I then wanted to move it to a partition on a second Internal HDD. I had to do this in Terminal using sudo (for root privileges) but the process involved the command line to mkdir (to make a directory to mount to), then mount the partition, then mv to move it. I did it, but my question is how can I access the Gnome GUI as root and just drag and drop what I wanted to move please? I've tried longing out from my usual User account and trying to login as "root" but it will not let me.

---

### Post by Joeb454 on 2008-11-11
Root login's are in general - a bad idea.

However if you wanted to use Nautilus with root provileges in order to do something like you mentioned but graphically, run ```
gksu nautilus
```

Naturally - be very aware of what can happen if you mess up in that case ;)

---

