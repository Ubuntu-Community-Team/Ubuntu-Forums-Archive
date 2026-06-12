---
title: "cant delete files?"
date: 2024-06-03
forum: New to Ubuntu
---

### Post by oeyestvd on 2024-06-03
Hey guys, i opened a new thread because the subject was different.
So, this started because my ubuntu 20.04.2 had the disk full. i was trying to delete files but all i had was permission denied.

After, i unplugged this ssd disk from the ubuntu server and attached it to a laptop with ubuntu.
at first i wasnt seeing the partition, however after doing "$ sudo apt-get install lvm2" the partition popped up and i can see the folders.

But i cant delete folders or see everything on the disk. I wanted to know where is all the disk space occupied.
How can i do this?

Thanks!!

---

### Post by Rubi1200 on 2024-06-03
What is the output of these 2 commands (run them separately):
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs

```

When you post back here please reply using Go Advanced >> paste the output >> highlight and then click on the # icon on the toolbar to wrap with code tags.

Otherwise, it is really hard to read and analyze the data.

Thanks.

---

### Post by oeyestvd on 2024-06-04
[COLOR=#0C0D0E][FONT=-apple-system]thank you so much for your help Rubi1200. for safety reasons at the moment i am cloning the original ssd with TODO BACKUP (ease us) just to be safe and dont screw anything up. The Clone ssd is 1tb (original one is 500gb) another option would be to make the partition size bigger on the cloned ssd. more details soon, still 8 hours left on the clone process :\
after the clone is done i will make those commands and post the results.
Again thank you so much[/FONT][/COLOR]

---

