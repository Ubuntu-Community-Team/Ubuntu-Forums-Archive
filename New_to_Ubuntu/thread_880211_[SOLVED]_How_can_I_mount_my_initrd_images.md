---
title: "[SOLVED] How can I mount my initrd images?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by eilenbeb on 2008-08-04
Solved.

original--------------------------------------------------------------
(noob warning)

Ubuntu(hardy) generates a new initrd.img when I install dmraid.  I do this for access to my fakeraid0 containing windows.

The new initrd.img fails to boot, unable to mount sys proc init (or something like that).

To fix this, I boot with a live CD and replace the initrd.img with the backup initrd.img.

What I want to do is mount the 2 images for comparison so I can figure out what is happening, why, and how.

thanks,
b
reolution--------------------------------------------------------------
I simply copied the img files to my home directory, renamed them as .gz.
Then I could open and extract them with an archiver.

---

