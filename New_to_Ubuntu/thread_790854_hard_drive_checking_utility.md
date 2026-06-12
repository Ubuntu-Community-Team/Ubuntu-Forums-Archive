---
title: "hard drive checking utility"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by hazman on 2008-05-11
is there any software out there to check and repair h/drives similar to scandisk in windows or defrag.i was using update manager when half way thru the system froze and h/drive started make noises or is hard drive buggered

---

### Post by RJARRRPCGP on 2008-05-11
Probably HDD failure. Sorry. :(

---

### Post by Tomatz on 2008-05-11
Sounds like drive faliure.

But if you are curious you can fix filesystem errors with the gparted live cd:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Burn the .iso to disc and boot with it in the drive.

_P.s _

If you can actually boot into ubuntu open a terminal and type:

> sudo touch /forcefsck

Then reboot, it will force a drive check.

---

### Post by macaholic on 2008-05-11
> **hazman said:**
> is there any software out there to check and repair h/drives similar to scandisk in windows or defrag.i was using update manager when half way thru the system froze and h/drive started make noises or is hard drive buggered
You can use gparted to check and repair disks.```
sudo apt-get install gparted
```
However you won't be able to do it to the partition you are currently on, so you will ahve to boot into a live cd and check it.

---

### Post by thisiam on 2008-05-11
check the hardrive manufacturer, i know seagate has tools to check their harddrives.

---

### Post by psusi on 2008-05-15
If you want to check the physical disc for defects, you can install the smartmontools package.

sudo apt-get install smartmontools
sudo smartctl -A /dev/sda
sudo smartctl -t long /dev/sda
sudo smartctl -l selftest /dev/sda

The first command installs the package.  The second gets some statistics from the drive.  The third asks the drive to begin a full disk media test, which can take quite some time.  Eventually when it finishes, you can see the results of the test from the last command.

---

### Post by SneakyBooBoo on 2008-05-15
do i need to defrag an ext3 partition? and if it is possible, what can i use to do it. i checked in synaptic for something but couldnt find.

---

### Post by Oldsoldier2003 on 2008-05-15
> **SneakyBooBoo said:**
> do i need to defrag an ext3 partition? and if it is possible, what can i use to do it. i checked in synaptic for something but couldnt find.

nope :)

---

