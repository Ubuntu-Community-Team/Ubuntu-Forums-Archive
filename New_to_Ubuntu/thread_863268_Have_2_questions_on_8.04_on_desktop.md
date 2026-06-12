---
title: "Have 2 questions on 8.04 on desktop"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by mastergunner on 2008-07-18
How do I remove previous kernels after there is an update. Also how do I remove different versions of firefox.

---

### Post by tuxxy on 2008-07-18
Remove both using Synaptic Package Manager, search for you old kernal image and remove, do the same for your firefox version you would like to remove.

---

### Post by overdrank on 2008-07-18
> **mastergunner said:**
> How do I remove previous kernels after there is an update. Also how do I remove different versions of firefox.

To add to tuxxy this link may help.
[http://ubuntuforums.org/showthread.php?t=858840](http://ubuntuforums.org/showthread.php?t=858840)

---

### Post by mastergunner on 2008-07-18
Thanks but that doesnt work. For firefox I have tried that and I have in my usr/bin 3 different firefox executables. They are firefox, firefox-3.0 and mozilla-firefox. How can I just wipe all of these out and reload the current version. Also can you explain a little more about the kernel removal. At boot up it says I have like 4 different kernels. I just pick the newest one to load.

---

### Post by Troll_the_Great on 2008-07-18
Open Synaptic and search for "linux headers".There you will see kernel 2.6.24-16 and so on.Just remove the one you don't need anymore.
Cheers!

---

### Post by Oldsoldier2003 on 2008-07-18
> **mastergunner said:**
> Thanks but that doesnt work. For firefox I have tried that and I have in my usr/bin 3 different firefox executables. They are firefox, firefox-3.0 and mozilla-firefox. How can I just wipe all of these out and reload the current version. Also can you explain a little more about the kernel removal. At boot up it says I have like 4 different kernels. I just pick the newest one to load.

Do a synaptic search for "linux-image" and mark the old kernels for complete removal, this will also remove them from your bootup menu. If you have two kernels you will have four options, the regular boot and recovery mode for each of the two kernels.
edit: you should be able to do the same in Adept.

---

### Post by mastergunner on 2008-07-18
Appreciate it. Now how about my Firefox issues. Any ideas on that?

---

### Post by tuxxy on 2008-07-18
EDIT: I beleive you should be using the /lib/mozilla/ dir

---

### Post by mastergunner on 2008-07-18
What does this do tuxxy?

---

### Post by phoenix_abhi on 2008-07-18
What should I use to remove ? Removal or complete removal option ? (kernel)

---

### Post by tuxxy on 2008-07-18
Complete removal if you wont use again :)

---

### Post by Oldsoldier2003 on 2008-07-18
> **phoenix_abhi said:**
> What should I use to remove ? Removal or complete removal option ? (kernel)

complete removal will remove the kernel and all the associated dependencies. When you want to get rid of old kernels use complete removal.

---

### Post by phoenix_abhi on 2008-07-18
Thanx done a complete removal

---

