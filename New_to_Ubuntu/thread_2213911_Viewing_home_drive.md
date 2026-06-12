---
title: "Viewing home drive"
date: 2014-03-29
forum: New to Ubuntu
---

### Post by Asif_Khan on 2014-03-29
I can see all my drives C,E but not D where my ubuntu is installed(installed using wubi).How to view my drive?

---

### Post by grahammechanical on 2014-03-29
I am sure that when we install Ubuntu using Wubi we do not get a real drive/partition. Ubuntu is installed inside Windows. I guess it resides in a Windows folder. Now, if we are in Ubuntu and using File Manager to see the partition that Ubuntu is installed in we look in the left hand pane where it says devices and we open either File System or Computer, depending on the version of Ubuntu we are using. Then we see all the system files/folders. Some of which are hidden by the way.

Regards.

---

### Post by Impavidus on 2014-03-29
If you use wubi, the partition on which Ubuntu is installed (the "D drive" in your case) can be found at /host.

---

