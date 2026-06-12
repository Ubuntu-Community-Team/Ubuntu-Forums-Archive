---
title: "Grub refuses to get to the bootsreen."
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Auriono on 2008-05-03
Whenever Grub is about to load up Ubuntu, I get this message,

Undefined Video Mode Number 318.
Then loads up a bunch of video number resolutions but they don't seem to do anything when active...any help?

---

### Post by Auriono on 2008-05-03
Anyone?

---

### Post by schnauzer93 on 2008-05-04
I have this problem, too.

---

### Post by NightwishFan on 2008-05-04
Perhaps boot into recovery mode and edit your /boot/grub/menu.lst and delete the lines "quiet" and "splash" although im not sure how to do that from recovery mode. It is worth a try until someone else can drop in to help.

---

