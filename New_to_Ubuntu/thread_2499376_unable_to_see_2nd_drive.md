---
title: "unable to see 2nd drive"
date: 2024-07-24
forum: New to Ubuntu
---

### Post by cemenc2 on 2024-07-24
Hello,

newbie here, 

I installed xubuntu on my desktop computer with 250gb ssd and 1tb sata drives. 
I confirmed OS installed on SSD. after I boot into OS I can't seem to use (see or open) the 2nd drive. 

it is not automatically mounted 
what do you suggest?

---

### Post by oldfred on 2024-07-24
Partitions are not automatically mounted unless in fstab.

Post this in code tags.
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint
sudo parted -l
cat /etc/fstab

---

### Post by yancek on 2024-07-25
On Linux systems, access to directories outside the user /home directory is limited and it is up to the user to modify this.  The information requested in post 2 will help determine your situation but this is very basic and you need to know if if you are going to be using Ubuntu/Linux.   The Ubuntu Desktop Guide at the Ubuntu site from the link below would be a good place to start.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

