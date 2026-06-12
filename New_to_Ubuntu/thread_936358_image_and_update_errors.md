---
title: "image and update errors"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by osteoblastic on 2008-10-02
Alright, I'm sort of an intermediate beginner, and I'm having a few problems that are no doubt related. I will try to relay them.

To fix a problem I was having with my updates (which gave an sub-process removal error with a linux-image), someone suggested I marked linux-image 2.6.24-16-generic for complete removal in the synaptic package manager. Like with the updates, I got an erorr saying the removal wasn't completed, error status 2 (same as the update manager error).

sudo apt-get update  finishes fine, no errors or complaints.

sudo apt-get install -f gives me:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-16-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 15.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117160 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
/usr/sbin/update-initramfs: 516: mkinitramfs: not found
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now my Add/Remove Applications is telling me I have a major error:
"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

I did some searching and none of what I found relates to my particular issue and packages. Can someone give me some guidance? Tests to run or things to check for?

---

### Post by shearn89 on 2008-10-03
wow... looks like you managed to remove some really crucial stuff. Specifically, the system.map file for your kernel, and mkinitramfs.

The system.map file contains all the variables used by the system (i think), and the mkinitramfs program creates the image used by the system when booting. Without it, you'll get lots of problems.

I'm not sure what to do about system.map, but if you install mkinitramfs you should get somewhere. Try and do:
```

sudo apt-get install initramfs-tools

```
And if that doesn't work, post anything you get here.

---

### Post by osteoblastic on 2008-10-03
> **shearn89 said:**
> wow... looks like you managed to remove some really crucial stuff. Specifically, the system.map file for your kernel, and mkinitramfs.

The system.map file contains all the variables used by the system (i think), and the mkinitramfs program creates the image used by the system when booting. Without it, you'll get lots of problems.

I'm not sure what to do about system.map, but if you install mkinitramfs you should get somewhere. Try and do:
```

sudo apt-get install initramfs-tools

```
And if that doesn't work, post anything you get here.


Thanks much for the reply! It seems to lead me to the same place, unfortunately:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
initramfs-tools is already the newest version.
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-16-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 15.8MB disk space will be freed.
Do you want to continue [Y/n]? 


I can't seem to get around removing that linux-image, and I can't reinstall it, either. If I have a more current version than that one, why is it being so huffy about it? And how did trying to remove that mess with my system map? Time to go do some more research...

---

### Post by shearn89 on 2008-10-03
hmmm. You could try forcing a reinstall of initramfs, i think the code is:
```

sudo apt-get install --reinstall initramfs-tools

```

Apart from that, i'd have to go with a backup of important stuff and customised system fils, and a reinstall...

---

### Post by Ryadt on 2008-10-03
Try ```
sudo apt-get autoclean
``````
sudo apt-get autoremove
```

---

### Post by cariboo on 2008-10-03
It looks like you manually remove some files, instead of using the package manager to remove them. Open Sysnaptic and got to Edit-->Fix Broken Packages, and do what the program suggests.

Jim

---

