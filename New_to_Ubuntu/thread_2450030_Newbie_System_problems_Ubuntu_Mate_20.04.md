---
title: "Newbie: System problems Ubuntu Mate 20.04"
date: 2020-09-06
forum: New to Ubuntu
---

### Post by sabyuntu on 2020-09-06
Hi,

I am new to Ubuntu Mate and facing some issues, please see if you know what to do:

1. After waking up from sleep, the desktop is in place, **but applications does not launch**. If I go into the System monitor, most of the processes are still sleeping. Logout ends in a error in black screen, **"Can't write log entries" or something**. So, restart is the only solution. Not consistent behavior, happens once in a while. 

2. Copying files to USB often fails. Larger files, I was copying 10, 2 GB files into the USB drives. It fails after copying a few files, "Input/output error". **Actually Caja hangs.** This is not consistent, if I start again, it might work. This not a problem with the USB drive, it works perfectly on my other machines. Doing this, it has deleted many of my files by error, though I only copied the files (not moved), files were not in the USB drive, nor in the HD folder. 

3. File volume icons like: root, and File systems icon appears in the desktop after restart. Home button is permanently there. Not after every restart. Can't right click and Unmount. Can't delete the icons. 

I have updated and upgraded all the system / software. If you have experienced these issues, please help me to sort out.

---

### Post by Impavidus on 2020-09-06
The sleep status of applications is not related to the sleep status of the OS. A sleeping application just means it's waiting for someting, like an expiring timer or input. When you write "restart is the only solution," have you really tried everything, including SysRq+REISUB? You may not be aware of it.

I/O errors during file copy and files disappearing suggest a broken hard drive. I suggest you check the health of your hard drive, but keep in mind that even if it passes the check, it's not guaranteed your hard drive is OK. Have you got backups of all your important files? Backups are mandatory, no matter what OS you use.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by mastablasta on 2020-09-08
what is the file system on USB drive? FAT32?

---

