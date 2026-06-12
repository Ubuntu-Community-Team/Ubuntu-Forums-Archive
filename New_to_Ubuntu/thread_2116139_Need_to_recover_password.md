---
title: "Need to recover password"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by Greenwick on 2013-02-14
I recently updated to Ubuntu 12.10 and also installed the Gnome desktop.  I also changed my settings so tgat I didn't have to enter my password anymore.  Now my assword has apparently been changed, and I have no idea what it is.  (I am certain I remember it, so that isn't the issue.)

I tried following this guide
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

I was able to access the shell, and this is what happened:

passwd < username >
Enter new UNIX password:
Retyoe new UNIX password:
passwd: Authentication token manipulation error
passwd: password unchanged

---

### Post by zombifier25 on 2013-02-15
Tip: if you are the only admin user of the system, do not change your password to blank, because it will break a lit of stuffs and you'll no longer be able to do anything that modifies the system.

About the GRUB part, you must hold the Shift button throughout the boot process so that GRUB shows up. If you fail, reset and try again. When GRUB shows up, follow the rest of the instructions.

---

### Post by Greenwick on 2013-02-15
Thanks, I was able to get GRUB to show up.  I had trouble with it at first, but the I found this article where someone else had the same problem I was having.

[http://prefetch.net/blog/index.php/2011/08/29/remounting-linux-read-only-file-systems-read-write/](http://prefetch.net/blog/index.php/2011/08/29/remounting-linux-read-only-file-systems-read-write/)

It looks like my computer was set to read/write

---

### Post by zombifier25 on 2013-02-15
So did you fix it?

---

### Post by Greenwick on 2013-02-15
Yes, I was abe to fix it.  After I set it to read/write instead of read only, I was able to change my password in the root directory.  Not sure how to set this thread as solved, or if that's a current function on the forum.

---

### Post by Mark Phelps on 2013-02-16
Look at the Thread Tools in the upper right area of the thread, use the pulldown to select SOLVED.

---

### Post by Greenwick on 2013-02-19
Thanks!

---

