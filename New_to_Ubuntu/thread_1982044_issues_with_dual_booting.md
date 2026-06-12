---
title: "issues with dual booting"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by hookitup on 2012-05-17
so i am trying to dual boot windows 7 and ubuntu 12.04, i have windows currently installed and so then i booted a live ubuntu 12.04 usb and when i go to install i only get two options, "erase disk and install ubuntu" "something else", how come i do not see the "install ubuntu alongside windows7" doesnt make sense to me. when i go to something else it shows that i do have the harddrive in there and it can see its full size.


Thanks for the help.

---

### Post by wilee-nilee on 2012-05-17
If you have 4 primary partitions this will happen, and if you have not made a unallocated space to install Ubuntu in. I suspect 4 partitions already. Open gparted on the live Ubuntu desktop and take a screenshot of the HD and post it.

---

### Post by hookitup on 2012-05-17
thanks for your quick reply, durning the windows installation i split the hardrive in two partitions, then it got split in a 3rd with 100mb or something for the system memory (standard for windows) so i do have about 40GB of unallocated space worth of one partition, and its not seeing it at all, when i go into gparted it shows the whole hardrive space as unallocated



update: i just check windows and it can see all 3 partition, (100MB for system reserve) (40gb for windows C:) and (40gb unallocated) 
now why cant gparted see this, so strange.

---

### Post by oldfred on 2012-05-18
If you made partitions in Windows, they will not work for Linux and Windows may have converted to dynamic?

Check if in Windows partitions show as basic or dynamic.

---

### Post by hookitup on 2012-05-20
i think that might have been the issue, i just erased the hard drive and installed ubuntu

---

