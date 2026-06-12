---
title: "[SOLVED] partition not recognized till clicked."
date: 2008-08-07
forum: New to Ubuntu
---

### Post by allenbradley on 2008-08-07
I recently installed ubuntu 8.04 x86, dual booting with vista on a dell inspiron 1525. I have a vista partition, a data partition for vista nd linux to access. I store my stuff, such as songs, in the data partition. When i boot into ubuntu, and turn amarok on, it says the file cannot be found.However, when i go to the Data partition via Places on the toolbar, the Partition icon shows up on the desktop and amarok finds all the songs. On my friends comp however, the partition icon shows up on the desktop immediately after boot, while mine does not. In order to make the icon appear everytime,i have to click on places and then access the partitionto see the icon. Can anyone please help?

---

### Post by Victormd on 2008-08-07
Check the link on my signature to automount your partitions at startup... Let me know if you run into any problems.

---

### Post by lordadi on 2008-08-07
Hi,

You are going to need to edit your fstab, so that DATA gets mounted upon boot. Following that link recommended above is the way to go.


Cheers,


Lordadi.

---

### Post by allenbradley on 2008-09-16
The method is not working. I tried it out but there is no difference. What should I do now?

---

### Post by nowshining on 2008-09-16
i just created a manual mount script edit it to ur needs and then add it as a menu item: - add them both to a new txt file and make sure they are executable... as for the menu items - create a new main folder/subfolder and link to them...

Mount - first script

```
#!/bin/bash

gksudo mount /dev/sdb1 /media/mydisk -t ext3

exit 0
```

unmount

```

#!/bin/bash

gksudo umount /dev/sdb1 /media/mydisk -t exxt3 

exit 0
```

ah! but first we needo create a folder in /media/

open up a terminal

sudo mkdir /media/nameoffolderyouwant

example to go with the above scripts

sudo mkdir /media/mydisk

---

### Post by angelsguitar on 2008-09-16
If your windows partitions are formated in ntfs, install ntfs-config.  You can find it in Synaptic, or just type this command at the terminal:

```
sudo apt-get install ntfs-config
```

Once installed, look for it on the "System Tools" section in the Applications menu.  Run it, put the admin password, mark all hard drive check marks, press OK, and again mark all checkmarks (Enable support for all external devices, and Enable support for all internal devices).  Press OK.  Now your ntfs (windows) partitions should mount automatically, and the icons should appear on your desktop.

---

### Post by allenbradley on 2008-09-16
Got it! Thanks a lot guys.

---

### Post by pmlxuser on 2008-09-16
so would you please mark your thread [solved]

---

### Post by allenbradley on 2008-09-16
oh right... Sorry!

---

