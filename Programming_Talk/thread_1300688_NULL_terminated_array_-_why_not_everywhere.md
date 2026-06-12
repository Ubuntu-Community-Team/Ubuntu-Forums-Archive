---
title: "NULL terminated array - why not everywhere?"
date: 2009-10-25
forum: Programming Talk
---

### Post by froggyswamp on 2009-10-25
Folks, while learning C & Gtk I found that in some cases one is required to pass a NULL terminated string array. As far as I understand NULL is required for the other function to detect the length of the array.
If so, isn't it a small inconsistency that in other areas one is required to also pass the size (of whatever array) as a separate parameter? or is here performance at stake? Just wondering.

EDIT:
oops apparently the post before mine clarified this
[http://ubuntuforums.org/showthread.php?t=1300667](http://ubuntuforums.org/showthread.php?t=1300667)

---

### Post by MadCow108 on 2009-10-25
in addition to the reason in the other thread (determining size needs a loop over whole array) terminated arrays have the disadvantage that the terminating construct can not appear in the data of the array.

e.g. a null terminated array cannot contain null bytes.
This is no problem with cstrings or certain arrays of pointers as no character contained in a string is coded to null and no legit pointer should have the value null.
But in general this is a problem.

---

