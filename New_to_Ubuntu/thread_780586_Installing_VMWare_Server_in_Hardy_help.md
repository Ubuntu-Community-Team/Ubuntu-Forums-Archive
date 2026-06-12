---
title: "Installing VMWare Server in Hardy help"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by kahram.yoon on 2008-05-03
TRYING TO:
Installing VMWare Server in Hardy
This is a cleaned up copy of the instructions for installing the VMWare Server from tar.gz found at [http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976) with a correction thanks to forrestallen. Since the Hardy Beta forums are now locked I thought it might be best to make a copy here to allow further discussion if needed.


First install the packages needed by vmware.

Code:

sudo apt-get install build-essential linux-headers-`uname -r`
sudo apt-get install xinetd

for 64bit installs also install the ia32-libs
Code:

sudo apt-get install ia32-libs

Additionally I recommend installing the linux-header metapackage appropriate to your kernel. "sudo apt-get install linux-headers-generic" for desktops in the standard kernel and "sudo apt-get install linux-headers-server" for server installs. This makes it easier down the road, automatically pulling down the headers if the kernel gets updated.

next download vmware server and expand it out somewhere
Code:

tar -xvzf VMware-server-1.0.5-80187.tar.gz
COPIED THIS INTO CONSOLE AND THIS IS WHAT COMES OUT... DONT KNOW WHY

-desktop:~$ tar -xvzf VMware-server-1.0.5-80187.tar.gz
tar: VMware-server-1.0.5-80187.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

whats wrong? how do i fix it?

---

### Post by Monicker on 2008-05-03
Are you positive you are in the directory to which you downloaded the file when you try to extract it?

If you do an ls, do you see the file?

---

### Post by CloudFX on 2008-05-03
Try doing it all from the VMWare site:
[http://www.vmware.com/products/server/](http://www.vmware.com/products/server/)

---

### Post by unbuntued on 2008-05-03
> **kahram.yoon said:**
> TRYING TO:
tar -xvzf VMware-server-1.0.5-80187.tar.gz
COPIED THIS INTO CONSOLE AND THIS IS WHAT COMES OUT... DONT KNOW WHY

-desktop:~$ tar -xvzf VMware-server-1.0.5-80187.tar.gz
tar: VMware-server-1.0.5-80187.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

whats wrong? how do i fix it?

The file you are trying to extract 'VMware-server-1.0.5-80187.tar.gz' is not in your current directory. If you're too lazy to download the file manually and move it to your current folder (or any other folder), just execute the following (it will download the file for you than extract it):
```
wget http://download3.vmware.com/software/vmserver/\
VMware-server-1.0.5-80187.tar.gz

tar -xzvf   VMware-server-1.0.5-80187.tar.gz
```

---

