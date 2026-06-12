---
title: "eject cd"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by rox1547 on 2008-04-30
Dumb question alert.
I'm running the Ubuntu live cd (my hard drive is dead). I want to burn an iso but I can't even eject the cd. I typed mount -l in terminal in an attempt to get the drive name right so I could try the eject or umount command, and I can't even see the cd drive listed there...

---

### Post by angry_johnnie on 2008-04-30
to eject:

```
eject cdrom
```

to insert the tray back

```
eject -t cdrom
```

---

### Post by sam_delta on 2008-04-30
as far as i know you cant eject a live CD, since your running the system off the cd, the CD acts as something like your filesystem in a harddrive install

i might be wrong tho

try getting an external burner or something

sam

---

### Post by rox1547 on 2008-04-30
eject cdrom doesn't work. I don't get an error message, but nothing happens.

As for being unable to eject the live cd with Ubuntu up and running.. I thought everything needed to run Ubuntu was cached or something. But I'm probably wrong, and maybe I can't eject the cd after all.

---

### Post by zithe on 2008-04-30
When you turn on your computer, immediately hit the eject button. Might do something for you.

If you're forgetting 'sudo' in front of 'eject cdrom', that MAY cause a problem.

So, open a terminal window and write:

sudo eject cdrom

Worked for me with my CD in it.

---

### Post by steveneddy on 2008-09-28
To burn an .iso, try runninf Puppy Linux.

But you will need a lot of RAM, maybe 2 Gig of RAM.

The OS will live on 50 mb and the CD .iso will be about 700 mb.

For the system to operate well I would have 2 Gig of RAM.

If the hard drive in not operational you have to store all of the memory in the physical memory (RAM)

---

