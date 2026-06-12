---
title: "how to distinguish between usb flash and USB removable hard disk"
date: 2010-11-08
forum: Programming Talk
---

### Post by onlythegod on 2010-11-08
I plan to write a program that can distinguish between USB flash drivers and removable driver.I believe linux can tell apart them because gnome displays the usb flash and USB removable hard disk in different icons.
but, I have no idea about how to implement it.
Can anyone help me or give me some ideas?

---

### Post by spjackson on 2010-11-08
> **onlythegod said:**
> I plan to write a program that can distinguish between USB flash drivers and removable driver.I believe linux can tell apart them because gnome displays the usb flash and USB removable hard disk in different icons.
but, I have no idea about how to implement it.
Can anyone help me or give me some ideas?
You asked this question a week ago and nobody knew the answer. What avenues have you explored in the meantime? What fresh input can you provide?

After some research, I understand that most (but not all) flash usb drives identify themselves as removable media (i.e. the Removable Media Bit is set). With most external usb hard disks this is not the case; I haven't been able to determine whether there are any external usb hard drives that set the Removable Media Bit.

Here are 3 links for querying this status in Python, C++ and C.

[http://library.gnome.org/devel/pygobject/stable/class-giodrive.html#method-giodrive--is-media-removable](http://library.gnome.org/devel/pygobject/stable/class-giodrive.html#method-giodrive--is-media-removable)

[http://library.gnome.org/devel/glibmm/2.23/classGio_1_1Drive.html#aa9c9b3db01d76f26527702860498b531](http://library.gnome.org/devel/glibmm/2.23/classGio_1_1Drive.html#aa9c9b3db01d76f26527702860498b531)

[http://library.gnome.org/devel/gio/2.25/GDrive.html#g-drive-is-media-removable](http://library.gnome.org/devel/gio/2.25/GDrive.html#g-drive-is-media-removable)

I hope this helps.

---

