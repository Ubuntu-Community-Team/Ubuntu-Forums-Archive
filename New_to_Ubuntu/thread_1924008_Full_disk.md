---
title: "Full disk"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by erik1001 on 2012-02-11
Hello. First, sorry for my English.
Last time I used my Ubuntu it notified me there is not enough free space, but that was all. Actually i checked the user folders and they were OK. After restarting the PC, it didn't boot the Unity shell and I was able to access the terminal only and then I found that "/dev/sdb6" is full at 100%. Now i don't know how to delete stuff from there because i can't access it via "cd" command. What i should do? Thanks for the help.

---

### Post by forrestcupp on 2012-02-11
If it is a Linux partition, and you know the names of programs that you could uninstall, you can **sudo apt-get --purge remove** those packages. If you just want to delete files and you're not familiar with the command line, you could always boot to a LiveCD and do it graphically with Nautilus. Just make sure you know what you're deleting, and don't manually delete anything that was installed with apt or the software center.

---

### Post by mcduck on 2012-02-11
Where is the sda6 mounted? You can't access the device directly, instead you access it through the location where it's mounted...

Anyway, could you run the following commands in a terminal and post the outputs here:

```
sudo fdisk -l
mount
df -h
```

(the first command lists all detected hard drives & partitions, the second one lists mounted filesystems, and the last one reports used & available space)

---

### Post by erik1001 on 2012-02-11
I deleted my inkscape and i'll try to do reboot again, let's see what'll happen...
And OMG, everything is ok, thank you very much. @mcduckm, thank you too. Now I'm going to resize this partition because i don't want to have such problem again. Thank you very much.

---

