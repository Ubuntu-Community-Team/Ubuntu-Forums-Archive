---
title: "fsck dies with exit status 8"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by scragar on 2008-04-25
what should I do? Nothing appears to be broken, however this error is really holding up my boot sequence(at least until I hit ctrl+D to continue).

```
scragar@scragar-comp:~$ cat /var/log/fsck/checkfs
Log of fsck -C3 -R -A -a 
Sat Apr 26 02:47:57 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda2 is mounted.  e2fsck: Cannot continue, aborting.


/dev/sdb1: clean, 15299/30539776 files, 21754058/61049000 blocks
fsck died with exit status 8

Sat Apr 26 02:47:57 2008
----------------
```

Any help greatly appreciated.

---

### Post by Google Spider on 2008-04-25
hmmmm...I had a similar problem with mint a few days ago.
[http://www.linuxmint.com/forum/viewtopic.php?f=90&t=11698](http://www.linuxmint.com/forum/viewtopic.php?f=90&t=11698)

Though I formatted the whole drive and set up my triple boot(xp/mint/hardy) again, so can't really help more than giving you that link.

---

### Post by talsemgeest on 2008-04-25
Run e2fsck from the live cd.

---

### Post by scragar on 2008-04-25
Since it wasn't my main partition causing the problem(it was my second HD's first partition), I could run that command without needing to use a liveCD. After reading the manual page I found that I required the **-f** flag```
sudo e2fsck -f /dev/sdab1
```restarting after this didn't produce the problem, so that's fixed it. thank's so very much.

---

### Post by blastus on 2008-04-26
An "fsck died with exit status 8" is usually caused by an invalidated UUID in your /etc/fstab file. Edit /etc/fstab and make sure the UUIDs match what the following command shows:

```
ls /dev/disk/by-uuid -alh
```

Edit: Every time you format a partition it gets a new UUID. This is the primary cause of an invalidated UUID in /etc/fstab.

---

### Post by scragar on 2008-04-26
I knew about this, and changed all my stuff before that, replacing the UIDs with the relevant paths. I knew I would have to do this to start with, since I was installing windows onto a partition that contained my old gutsy install(Forgive me, I want to play the latest PC games...)

---

### Post by talsemgeest on 2008-04-26
Glad I could help.

---

