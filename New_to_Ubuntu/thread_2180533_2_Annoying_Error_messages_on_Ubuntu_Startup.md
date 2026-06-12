---
title: "2 Annoying Error messages on Ubuntu Startup"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by James_Cracknell on 2013-10-13
Hi, when I was trying to mount my music from windows onto ubuntu I made the mistake of mounting the wrong folders and now I get 2 error messages at startup that say the following :

1. An error occoured while mounting /media/system
2. An error occoured while mounting /mnt/windows

Is there any way to make these go away without having to press s for skip every startup for each of the 2 errors?
Many thanks in advance.

---

### Post by tgalati4 on 2013-10-13
Open a terminal.  What is the output of:

```
cat /etc/fstab
```

Any extrananous entries in [fstab]("https://help.ubuntu.com/community/Fstab") (file system table) will show errors.  You can delete them (or comment them out) and reboot.

---

### Post by James_Cracknell on 2013-10-13
this is the output as requested:

uboo@ubuntu:~$ cat /etc/fstab
UUID=60A823AFA82382A0  /host        ntfs-3g  defaults              0  0  
UUID=78A60E2CA60DEC06  /media/Data  ntfs-3g  noauto,owner          0  0  
UUID=967CF34F7CF3291F /media/SYSTEM RESERVED ntfs-3g defaults 0 0
/dev/sda2              /media/sda2  ntfs     nls=iso8859-1,noauto  0  0
/dev/sda3             /mnt/windows  ntfs     defaults 0  0             
uboo@ubuntu:~$ 


I'm guessing it's the bottom 2 lines of the output but how do I delete them?

Again Many Thanks in advance :)

---

### Post by sandyd on 2013-10-13
> **James_Cracknell said:**
> this is the output as requested:

uboo@ubuntu:~$ cat /etc/fstab
UUID=60A823AFA82382A0  /host        ntfs-3g  defaults              0  0  
UUID=78A60E2CA60DEC06  /media/Data  ntfs-3g  noauto,owner          0  0  
UUID=967CF34F7CF3291F /media/SYSTEM RESERVED ntfs-3g defaults 0 0
/dev/sda2              /media/sda2  ntfs     nls=iso8859-1,noauto  0  0
/dev/sda3             /mnt/windows  ntfs     defaults 0  0             
uboo@ubuntu:~$ 


I'm guessing it's the bottom 2 lines of the output but how do I delete them?

Again Many Thanks in advance :)
```

sudo nano /etc/fstab
```

Remove ```

/dev/sda3             /mnt/windows  ntfs     defaults 0  0
UUID=967CF34F7CF3291F /media/SYSTEM RESERVED ntfs-3g defaults 0 0
```

Press control+x to save
Btw, fstab doesn't support spaces in paths - which is why the line containing UUID would not work even if the drive was to be mounted

---

### Post by tgalati4 on 2013-10-14
You can use Control-k to delete the line that the cursor is on.  You can also put a # in front of the line to comment it out.  You might want to keep a record of it in case you need to make a similar mount in the future.  This way you have an idea of what the syntax is for the mount.

---

