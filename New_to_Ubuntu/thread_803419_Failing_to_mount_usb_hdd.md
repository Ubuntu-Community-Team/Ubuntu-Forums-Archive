---
title: "Failing to mount usb hdd"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-05-22
i was wondering if it was possible  for ubuntu to mount a external hard drive when it hasnt been safely removed from a windows system. i no all i have to do to get my hard drive to mount is safely remove it from windows but this is inconvenient because i am not dual bootin windows so i havta use a different computer to remove it. thanks in advance for all help given.

---

### Post by bumanie on 2008-05-22
A usb device will not mount in ubuntu if it has not been safely removed from windows. There is a program available in ubuntu that 'resets' the ntfs filesystem, but I can't remember its name and I am at work on a M$ only computer so I can't look anything up. If you go into synaptic and type ntfs into search, the tool will be in the list that comes up. Just highlight the various ntfs tools and then read what they do. You should see the one that may help you.

---

### Post by betterthanjordan79 on 2008-05-22
anybody have any idea what the program is that bumanie talks about here. i searched synaptic but i didnt really know what i was lookin for so i didnt download anything.

---

### Post by kansasnoob on 2008-05-22
I would think "ntfsprogs" although I've not used it for that exact purpose.

You can install ntfsprogs from synaptic and I believe it'll pull in the necessary libraries. Just open the search window in synaptic and type in ntfsprogs.

You can read more about ntfsprogs here:

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

It's proven quite useful to me in creating partitions that both windows and Ubuntu can read and write-to.

---

### Post by betterthanjordan79 on 2008-05-22
thanks kansasnoob-ill try that

---

### Post by sayakb on 2008-05-22
Why not simply force mount it just as the "Cannot mount volume" dialog box indicates.. At a terminal:
```
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

---

