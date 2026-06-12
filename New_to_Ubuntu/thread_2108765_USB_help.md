---
title: "USB help"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by tokyo08 on 2013-01-25
when i plugged my USB into the computer, it worked on Linux, but when i shift to Microsoft, on another computer, it is not working and it says it does not recognize the device, is it the computer and the drivers, or is it something with the Linux?

---

### Post by d4m1r on 2013-01-25
Are you talking about a USB memory stick? Did you format it under linux?

If so, what kind of filesystem did you format it into?

---

### Post by tokyo08 on 2013-01-25
i tried to, and it worked, then i go to microsoft,it doesnt, do i have to reformat it?

---

### Post by tgalati4 on 2013-01-25
If you formatted it under linux, it either put on ext2, ext3, or ext4 and Windows won't be able to read it--without loading extra stuff to support ext file systems.  If you formatted it as FAT32, it's possible that the Cylinder, Head, Sector count got messed up.  USB and SD cards need a specific CHS count to function properly.  Back up your data under Linux and then reformat in Windows.  Then the drive should be OK for both systems.  Write down the CHS count for future reference.

---

### Post by tokyo08 on 2013-01-25
ok! you solved mai problem!

---

### Post by mörgæs on 2013-01-25
Good, then please mark the thread 'solved' using 'thread tools'.

---

### Post by tokyo08 on 2013-01-25
thanks for telling me how...i didnt know

---

