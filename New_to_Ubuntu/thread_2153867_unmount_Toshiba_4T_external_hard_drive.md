---
title: "unmount Toshiba 4T external hard drive"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by lucyi on 2013-06-12
Ubuntu 10.04 (seriously, I know I should upgrade) :redface:
When I right click on desktop icon for the Toshiba 4T external HDD, choose Safely Remove Drive, I got an error message that the drive could not be stopped.  How do I get around this?  In the long search in these forums for an answer, enough time passed and I tried it again.  I think it was successful.  I did not get an error message, the icon disappeared from the desktop and I unplugged from the usb port.  What if I want to unmount the hardware in a hurry?  I am not really good at using the terminal commands, but if you give me the correct input, I will write it down.

---

### Post by ajgreeny on 2013-06-12
```
sudo umount /dev/sd??
``` where sd?? is your disk or partition that's mounted.  If the disk is in use, even if you are just looking at a folder on it in a file manager, you may get that error message you saw, so shut down anything that may be using the partition/disk and the error may disappear.

---

### Post by lucyi on 2013-06-12
Thank you.

---

