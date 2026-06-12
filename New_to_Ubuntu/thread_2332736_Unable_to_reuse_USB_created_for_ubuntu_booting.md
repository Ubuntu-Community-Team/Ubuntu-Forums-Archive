---
title: "Unable to reuse USB created for ubuntu booting"
date: 2016-08-03
forum: New to Ubuntu
---

### Post by vinayrai111 on 2016-08-03
Hi, I am new to Ubuntu (as forum said).
I installed Ubuntu today only. I want to install Windows also, so to partition my disk, I again created a bootable disk of Ubuntu 16.04.01 iso file using "startup disk creator" . Then I booted from usb pendrive and used Gparted to partition disks, created a new volume for Windows.
But now I am unable to use that bootable USB that I created, can't format it, tried formatting it in Windows also but didn't work.
Look at the attached image, this is what "disks" showing.

Please let me know, how can I reuse this pendrive and if possible also tell me that how can I make bootable Windows usb on this pendrive.

Thanks in advance.

---

### Post by Bucky Ball on 2016-08-03
Welcome. See the gear button just under the partitions, third one on the right? Click it and you should be able to delete the partition.

You're other option is to do exactly as you did with the USB live session: use Gparted. Install it from the repositories (whatever package manager you are using or the terminal) and obliterate the partitions on the USB dongle. 

Goes without saying, but *double/triple* check you are deleting the partitions on the USB dongle, *not* the hard drive. The drive you are looking at in the screen shot says 7.7Gb size, so presuming you're in the right place. ;)

---

### Post by vinayrai111 on 2016-08-03
Tried it all but now pendrive is showing "read-only", tried to format it via "disks" but formatting didn't help.
I think it is a lost cause now, any suggestion.

---

### Post by Bucky Ball on 2016-08-03
You have it unmounted? Try installing Gparted from the repositories, select the USB from the drop down menu at the top right, right click the partition and unmount it if it is mounted. Try deleting it then.

---

### Post by arochester on 2016-08-03
[https://www.unixmen.com/how-to-format-usb-drive-in-the-terminal/](https://www.unixmen.com/how-to-format-usb-drive-in-the-terminal/) ?

---

