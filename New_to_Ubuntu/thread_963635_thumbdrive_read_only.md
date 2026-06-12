---
title: "thumbdrive read only"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by cgkades on 2008-10-30
how do i tell the system to mount my thumb drive with rw privileges not just ro? i'm not sure how it got screwed up either, so if anyone has any ideas as to what may have caused this that would be helpful too.

Thanks for any help :)

oh not sure if it matters, but i'm still using 8.04

edit: i figured out how to do it manually, but how to i set the system to always do it.. here's a screen shot of the problem. i cant figure out how to change that ro. and there are settings below, but i dont know where it saves those either

---

### Post by Mark_in_Hollywood on 2008-10-31
Those devices have driven me nuts. My fastest way was to reformat the device in Windows xp.

If the above isn't "up to snuff" for you, load the LiveCd, select partition manager or use GParted LiveCd and set disklabel to "msdos" and format the device as ext2 or ext3.

Horsing around with sudo chown and such takes too much time.

---

