---
title: "unable to mount new volume .."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by higatech on 2008-06-19
hi ... I am new to Ubuntu 
wen i connected my portable hardisk to my comp ...
it showed the following msg ..... plz help me out ....
[IMG]http://img104.imageshack.us/img104/9959/screenshotgnomemountfl0.png[/IMG]

plz help me out ........ plz reply soon ...

---

### Post by iaculallad on 2008-06-19
Open your terminal and run this command as pointed by the error message:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/New\ Volume -o force
```

---

### Post by bumanie on 2008-06-19
The error message is indicatiing that the disk with windows on it was not shut down incorrectly. To fix this either reboot it with windows and shut down correctly, force mount as indicated in the error message. Or install ntfsprogs > sudo apt-get install ntfsprogs and type > sudo ntfsfix /dev/sdb1 Once booted you should add the drive to /etc/fstab. As it is a ntfs disk, install > sudo apt-get install ntfs-3g and > sudo apt-get install ntfsconfig Then go to Applications --> System Tools and open the ntfs configuration tool and follow the instructions. Your drive will automatically be added to /etc/fstab.

---

### Post by higatech on 2008-06-19
gr88 ... that was very quick ...

---

