---
title: "Cant eject 18tb hdd from files tab"
date: 2021-05-15
forum: New to Ubuntu
---

### Post by eammon-123 on 2021-05-15
Hi all. Ive just recently set my my first Ubuntu system, and I am having trouble ejecting one of my internal 18tb barracuda drives. The drive is permanently inserted in my files tab:

However when I go onto the disks it appears to not be mounted or inserted:


And it appears to show up as a disk drive.


Its attached via sas to my adaptec raid card which I think may be the issue.

Ive tried to force eject using sudo eject & when I try to manually unmount it I get the following error both in cmd and manually:
Screenshot from 2021-05-15 10-35-52

Any help would be very grateful as i'm very much a noob to linux

---

### Post by tea for one on 2021-05-15
Your drive [COLOR="#0000FF"]/dev/sda[/COLOR] does not display any partitions?

Is this an external or internal drive?

Can you open a terminal and enter:-
```
lsblk -o name,mountpoint,label,size,fstype,model | egrep -v "^loop"

```

Please post the command and output in code tags (advanced reply and use #)

---

### Post by ajgreeny on 2021-05-15
Let's also see your /etc/fstab file and the output of command ```
sudo fdisk -l
```

Does the disk even have a partition table or is it brand new with nothing on it?

---

