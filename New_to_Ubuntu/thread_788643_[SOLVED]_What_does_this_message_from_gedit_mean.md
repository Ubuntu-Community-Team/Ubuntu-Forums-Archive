---
title: "[SOLVED] What does this message from gedit mean?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by anewguy on 2008-05-09
I get the following error message a lot, specifically if I "sudo gedit" or I "su" and then "gedit".  The edit itself actually runs okay - it just doesn't show in the following.  Am I doing something wrong?

Thanks!  :):)

dave@dave-desktop:~$ cd /etc/udev/rules.d
dave@dave-desktop:/etc/udev/rules.d$ su
Password: 
root@dave-desktop:/etc/udev/rules.d# gedit 41-cvs-permissions.rules

(gedit:20911): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

== the edit actually runs here, then when I exit I return below ==

root@dave-desktop:/etc/udev/rules.d#

---

### Post by macaholic on 2008-05-09
Just curious, does the same thinkg happen when you run it as gksu rather than sudo?

---

### Post by spiderbatdad on 2008-05-09
Try using sudo -s (for root as user) or sudo -i
instead of su. Or make sure you are in the sudoers file, and sub directory filename.

---

### Post by Xiong Chiamiov on 2008-05-09
> **macaholic said:**
> Just curious, does the same thinkg happen when you run it as gksu rather than sudo?
That is a good point, you should always use gksudo (or kdesudo) instead of sudo for GUI work, or else it can do some screwy things sometimes.

---

### Post by anewguy on 2008-05-10
Never have had a problem with gedit myself, and I've edited a zillion things.  At any rate, the problem I think has something to do with the superuser.  If I just gksu gedit xxxxxx in my regular logon, I get no messages.  Nor do I if I just gedit xxxxxx -> I just can't save the file when it's owned by root.

However, as soon as I "su" and enter my password, THEN gksu gedit or just plain gedit, I get the message.  I'm guessing it has something to do with the superuser and how it is configured somehow for "X".  Just a guess.

---

