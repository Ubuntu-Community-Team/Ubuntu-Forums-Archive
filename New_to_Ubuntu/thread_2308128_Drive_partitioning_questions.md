---
title: "Drive partitioning questions"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by mj3mari on 2015-12-31
hello, i dont speak english very well. I thing i have an issue, i installed ubuntu 14.04 with separate partitions /boot=2gb /(/root)=100gb /home=50gb /swab=12gb and others, so i checked the free space with gparted and i surpriced /(/root)=100gb its 100gb free space its empty. the others partitions get informations like usage space but /(/root) not. Could you like to explaint me whats happen in that partition?
i get into /home 30gb free space and 50gb usage space. but My ubuntu 14.04 run very well so if its free space in /(/root) maybe i get a resize this partition to 20gb or 50gb and put it into /home to get more free space.
Last time when i has ubuntu 12.03  every partition gets usage space /home /root /boot /usr /var and ran very well. i didnt found explication to the free space into /(/root).
Regards.

---

### Post by oldfred on 2015-12-31
Please post this from terminal in your system:
df -h
       sudo parted /dev/sda unit s print

For standard desktops, I do not suggest separate system partitions with the possible exception of /home. Or  /boot, /var, and /usr should just be inside / (root).
Standard default install from Ubuntu is just / & swap. And for a new user that is fine. Then a bit more advanced is adding a separate /home. And still more advanced is use of /mnt/data for all data normally stored in /home and mount with fstab and use links to make data look like it is in /home.

Users with Windows should add a shared NTFS formatted data partition and optionally add links. New users can just copy data.

---

