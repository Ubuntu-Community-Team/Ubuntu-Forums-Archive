---
title: "Broken Count &gt;0"
date: 2018-04-10
forum: New to Ubuntu
---

### Post by thomasc5 on 2018-04-10
I was trying to update my Ubuntu 14.04 LTS last night. Somehow the update failed and now there is a circular stop sign icon at the top right hand corner.

I've tried "sudo apt-get install --fix-broken"  (from Google) but it doesn't seem to help. (a disk full error?)

I'm an absolute beginner. Hope someone could help. Thank you

-------------------------------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.13.0-144-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-144-generic
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
6 not fully installed or removed.
Need to get 0 B/693 kB of archives.
After this operation, 13.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y

(Reading database ... 2271963 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.13.0-144-generic_3.13.0-144.193_i386.deb ...
Unpacking linux-headers-3.13.0-144-generic (3.13.0-144.193) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-144-generic_3.13.0-144.193_i386.deb (--unpack):
error creating symbolic link `./usr/src/linux-headers-3.13.0-144-generic/include/linux/plist.h': No space left on device
No apport report written because the error message indicates a disk full error
 Errors  encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-144-generic_3.13.0-144.193_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

-------------------------------------------------------------

---

### Post by Bashing-om on 2018-04-10
thomasc5; Hello - Welcome to the forum .

Yepper :
> 
 No space left on device


> 
dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-144-generic_3.13.0-144.193_i386.deb (--unpack):
error creating symbolic link `./usr/src/linux-headers-3.13.0-144-generic/include/linux/plist.h': No space left on device
No apport report written because the error message indicates a disk full error


With the suppostion that the issue is /boot full -
verify the disk usage ->
post back - between code tags - the outputs of terminal commands:
```

df -h
df -i
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post1277616](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post1277616)

then we see what can be done.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Impavidus on 2018-04-10
As this happened when trying to create a symbolic link for a headers package, I suspect you ran out of inodes.

On your hard drive, you have a table of all files and directories with some basic properties, like owner, permissions and actual location on the hard drive of the contents. Every entry in this table is called an inode and you have a finite number of them. So your file system doesn't just have a limit on the total size of all files and directories, but also on their number. linux-headers-* packages contain a lot of files and over the life of 14.04 you may have accumulated a lot of them without regular cleanup. It shouldn't be hard to solve. Just post the output of Bashing-om's commands and we can help you further.

You probably have a lot of old kernel packages too, consuming disk space.

---

### Post by thomasc5 on 2018-04-13
> **Bashing-om said:**
> 

Bashing-om:

With the suppostion that the issue is /boot full -
verify the disk usage ->
post back - between code tags - the outputs of terminal commands:
```

df -h
df -i
dpkg -l | grep linux-

```



Bashing-om:
Thanks for your help.
I think I'd need to post the  "dpkg -l | grep linux-" terminal output in the next reply. The forum bot said my reply is too long.(?)


df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            993M  4.0K  993M   1% /dev
tmpfs           201M  1.1M  200M   1% /run
/dev/sda5        35G   26G  7.7G  77% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none           1003M   64M  940M   7% /run/shm
none            100M   28K  100M   1% /run/user

```

df -i
```

Filesystem      Inodes   IUsed  IFree IUse% Mounted on
udev            215073     505 214568    1% /dev
tmpfs           220099     489 219610    1% /run
/dev/sda5      2313808 2305599   8209  100% /
none            220099       2 220097    1% /sys/fs/cgroup
none            220099       1 220098    1% /run/lock
none            220099      43 220056    1% /run/shm
none            220099      23 220076    1% /run/user

```

---

### Post by wildmanne39 on 2018-04-13
You can post it to pastebin then post the link here:

[https://pastebin.com/](https://pastebin.com/)

---

### Post by thomasc5 on 2018-04-13
> **wildmanne39 said:**
> You can post it to pastebin then post the link here:

[https://pastebin.com/](https://pastebin.com/)

Yes, thank you. :)
Tried to attach the output text file, but it said it's over the 19.5k size limit.  


dpkg -l | grep linux-
[https://pastebin.com/TRNMe6sA](https://pastebin.com/TRNMe6sA)

---

### Post by Impavidus on 2018-04-14
OK, you ran out of inodes because you have hundreds of old packages.

First some manual cleanup to make apt happy again:```
sudo dpkg --purge linux-headers-3.13.0-{32..37}{,-generic} linux-image{,-extra}-3.13.0-{32..37}-generic
```
That should give some breathing room.

Next```
sudo apt-get install -f
```to get the partially installed packages installed. That will put package management back into a clean state.

Now to clean up disk space, you can remove a lot of old packages. I'm not sure if this was already implemented in 14.04, but you can try:```
sudo apt-get autoremove --purge
```
That may remove all the old kernel and header packages. It will take a while. A long while.

If that doesn't work, it must be possible to come up with some nice one-liner that does the same.

---

### Post by thomasc5 on 2018-04-15
> **Impavidus said:**
> OK, you ran out of inodes because you have hundreds of old packages.

First some manual cleanup to make apt happy again:```
sudo dpkg --purge linux-headers-3.13.0-{32..37}{,-generic} linux-image{,-extra}-3.13.0-{32..37}-generic
```
That should give some breathing room.



The little red stop sign icon is gone. Thank you!   :D
  
While the "**sudo dpkg --purge linux-headers...**" took about 5 minutes to run,  the "**sudo apt-get autoremove --purge**"  was almost instant:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.

```

Does it mean the disk space has not been freed up?  Btw, how often should I run this "purge" command? Where can I find out more about it?

---

### Post by deadflowr on 2018-04-15
> Does it mean the disk space has not been freed up? Btw, how often should I run this "purge" command? Where can I find out more about it?
You need to run the df -i command again to see if you have freed up some inodes.

---

### Post by Impavidus on 2018-04-15
It seems that the first part worked, so you have some headroom and the package manager is happy again. But you still have hundreds of old packages, using over a million inodes and about 10GB disk space.

Reboot and verify you're running the latest kernel:```
uname -r
```It think it should now show 3.13.0-144.

I've some difficulty finding a good one-liner that I can verify to be safe, but I think the command at the end of the top answer [here]("https://askubuntu.com/questions/401581/bash-one-liner-to-delete-only-old-kernels") (the answer by Malte Skoruppa) is OK. Maybe somebody will pop in with a better one. I vaguely remember there's some limitation on number of command line arguments, so let's hope we don't hit that limit.

In more recent versions of Ubuntu it has become easier and if you don't wait too long before removing old stuff, it isn't really a problem to do it manually.

Then, let's again see the output of```
df -h
df -i
dpkg -l | grep linux-
```
Usually, I remove old kernels right after installing a new one, but doing it once every few months or so should suffice.

---

### Post by thomasc5 on 2018-04-17
> **deadflowr said:**
> You need to run the df -i command again to see if you have freed up some inodes.

deadflowr, 

```

Filesystem      Inodes   IUsed  IFree IUse% Mounted on
udev            215073     505 214568    1% /dev
tmpfs           220099     489 219610    1% /run
/dev/sda5      2313808 2153402 160406   94% /
none            220099       2 220097    1% /sys/fs/cgroup
none            220099       1 220098    1% /run/lock
none            220099      26 220073    1% /run/shm
none            220099      24 220075    1% /run/user

```

---

### Post by thomasc5 on 2018-04-17
> **Impavidus said:**
> It seems that the first part worked, so you have some headroom and the package manager is happy again. But you still have hundreds of old packages, using over a million inodes and about 10GB disk space.

Reboot and verify you're running the latest kernel:```
uname -r
```It think it should now show 3.13.0-144.



Impavidus,
Yes, the kernel is "3.13.0-144-generic"


df -h
```

Filesystem      Size  Used Avail Use% Mounted on
udev            993M  4.0K  993M   1% /dev
tmpfs           201M  1.1M  200M   1% /run
/dev/sda5        35G   25G  8.7G  74% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none           1003M   53M  951M   6% /run/shm
none            100M   32K  100M   1% /run/user

```


df -i
```

Filesystem      Inodes   IUsed  IFree IUse% Mounted on
udev            215073     505 214568    1% /dev
tmpfs           220099     489 219610    1% /run
/dev/sda5      2313808 2153446 160362   94% /
none            220099       2 220097    1% /sys/fs/cgroup
none            220099       1 220098    1% /run/lock
none            220099      28 220071    1% /run/shm
none            220099      24 220075    1% /run/user

```


dpkg -l | grep linux-
[https://pastebin.com/Wc4NHf65](https://pastebin.com/Wc4NHf65)


Thank you

---

### Post by Impavidus on 2018-04-17
It's still almost full, so try this one:```
dpkg -l | grep linux- | awk '/^ii/{print $2}' | egrep '[0-9]+\.[0-9]+\.[0-9]+' | egrep -v '3.13.0-144' | egrep -v '3.13.0-143' | xargs sudo apt-get purge
```That should remove all old headers and kernels, unless you get some buffer overflow because of the large number of packages you try to remove at once. But I expect it will work. It will keep the headers and kernel for 3.13.0-143 and 3.13.0-144, the latest and one spare. It will take some time.

Then check again. Did you get your disk space back and a lot of packages (256 I think) removed?

---

### Post by thomasc5 on 2018-04-20
> **Impavidus said:**
> It's still almost full, so try this one:```
dpkg -l | grep linux- | awk '/^ii/{print $2}' | egrep '[0-9]+\.[0-9]+\.[0-9]+' | egrep -v '3.13.0-144' | egrep -v '3.13.0-143' | xargs sudo apt-get purge
```

I'm unable to remove the packages, as when it prompts "Do you want to continue? [Y/n]" , it automatically defaults to "Abort" and quits. :confused:


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.13.0-100* linux-headers-3.13.0-100-generic*
  linux-headers-3.13.0-101* linux-headers-3.13.0-101-generic*
  linux-headers-3.13.0-103* linux-headers-3.13.0-103-generic*
  linux-headers-3.13.0-105* linux-headers-3.13.0-105-generic*
  linux-headers-3.13.0-106* linux-headers-3.13.0-106-generic*
  linux-headers-3.13.0-107* linux-headers-3.13.0-107-generic*
  linux-headers-3.13.0-108* linux-headers-3.13.0-108-generic*
  linux-headers-3.13.0-110* linux-headers-3.13.0-110-generic*
  linux-headers-3.13.0-112* linux-headers-3.13.0-112-generic*
  linux-headers-3.13.0-113* linux-headers-3.13.0-113-generic*
  linux-headers-3.13.0-115* linux-headers-3.13.0-115-generic*
  linux-headers-3.13.0-116* linux-headers-3.13.0-116-generic*
  linux-headers-3.13.0-117* linux-headers-3.13.0-117-generic*
  linux-headers-3.13.0-119* linux-headers-3.13.0-119-generic*
  linux-headers-3.13.0-121* linux-headers-3.13.0-121-generic*
  linux-headers-3.13.0-123* linux-headers-3.13.0-123-generic*
  linux-headers-3.13.0-125* linux-headers-3.13.0-125-generic*
  linux-headers-3.13.0-128* linux-headers-3.13.0-128-generic*
  linux-headers-3.13.0-129* linux-headers-3.13.0-129-generic*
  linux-headers-3.13.0-132* linux-headers-3.13.0-132-generic*
  linux-headers-3.13.0-133* linux-headers-3.13.0-133-generic*
  linux-headers-3.13.0-135* linux-headers-3.13.0-135-generic*
  linux-headers-3.13.0-137* linux-headers-3.13.0-137-generic*
  linux-headers-3.13.0-139* linux-headers-3.13.0-139-generic*
  linux-headers-3.13.0-141* linux-headers-3.13.0-141-generic*
  linux-headers-3.13.0-142* linux-headers-3.13.0-142-generic*
  linux-headers-3.13.0-39* linux-headers-3.13.0-39-generic*
  linux-headers-3.13.0-40* linux-headers-3.13.0-40-generic*
  linux-headers-3.13.0-43* linux-headers-3.13.0-43-generic*
  linux-headers-3.13.0-44* linux-headers-3.13.0-44-generic*
  linux-headers-3.13.0-45* linux-headers-3.13.0-45-generic*
  linux-headers-3.13.0-46* linux-headers-3.13.0-46-generic*
  linux-headers-3.13.0-48* linux-headers-3.13.0-48-generic*
  linux-headers-3.13.0-49* linux-headers-3.13.0-49-generic*
  linux-headers-3.13.0-51* linux-headers-3.13.0-51-generic*
  linux-headers-3.13.0-52* linux-headers-3.13.0-52-generic*
  linux-headers-3.13.0-53* linux-headers-3.13.0-53-generic*
  linux-headers-3.13.0-54* linux-headers-3.13.0-54-generic*
  linux-headers-3.13.0-55* linux-headers-3.13.0-55-generic*
  linux-headers-3.13.0-57* linux-headers-3.13.0-57-generic*
  linux-headers-3.13.0-58* linux-headers-3.13.0-58-generic*
  linux-headers-3.13.0-61* linux-headers-3.13.0-61-generic*
  linux-headers-3.13.0-62* linux-headers-3.13.0-62-generic*
  linux-headers-3.13.0-63* linux-headers-3.13.0-63-generic*
  linux-headers-3.13.0-65* linux-headers-3.13.0-65-generic*
  linux-headers-3.13.0-66* linux-headers-3.13.0-66-generic*
  linux-headers-3.13.0-67* linux-headers-3.13.0-67-generic*
  linux-headers-3.13.0-68* linux-headers-3.13.0-68-generic*
  linux-headers-3.13.0-70* linux-headers-3.13.0-70-generic*
  linux-headers-3.13.0-71* linux-headers-3.13.0-71-generic*
  linux-headers-3.13.0-74* linux-headers-3.13.0-74-generic*
  linux-headers-3.13.0-76* linux-headers-3.13.0-76-generic*
  linux-headers-3.13.0-77* linux-headers-3.13.0-77-generic*
  linux-headers-3.13.0-79* linux-headers-3.13.0-79-generic*
  linux-headers-3.13.0-83* linux-headers-3.13.0-83-generic*
  linux-headers-3.13.0-85* linux-headers-3.13.0-85-generic*
  linux-headers-3.13.0-86* linux-headers-3.13.0-86-generic*
  linux-headers-3.13.0-87* linux-headers-3.13.0-87-generic*
  linux-headers-3.13.0-88* linux-headers-3.13.0-88-generic*
  linux-headers-3.13.0-92* linux-headers-3.13.0-92-generic*
  linux-headers-3.13.0-93* linux-headers-3.13.0-93-generic*
  linux-headers-3.13.0-95* linux-headers-3.13.0-95-generic*
  linux-headers-3.13.0-96* linux-headers-3.13.0-96-generic*
  linux-headers-3.13.0-98* linux-headers-3.13.0-98-generic*
  linux-image-3.13.0-100-generic* linux-image-3.13.0-101-generic*
  linux-image-3.13.0-103-generic* linux-image-3.13.0-105-generic*
  linux-image-3.13.0-106-generic* linux-image-3.13.0-107-generic*
  linux-image-3.13.0-108-generic* linux-image-3.13.0-110-generic*
  linux-image-3.13.0-112-generic* linux-image-3.13.0-113-generic*
  linux-image-3.13.0-115-generic* linux-image-3.13.0-116-generic*
  linux-image-3.13.0-117-generic* linux-image-3.13.0-119-generic*
  linux-image-3.13.0-121-generic* linux-image-3.13.0-123-generic*
  linux-image-3.13.0-125-generic* linux-image-3.13.0-128-generic*
  linux-image-3.13.0-129-generic* linux-image-3.13.0-132-generic*
  linux-image-3.13.0-133-generic* linux-image-3.13.0-135-generic*
  linux-image-3.13.0-137-generic* linux-image-3.13.0-139-generic*
  linux-image-3.13.0-141-generic* linux-image-3.13.0-142-generic*
  linux-image-3.13.0-39-generic* linux-image-3.13.0-40-generic*
  linux-image-3.13.0-43-generic* linux-image-3.13.0-44-generic*
  linux-image-3.13.0-45-generic* linux-image-3.13.0-46-generic*
  linux-image-3.13.0-48-generic* linux-image-3.13.0-49-generic*
  linux-image-3.13.0-51-generic* linux-image-3.13.0-52-generic*
  linux-image-3.13.0-53-generic* linux-image-3.13.0-54-generic*
  linux-image-3.13.0-55-generic* linux-image-3.13.0-57-generic*
  linux-image-3.13.0-58-generic* linux-image-3.13.0-61-generic*
  linux-image-3.13.0-62-generic* linux-image-3.13.0-63-generic*
  linux-image-3.13.0-65-generic* linux-image-3.13.0-66-generic*
  linux-image-3.13.0-67-generic* linux-image-3.13.0-68-generic*
  linux-image-3.13.0-70-generic* linux-image-3.13.0-71-generic*
  linux-image-3.13.0-74-generic* linux-image-3.13.0-76-generic*
  linux-image-3.13.0-77-generic* linux-image-3.13.0-79-generic*
  linux-image-3.13.0-83-generic* linux-image-3.13.0-85-generic*
  linux-image-3.13.0-86-generic* linux-image-3.13.0-87-generic*
  linux-image-3.13.0-88-generic* linux-image-3.13.0-92-generic*
  linux-image-3.13.0-93-generic* linux-image-3.13.0-95-generic*
  linux-image-3.13.0-96-generic* linux-image-3.13.0-98-generic*
  linux-image-extra-3.13.0-100-generic* linux-image-extra-3.13.0-101-generic*
  linux-image-extra-3.13.0-103-generic* linux-image-extra-3.13.0-105-generic*
  linux-image-extra-3.13.0-106-generic* linux-image-extra-3.13.0-107-generic*
  linux-image-extra-3.13.0-108-generic* linux-image-extra-3.13.0-110-generic*
  linux-image-extra-3.13.0-112-generic* linux-image-extra-3.13.0-113-generic*
  linux-image-extra-3.13.0-115-generic* linux-image-extra-3.13.0-116-generic*
  linux-image-extra-3.13.0-117-generic* linux-image-extra-3.13.0-119-generic*
  linux-image-extra-3.13.0-121-generic* linux-image-extra-3.13.0-123-generic*
  linux-image-extra-3.13.0-125-generic* linux-image-extra-3.13.0-128-generic*
  linux-image-extra-3.13.0-129-generic* linux-image-extra-3.13.0-132-generic*
  linux-image-extra-3.13.0-133-generic* linux-image-extra-3.13.0-135-generic*
  linux-image-extra-3.13.0-137-generic* linux-image-extra-3.13.0-139-generic*
  linux-image-extra-3.13.0-141-generic* linux-image-extra-3.13.0-142-generic*
  linux-image-extra-3.13.0-39-generic* linux-image-extra-3.13.0-40-generic*
  linux-image-extra-3.13.0-43-generic* linux-image-extra-3.13.0-44-generic*
  linux-image-extra-3.13.0-45-generic* linux-image-extra-3.13.0-46-generic*
  linux-image-extra-3.13.0-48-generic* linux-image-extra-3.13.0-49-generic*
  linux-image-extra-3.13.0-51-generic* linux-image-extra-3.13.0-52-generic*
  linux-image-extra-3.13.0-53-generic* linux-image-extra-3.13.0-54-generic*
  linux-image-extra-3.13.0-55-generic* linux-image-extra-3.13.0-57-generic*
  linux-image-extra-3.13.0-58-generic* linux-image-extra-3.13.0-61-generic*
  linux-image-extra-3.13.0-62-generic* linux-image-extra-3.13.0-63-generic*
  linux-image-extra-3.13.0-65-generic* linux-image-extra-3.13.0-66-generic*
  linux-image-extra-3.13.0-67-generic* linux-image-extra-3.13.0-68-generic*
  linux-image-extra-3.13.0-70-generic* linux-image-extra-3.13.0-71-generic*
  linux-image-extra-3.13.0-74-generic* linux-image-extra-3.13.0-76-generic*
  linux-image-extra-3.13.0-77-generic* linux-image-extra-3.13.0-79-generic*
  linux-image-extra-3.13.0-83-generic* linux-image-extra-3.13.0-85-generic*
  linux-image-extra-3.13.0-86-generic* linux-image-extra-3.13.0-87-generic*
  linux-image-extra-3.13.0-88-generic* linux-image-extra-3.13.0-92-generic*
  linux-image-extra-3.13.0-93-generic* linux-image-extra-3.13.0-95-generic*
  linux-image-extra-3.13.0-96-generic* linux-image-extra-3.13.0-98-generic*
0 upgraded, 0 newly installed, 256 to remove and 19 not upgraded.
After this operation, 14.3 GB disk space will be freed.
Do you want to continue? [Y/n] Abort.

```

---

### Post by Impavidus on 2018-04-20
It aborts? Maybe some strange limit. I never tried to remove 256 packages at once, maybe it's some feature to prevent accidental mass deletion events.

Let's try it manually, just 10 versions at a time.```
sudo apt-get purge linux-headers-3.13.0-{39,40,43,44,45,46,48,49,51,52}{,-generic} linux-image{,-extra}-{39,40,43,44,45,46,48,49,51,52}-generic
sudo apt-get purge linux-headers-3.13.0-{53,54,55,57,58,61,62,63,65,66}{,-generic} linux-image{,-extra}-3.13.0-{53,54,55,57,58,61,62,63,65,66}-generic
sudo apt-get purge linux-headers-3.13.0-{67,68,70,71,74,76,77,79,83,85}{,-generic} linux-image{,-extra}-3.13.0-{67,68,70,71,74,76,77,79,83,85}-generic
sudo apt-get purge linux-headers-3.13.0-{86,87,88,92,93,95,96,98,100,101}{,-generic} linux-image{,-extra}-3.13.0-{86,87,88,92,93,95,96,98,100,101}-generic
sudo apt-get purge linux-headers-3.13.0-{103,105,106,107,108,110,112,113,115,116}{,-generic} linux-image{,-extra}-3.13.0-{103,105,106,107,108,110,112,113,115,116}-generic
sudo apt-get purge linux-headers-3.13.0-{117,119,121,123,125,128,129,132,133,135}{,-generic} linux-image{,-extra}-3.13.0-{117,119,121,123,125,128,129,132,133,135}-generic
sudo apt-get purge linux-headers-3.13.0-{137,139,141,142}{,-generic} linux-image{,-extra}-3.13.0-{137,139,141,142}-generic
```
Sometimes brute force is more effective than being clever. That should cut your disk space usage in half.

Edit: Or use the command of post #13, but add -y at the end. See below. It seems xargs or the pipe interferes with apt-get's request for confirmation.

---

### Post by deadflowr on 2018-04-20
Just add -y for yes to the xargs sudo apt purge command
I always have to.
```
xargs sudo apt purge -y
```
you can also dry-run it first by running with an -s option to simulate it.
simulating is a good way to see what will actually happen, and allow you to avoid making things worse.
But from the output above, all looks good to go so adding the -y is fine.

---

### Post by Impavidus on 2018-04-20
> **deadflowr said:**
> Just add -y for yes to the xargs sudo apt purge command
That could be it. I never use xargs myself.

---

### Post by deadflowr on 2018-04-20
I think if you run it with apt/apt-get you need to add -y to confirm.
If you try it with dpkg like
```
xargs sudo dpkg -P
```
it should not need to be confirmed.
Simply because apt/apt-get may want to remove more than what is requested from the outputted content.
dpkg should simply remove only that which is listed and nothing more.

---

### Post by thomasc5 on 2018-04-27
Yes it needs the -y option. 
After about an hour, it's finally purged all the packages. Yippee!

A big thank you to Impavidus and Deadflowr!

---

