---
title: "How do I reinstall an entire ubuntu partition without affecting my other partitions?"
date: 2014-09-07
forum: New to Ubuntu
---

### Post by mike_g2 on 2014-09-07
On my system I have 4 partitions:


[LIST]
[*]Ubuntu 14 LTS
[*]Windows 7
[*]A file partition (shared by ubuntu and windows)
[*]swap
[/LIST]

I want to reinstall ubuntu becuase I have messed it up and think it will be the fastest way to solve it, however I want to ensure that my other partitions (Well, mainly the file store and windows) are not altered in any way. How do I go about this safely?

---

### Post by Mark Phelps on 2014-09-07
Good question ... so, first of all, do NOT choose the "replace" option when doing the install.  Doing so will erase the ENTIRE DRIVE!  It tells you this, but not very well, and has left many folks with a wiped-out Windows install as a result.

You should back up the Windows partitions, if you want to be absolutely safe, to an external drive.  A good app for doing this (in Windows) is Macrium Reflect.

To reinstall Ubuntu, then do the following:
1) Boot into the install media, choose Try Ubuntu, and then run GParted to erase the Ubuntu partition.
2) When that is done, reboot using the install media and this time, choose Install -- but use the Something Else option -- being sure to select the previously erased Ubuntu partition.

---

### Post by nerdtron on 2014-09-07
You don't have to erase the Ubuntu partition in gparted.
1. Since you already have your partitions in place, choose "Somethins Else" on the ubuntu installer.
2. Assign the Ubuntu partition with a mount point of "/", make it filesystem type ext4 and check the format drive option.
3. Assign the swap partition as "swap area".

Before you proceed you can post the screenshot of the installer screen here so we can see if everything is fine.

Note: Do not select,  alter, assign, format, or mount any of the windows partitions just to be on the safe side.

---

