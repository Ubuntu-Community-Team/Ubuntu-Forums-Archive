---
title: "unmountable drive"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-27
When I try to mount my windows drive (c:), i get this error. 
[IMG]http://img137.imageshack.us/img137/575/screenshotgnomemountad6.png[/IMG]

It used to work up until this morning, i dont know what happened.

---

### Post by alienexplorers on 2008-05-27
Did you do the new updates for Hardy.  The kernel was updated and that might be causing your problem.  If you still have the old kernel in the grub menu then boot to the older kernel and see if that helps.

---

### Post by adobrakic on 2008-05-27
Yeah, i did the new updates. But i'm really not sure if i have the old updates, or how i even would implement them instead of the new ones. :x

---

### Post by alienexplorers on 2008-05-27
When you boot up do you get the grub menu.  It normally lists the regular kernel and the recovery mode.  If you don't get this menu then hit <esc> while grub is loading.  That should bring up the grub menu.  Check to see if you have both the 16-xxx and 17-xxx kernels.

---

### Post by Kevbert on 2008-05-27
Funnily enough I had this problem yesterday.  Boot in windows, log in and then shutdown the PC completely.  Next turn on the PC boot into Ubuntu and you should be able to mount the drive as normal.  I'm using 7.10.

---

### Post by adobrakic on 2008-05-27
Yeah, i do get that. And yeah, it does give me both of those kernals cause i remember thinking "why is there four different modes i can choose from", should i choose the 16 regular mode?

---

### Post by adobrakic on 2008-05-27
> **Kevbert said:**
> Funnily enough I had this problem yesterday.  Boot in windows, log in and then shutdown the PC completely.  Next turn on the PC boot into Ubuntu and you should be able to mount the drive as normal.  I'm using 7.10.

ill also try this, thanks

---

### Post by bumanie on 2008-05-27
> sudo apt-get install ntfsprogs> sudo ntfs fix or else remount the drive in windows and remove via the correct shutdown process ie safe removal of device.

---

