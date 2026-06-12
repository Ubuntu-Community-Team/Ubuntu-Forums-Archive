---
title: "External hard drive writing permissions issue"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Binary.tobis on 2008-07-10
So I am having trouble writing files and deleting files on my external hard drive which I am connection through USB to my toshiba satellite. I posted a while back about it and someone helped me edit a text file somewhere which fixed it. This stopped working after a while though and I am not sure why. :( I was hoping someone could walk me through how to give myself permission to write to the external hard drive. Thanks in advance!

---

### Post by freak42 on 2008-07-10
What format is used on your external disk?
Was the file /etc/fstab?
What did you change in the file?

---

### Post by superprash2003 on 2008-07-10
if its an ntfs drive then you could try installing ntfs-3g

---

### Post by Binary.tobis on 2008-07-12
I added the line ```
/dev/sda1       /media/external  ntfs-3g  defaults,auto,rw,umask=007   0   1
```

to the end of my fstab file, then it displayed the message ```
[mntent]: warning: no final newline at the end of /etc/fstab
mount: only root can mount /dev/sda1 on /media/external.
```

when I tried to access the external drive. I just need to transfer one set of files too. -_-

---

### Post by freak42 on 2008-07-13
make sure you have a newline at the end of the file: that is the cursor can go right one line below the line with your information, if not, then press enter once at the end of your line...

are you sure you want to mount your external drive as /dev/sda1 ?? This is usually your internal drive (is there another line in your fstab starting with /dev/sda1)? If there is you need another (unique identifier: you can try /dev/sdb1, if it is not taken)

---

### Post by ChameleonDave on 2008-07-13
> **Binary.tobis said:**
> So I am having trouble writing files and deleting files on my external hard drive which I am connection through USB to my toshiba satellite. I posted a while back about it and someone helped me edit a text file somewhere which fixed it. This stopped working after a while though and I am not sure why. :( I was hoping someone could walk me through how to give myself permission to write to the external hard drive. Thanks in advance!
Please plug the device in and do this following in a terminal:

```

cat /etc/fstab
sudo blkid

```

Post the results here.

---

