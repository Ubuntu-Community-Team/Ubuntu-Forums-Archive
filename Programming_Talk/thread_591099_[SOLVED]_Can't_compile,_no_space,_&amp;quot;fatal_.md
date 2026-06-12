---
title: "[SOLVED] Can't compile, no space, &amp;quot;fatal error&amp;quot;"
date: 2007-10-25
forum: Programming Talk
---

### Post by Vadi on 2007-10-25
Hi all,

I've ran into a problem where I can't seem to be able to compile my program at all, due to supposed no space in /tmp. I mount mount my / and my /home patritions on separately, and I cleaned up some space in / already, such that df shows the following:

```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             10128052   8398468   1215104  88% /
varrun                  257632       104    257528   1% /var/run
varlock                 257632         0    257632   0% /var/lock
udev                    257632        60    257572   1% /dev
devshm                  257632         0    257632   0% /dev/shm
lrm                     257632     34696    222936  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             27308248   7524724  18396312  30% /home
overflow                  1024       292       732  29% /tmp
```

But when I try to compile, I still get the "fatal error: error writing to /tmp/ccnXKWYT.s: No space left on device
compilation terminated." error. Can anyone help? I don't know what to do.

---

### Post by tageiru on 2007-10-25
Well that is hardly surprising as your tmp is 1MiB in size. What are you mounting as /tmp?

Your /etc/fstab might shed some light on this.

---

### Post by Vadi on 2007-10-25
I asked a few people about this, and they also found tmp of 1mb to be really weird. I don't know, I didn't do anything with it - I only have the / and my /home.

In any case, I rebooted my laptop, and tmp no longer shows up on "df":

```
$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             10128052   8361460   1252112  87% /
varrun                  257632        96    257536   1% /var/run
varlock                 257632         0    257632   0% /var/lock
udev                    257632        76    257556   1% /dev
devshm                  257632         0    257632   0% /dev/shm
lrm                     257632     34696    222936  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             27308248   8499184  17421852  33% /home
/dev/sdb1               972404    491972    431036  54% /media/disk

```

And I can compile again, so I guess case solved. But I really don't know why did it get mounted.

---

### Post by hecato on 2007-10-25
But ***tmp*** should be there (even that df doesnt list it) 
```
ls /
```Is estrange that it appear with df and with 1Mb... dont know why. Perhaps the solution is like posted above is /tmp/fstab... or what you do in that session could be the answer.

---

### Post by rwmacleod on 2007-11-15
I'm having the same problem.

I found /etc/init.d/mountoverflowtmp
...
# Short-Description: mount emergency /tmp.
# Description:       Mount a tmpfs on /tmp if there would
#                    otherwise be too little space to log in.
...

I think that this gets used if your root filesystem is full on boot.
I've cleared out some space so expect that if I reboot, 
then my kernel compile will work...

I tried to just unmount but of course:

sudo /etc/init.d/mountoverflowtmp stop
 * Unmounting any overflow tmpfs from /tmp...          umount: /tmp: device is busy

// Randy

---

### Post by Vadi on 2007-11-16
Oh, yeah, I did have a problem with a full root patrition - somehow there was 4GB of stuff in trash.

But I deleted that, rebooted, and it was OK.

---

### Post by rwmacleod on 2007-11-16
Yes. That worked for me after all too.

Here's the design outline:
[https://wiki.ubuntu.com/BootLoginWithFullFilesystem](https://wiki.ubuntu.com/BootLoginWithFullFilesystem)

It would be nice if you didn't have to reboot to once you clean-up the full disk.
I guess for most user's only having a 1M /tmp dir isn't a problem
and they can continue using the system indefinitely.

// Randy

---

### Post by mia1dolfan on 2008-01-21
This just occurred to me as well.  After freeing up some space I issued

```
umount -l /tmp
```

and went along my business without rebooting...

---

