---
title: "just noticed hard drives have stopped automounting at startup"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by snuffy on 2008-08-22
just noticed my hard drives have stopped automounting at startup.

They used to automount, i'm sure, because they would show up on my desktop at startup. 

this is especially annoying as my music collection is on one of those drives, so when i start rhythmbox, it removes all my mp3s because it thinks they're not there.

is there a simple way to get them to automount again?

cheers.
tim.

---

### Post by Gannon8 on 2008-08-22
I think the current version of Ubuntu only automounts external devices except those listed in fstab. I'm not sure how to turn it on again, or if it is possible without editing source.

---

### Post by bmac on 2008-08-22
Open Gnome Configuration Editor
apps/nautilus/preferences/media_automount (check box)


Hope this helps....

---

### Post by SpaceMaster on 2008-08-22
helped me as well ^^.  My secondary internal HDD wasn't appearing upon boot.

You just saved me three clicks each time I start up! (or from entering on each startup "sudo mkdir /media/*** && sudo mount -t ext3 /dev/sdb1 /media/***") ^_^

---

### Post by snuffy on 2008-08-22
i checked this. the box was already checked.

now what?



> **bmac said:**
> Open Gnome Configuration Editor
apps/nautilus/preferences/media_automount (check box)


Hope this helps....

---

### Post by bmac on 2008-08-22
In the same apps/nautilus/preferences
Is your "show_desktop" checked? Assuming you want them to show on your desktop, as indicated in your original post.

---

### Post by philinux on 2008-08-22
You could install pysdm which is a gui for managing fstab and mounts etc.

---

### Post by snuffy on 2008-08-22
yes, show desktop is checked.


> **bmac said:**
> In the same apps/nautilus/preferences
Is your "show_desktop" checked? Assuming you want them to show on your desktop, as indicated in your original post.

---

### Post by egalvan on 2008-08-22
After booting, external drives show on the desktop, and the internal drives I can get by going to:

  Places

then clicking the drive I want. It immediately shows on the desktop.

That's only two clicks :)


Also, most of my external drives are NTFS, so I can still easily use them with other folk's computers.

:popcorn:

---

### Post by snuffy on 2008-08-24
i installed pysdm, but i can't find it in the applications/system menu. where is it?


its these things that annoy me about ubuntu.

all i want is my drives to automount and show up on the desktop. :-(

---

### Post by porchrat on 2008-08-24
if you recently messed around with the drives (for example reformatting etc.) the UUID may have changed in which case fstab would be attempting to mount a drive with the wrong UUID.

Check the UUID.  Happened to my swap partition once

---

