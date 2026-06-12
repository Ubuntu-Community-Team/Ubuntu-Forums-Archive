---
title: "Strange installation issue with Root drive not found"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by NnbEcm4 on 2013-10-20
Hello all! 

My name is Nigel from Lowestoft in the UK and completely novice towards Linux in every sense.

I've been using Ubuntu 8 for a while simply for LinuxCNC on a Clevo L295 all in one.
Having upgraded to 10.04, I have been experiencing a few issues. First of all, when booting into 2.6.32-52-generic Kernel, I was getting some strange display corruption, the screen what pink, flashing with thousands of streaking lines.
I eventually fixed it with xforcevesa and nomodeset and so far from the look of it, 10.04 is a nice step up.

Now, LinuxCNC will only run on 2.6.32-122 but I've only got 2.6.32-52 and 2.6.24-16-rtai

Doing a grub-update shows -122 on the list but it doesn't appear on the boot menu

Any ideas?

---

### Post by NnbEcm4 on 2013-10-20
Well, I've actually just now managed to fix it. I simply booted into the Linux kernel that worked and opened up the grub list.
Copied of one of the selections and pasted it further down and simply renamed the kernel on the lines to -122.

Sorted!

---

