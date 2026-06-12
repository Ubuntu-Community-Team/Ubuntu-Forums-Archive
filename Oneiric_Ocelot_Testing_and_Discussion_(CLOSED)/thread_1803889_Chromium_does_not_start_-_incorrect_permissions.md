---
title: "Chromium does not start - incorrect permissions"
date: 2011-07-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-14
After important updates chromium does not start any more:
- base-files (6.4ubuntu1)
- initscripts (2.88dsf-13.10ubuntu3)
- mountall (2.29)
- sysv-rc (2.88dsf-13.10ubuntu3)
- sysvinit-utils (2.88dsf-13.10ubuntu3)

I get this permission error:
```

[1601:1611:838108318:ERROR:shared_memory_posix.cc(158)] Creating shared memory in /dev/shm/.org.chromium.Chromium.hb5Es7 failed: Permission denied
[1601:1611:838108431:ERROR:shared_memory_posix.cc(161)] Unable to access(W_OK|X_OK) /dev/shm: Permission denied
[1601:1611:838108478:FATAL:shared_memory_posix.cc(163)] This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 1777 /dev/shm' to fix.
Aborted

```

After changing permissions Chromium is OK again.
```

sudo chmod 1777 /dev/shm

```

---

### Post by rburkartjo on 2011-07-14
harry will give that a try chromium just stopped working for me also

---

### Post by P-I H on 2011-07-14
> After changing permissions Chromium is OK again.
Code:
```
sudo chmod 1777 /dev/shm
```

That worked for me too

---

### Post by VinDSL on 2011-07-14
TY, Harry!

We know we can always depend on you - even if it takes a few minutes to wait for a post...  :D

OMG!  How I've grown to h-a-t-e Firefox!?!?!  I was going to go to bed, and such my thumb.

Chromium is working again, for me, also...  ;)

---

### Post by jbicha on 2011-07-14
This bug is part of the ongoing /run migration. It's a high priority bug and is being worked on.

---

### Post by Harry33 on 2011-07-14
Hmm, and my workaround (sudo chmod 1777 /dev/shm) does not survive a reboot.

---

### Post by Harry33 on 2011-07-14
It seems these updates have fixed this Chromium-browser shm-permission issue too.

```

Upgraded the following packages:
initscripts (2.88dsf-13.10ubuntu3) to 2.88dsf-13.10ubuntu4
libgudev-1.0-0 (1:172-0ubuntu2) to 1:172-0ubuntu3
libudev0 (172-0ubuntu2) to 172-0ubuntu3
mountall (2.29) to 2.30
sysv-rc (2.88dsf-13.10ubuntu3) to 2.88dsf-13.10ubuntu4
sysvinit-utils (2.88dsf-13.10ubuntu3) to 2.88dsf-13.10ubuntu4
udev (172-0ubuntu2) to 172-0ubuntu3

```

---

### Post by rburkartjo on 2011-07-14
yup harry update on my end also fixed the issue. glad to have chromium back

---

### Post by Harry33 on 2011-07-14
> **rburkartjo said:**
> yup harry update on my end also fixed the issue. glad to have chromium back

Yes I am also so used to work with Chromium that Firefox feels odd to me now.

---

### Post by VinDSL on 2011-07-14
> **Harry33 said:**
> Yes I am also so used to work with Chromium that Firefox feels odd to me now.
Fx used to be my favorite browser.  They lost me after version 3.5

A year ago, I started a thread on Anandtech chronicling its replacement:

[ Oh, my! I'm about to abandon Firefox, in favor of Chrome...]("http://forums.anandtech.com/showthread.php?t=2073956")

My 6-month quest ended with a whimper, not a bang.  However, Chrome was the clear victor.

I don't know exactly when I started running Chromium, but now I prefer it to all else - by far.  ;)

---

### Post by mooreted on 2011-07-17
Try adding this to fstab:

none /dev/shm tmpfs defaults 0 0

---

### Post by Harry33 on 2011-07-17
> **mooreted said:**
> Try adding this to fstab:

none /dev/shm tmpfs defaults 0 0

Don't know to whom you replied to, but this bug has been fixed.

---

### Post by mooreted on 2011-07-17
> **Harry33 said:**
> Don't know to whom you replied to, but this bug has been fixed.

Well, I just had this issue yesterday and this seems to have fixed it. It certainly doesn't hurt to have that entry in fstab.

---

