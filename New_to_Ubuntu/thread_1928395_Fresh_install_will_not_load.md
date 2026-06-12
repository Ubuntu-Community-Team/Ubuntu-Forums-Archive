---
title: "Fresh install will not load"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-02-20
when it (Ubuntu 11.10) finished installing and went to reboot, i selected Ubuntu in the grub and got:

run-init: /sbin/init: Exec format error

New install? It wont even load in recovery mode.....

---

### Post by muteXe on 2012-02-20
[http://www.linuxquestions.org/questions/linux-general-1/kernel-panic-not-syncing-attempted-to-kill-init-305582/](http://www.linuxquestions.org/questions/linux-general-1/kernel-panic-not-syncing-attempted-to-kill-init-305582/)

3 pages, but solution on the third page. Maybe.

---

### Post by theducksfan2010 on 2012-02-20
I installed it again - it completed install and I got the same error and it will not load in normal or recovery mode, this is making me want to throw Ubuntu 11.10 out for good.

---

### Post by theducksfan2010 on 2012-02-20
booting up with Crunchbang Live Cd to use gparted and wipe all partitions except my ntfs - Windows 7 still loads - When i set the mount point for my Ubuntu partition (Ext 4) i am going to set it at /

Any ideas?

---

### Post by sadaruwan12 on 2012-02-20
If your going to manually partition the hard drive then ok you can use your entire drive as your root (/) partition or other wise use the automatic option given to by the installer.

---

### Post by theducksfan2010 on 2012-02-20
I think there were residual errors left over from the failed two attempts to load where iit hung up on reboot. I tried to repartition the hd (minus the ntfs) and was not able to do all of it. I let the installer slide Ubuntu in next to Windows instead of manually picking a partition and it had two folders - of which I was able to drag Ubuntu to 108Gb and had to leave 8Gb unaccounted for. The install worked this time, but it was a 11.04 disk not 11.10 so I am running 
sudo apt-get update &
sudo apt-get upgrade 

then ready for the migration to 11.10

---

