---
title: "[SOLVED] What permssion does a user need for external usb hard disk drive?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-27
I have an external usb 2.0 hard disk drive. Under the devices "Properties" and "Permissions" it says:

The permissions of "marks80" could not be determined. The "marks80" is name on the icon on Desktop.

I opened gksudo nautilus and had a look at the drive & permissions. It showed the permissions as belonging to: mark (my username). And group mark, too.

I seem to be able to copy and paste and delete files from the ext. drive, but don't know how or (more importantly) what to fix so the drive's properties shows (and more importantly) HAS the correct user permissions.

---

### Post by eentonig on 2008-10-28
So functionally, it's is working fine? It's just the information it shows under 'Properties', correct?

---

### Post by Mark_in_Hollywood on 2008-10-29
when I look at the device's permission in /media/devicename, it shows as being owned by the user and NOT by root. Same for group.

The desktop icon for the same device says: The permissons for "devicename" can't be determined.

This is a bug or fluke in the OS. I know USB devices are being harmonized better into the kernel, so I'm lovin' the wait.

Linux rocks! and 

Thanks, community.

---

