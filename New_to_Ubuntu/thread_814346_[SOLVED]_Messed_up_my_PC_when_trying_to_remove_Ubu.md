---
title: "[SOLVED] Messed up my PC when trying to remove Ubuntu"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Justin125 on 2008-05-31
Me, a linux n00b, wanted to remove Ubuntu; I thought:

I'll just remove the partition in Vista and everything will be fine!

And so it was, until I went to restart it and GRUB loaded...

Error 17.

Can't do a thing. I've been reading on it and I hear it has to do with MBR or something?

I REALLY need help. This renders my computer pretty useless.

---

### Post by sayakb on 2008-05-31
Afaik, theres a startup repair in the Vista Setup disk that repairs the boot loader. 
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by gredorian on 2008-05-31
Try this... boot from your Windows disk and go in recovery mode. In the console, enter **fixmbr**. If it doesn't work try **fixboot**.

(I assume you want to fix Windows' boot)

---

### Post by wirelessmonkey on 2008-05-31
Boot from your Vista CD, and allow it to autorepair, or if not given the option, type fixmbr at the repair command prompt.

---

