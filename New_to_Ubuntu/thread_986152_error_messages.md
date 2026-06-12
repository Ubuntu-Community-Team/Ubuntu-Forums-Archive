---
title: "error messages"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-18
Hi I get these error messages when loading into Ubuntu
1. unrecognised partition table for drive 84.use FDisk ...
2.unable to enumarate usb device on port 2.
3. firefox still crashes because of segmantion fault. This is not specific
to Ubunti. But does anybody have any solutions?
M

---

### Post by cmnorton on 2008-11-18
The first thing I would do is fix the disk problem. Even if you can boot into Ubuntu, I'd be more inclined to fix this with a rescue disk, although someone more experienced might have a way to fix this by logging in directly.

What's in your /etc/fstab file?

It may be as simple as needing to partition and format this disk, but without knowing why it's there and called that name, I'd hesitate to do anything.

---

### Post by irish66 on 2008-11-18
I presume i type
/etc/fstab file
into terminal.
Well I did anyhow, anf got permission denied.
M

---

