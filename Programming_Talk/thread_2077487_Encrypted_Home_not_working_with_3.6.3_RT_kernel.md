---
title: "Encrypted Home not working with 3.6.3 RT kernel"
date: 2012-10-28
forum: Programming Talk
---

### Post by zenon222 on 2012-10-28
I run ubuntu 10.04 Lucid.  I custom compile vanilla kernels with the RT patch to use with JACK.

Yesterday I compiled a fresh 3.6.3-rt6 kernel and ubuntu failed to fully load into gnome.
I flipped to a terminal to start digging around at why gnome thought  some files in the /home/[user]/ directory were not "writable" and  quickly discovered that my encrypted home directory had not loaded!

I had compiled with the "make oldconfig" and then went into menuconfig to confirm everything looked as I like it.  It did.

Currently I'm running off an old 3.4.11-rt19 kernel.

I have confirmed that "eCrypt filesystem layer support" was indeed  checked as "compiled in" (not just module, but forced into the kernel).

What gives?!

HELP!

---

### Post by zenon222 on 2012-11-03
?bump? :-(

---

