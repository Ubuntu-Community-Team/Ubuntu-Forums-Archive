---
title: "Broken package always trying to install"
date: 2016-06-13
forum: New to Ubuntu
---

### Post by alex549 on 2016-06-13
Hello!  I was trying to install a bluetooth driver from a post I found however it appears to not have worked, and now whenever I attempt to install new programs, it always tries to reinstall this program.  Thoughts?  Also, whats the best way to post output of terminal so it looks better?  Thanks!  ```
  sudo apt-get install gedit Reading package lists... Done Building dependency tree      
  Reading state information... Done gedit is already the newest version (3.18.3-0ubuntu4). gedit set to manually installed. 0 upgraded, 0 newly installed, 0 to remove and 145 not upgraded. 1 not fully installed or removed. 
After this operation, 0 B of additional disk space will be used. Do you want to continue? [Y/n] y Setting up ath10k-dkms (1.0) ... Removing old ath10k-1.0 DKMS files...  ------------------------------ Deleting module version: 1.0 completely from the DKMS tree. ------------------------------ Done. Loading new ath10k-1.0 DKMS files... First Installation:
 checking all kernels... Building only for 4.4.0-24-generic Building for architecture x86_64 Building initial module for 4.4.0-24-generic ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/ath10k-dkms.0.crash' 
Error! Bad return status for module build on kernel: 4.4.0-24-generic (x86_64) Consult /var/lib/dkms/ath10k/1.0/build/make.log for more information. dpkg: error processing package ath10k-dkms (--configure):  subprocess installed post-installation script returned error exit status 1 
Processing triggers for initramfs-tools (0.122ubuntu8) ... update-initramfs: Generating /boot/initrd.img-4.4.0-24-generic Errors were encountered while processing:  ath10k-dkms E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by QDR06VV9 on 2016-06-13
By using Code Tags 
and placing input in between them.
See My Signature for more info.
Regards

---

### Post by X-RED_Tech on 2016-06-13
Can you post the post you were following? It's probably easier to spot what might have gone wrong with it than you remembering what you did...

Possibly something to do with the installation of ath10, a driver for an Atheros card?

---

### Post by JayKay3OOO on 2016-06-13
sudo apt-get install - you may need to add -f

sudo apt-get install --fix-missing - as it says

sudo apt-get remove 'package name' - removed the package use & possibly followed by the install command.

sudo apt-get autoremove - removed un-needed packages  

Some, all or none of that may work. Good luck.

---

### Post by alex549 on 2016-06-13
Ah right.    ```
sudo apt-get remove 'package name' - removed the package use & possibly followed by the install command.
``` worked well!  Thanks guys

---

### Post by oldrocker99 on 2016-06-13
Since you seem to have had your problem fixed, please mark this thread as [SOLVED].

---

### Post by Mr Wonderfull on 2016-06-16
Thank you it worked for me.

---

