---
title: "GParted won't stop &quot;scanning all devices&quot;"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by t0p on 2008-07-30
I want to reformat a USB flash memory stick.  I decided to use **GParted** to do this.

So, I plugged in the stick. I right-clicked the stick's icon on the Desktop and unmounted it.  Then, in a terminal I typed

```
sudo gparted
```

The GParted window opened, with everything greyed-out except in the bottom of the window where it says **Scanning all devices...** and an orange "progress bar" flashing from the left to the right...

And that's it! GParted has been "scanning all devices" for over 10 minutes! I have stopped and restarted the program a few times, and GParted just does the same every time.  It says it's "Scanning all devices..." and won't go any further.

What can I do to fix this?  Or, if I can't fix GParted, what alternatives do I have to reformat the flash stick?

---

### Post by iaculallad on 2008-07-30
Kill the running Gparted process, and instead of doing,

```
sudo gparted
```

try:

```
gksudo gparted
```

---

### Post by saratchandra on 2008-07-30
Make sure all the partitions are mounted

---

### Post by t0p on 2008-07-30
> **iaculallad said:**
> Kill the running Gparted process, and instead of doing,

```
sudo gparted
```

try:

```
gksudo gparted
```

I tried that, but it doesn't appear to make any difference.

---

### Post by t0p on 2008-07-30
> **saratchandra said:**
> Make sure all the partitions are mounted

If I run GParted with the flash stick mounted, it scans the stick and displays its properties okay.  But I need to unmount the stick in order to format it, right?  And when I unmount it, GParted goes into its endless "scanning".

---

### Post by saratchandra on 2008-07-30
> **t0p said:**
> If I run GParted with the flash stick mounted, it scans the stick and displays its properties okay.  But I need to unmount the stick in order to format it, right?  And when I unmount it, GParted goes into its endless "scanning".

Just tried it on my computer and it worked. Here is how I did it. Go to "My Computer" and click on all drives. Then start gparted. It will open normally. Rightclick on the partition you want to format and click unmount. That works for me.

---

### Post by t0p on 2008-07-30
> **saratchandra said:**
> Just tried it on my computer and it worked. Here is how I did it. Go to "My Computer" and click on all drives. Then start gparted. It will open normally. Rightclick on the partition you want to format and click unmount. That works for me.

**Thanks** saratchandra!  I did what you said and it worked!  :)

---

### Post by Dr Small on 2008-07-30
I was going to suggest, that if you open gparted with the flash drive mounted, then unmounted it in gparted, it might have worked.

---

### Post by jnw222 on 2008-07-30
or use comand to unmount

sudo umount /dev/xxxy (drive name for me it is normally sdb)

---

### Post by jimav on 2013-01-17
The same infinite scan happens for me too when a USB hard drive is plugged in which is not formatted.

gparted seems to be trying to access the non-existent FLOPPY DISK
at /dev/fd... zillions of "Buffer I/O error on device fd0" are logged to /var/log/kern.log while gparted is "scanning".

Specifying a specific device as an argument to gparted does not prevent it from this scanning.

---

### Post by s.fox on 2013-01-18
Necromancy. Closed.

---

