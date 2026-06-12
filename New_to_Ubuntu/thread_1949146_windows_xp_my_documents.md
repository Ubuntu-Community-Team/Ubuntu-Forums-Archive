---
title: "windows xp my documents"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by lach3 on 2012-03-29
How do i view Windows My Documents folder through ubuntu.
I installed a dual boot ubuntu_wubi on my windows xp laptop.

---

### Post by Gleichsnerd on 2012-03-29
Hello, and welcome to the Ubuntu Forums!

I'm not a champ at wubi due to a personal loathing of the software, so you'll have work with me here.

When you open up the home folder (the folder icon in the unity dash), is there an option under the "Devices" title (towards the upper left of the window) that says "<somenumber>GB Filesystem"?

If so, then click that. It will mount the partition that XP works off of. You can navigate through Documents and Settings to find your documents there.

If not, then I greatly apologize, and hope that someone on here has more experience with Wubi than I.

Btdubs, once you're comfortable with the Ubuntu operating system, I **_STRONGLY_** recommend that you do a full install in a separate partition.

Cheers!

---

### Post by CharlesA on 2012-03-29
I think the windows partition is mounted to /host/ or some such thing.

[https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

---

