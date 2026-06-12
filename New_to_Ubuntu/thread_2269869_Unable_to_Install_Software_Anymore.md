---
title: "Unable to Install Software Anymore"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by joe163 on 2015-03-18
Just noticed the problem today when trying to install any software on pc.  I get the following error:

```
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `xserver-xorg-video-s3': No such device or address
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I have tried rebooting which fixed some drive errors.  Also, I often get the message that there was a problem with a software on the system prompting me to report the problem or cancel.

Output from lspci in attachment.

Please let me know if you need more info.

Thanks.  I have to sleep now for work tomorrow so will not be able to provide more info until the morning before I leave for work.

---

### Post by sandyd on 2015-03-18
> **joe163 said:**
> Just noticed the problem today when trying to install any software on pc.  I get the following error:

```
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `xserver-xorg-video-s3': No such device or address
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I have tried rebooting which fixed some drive errors.  Also, I often get the message that there was a problem with a software on the system prompting me to report the problem or cancel.

Output from lspci in attachment.

Please let me know if you need more info.

Thanks.  I have to sleep now for work tomorrow so will not be able to provide more info until the morning before I leave for work.

Please post the output of
```

apt-cache show xserver-xorg-video-s3
ls /var/lib/dpkg/info/xserver-xorg-video-s3.list

```

Also, what version of Ubuntu are you using?

---

### Post by joe163 on 2015-03-18
```
fr0sti3@fr0sti3:~$ apt-cache show xserver-xorg-video-s3 /var/lib/dpkg/info/xserver-xorg-video-s3.list
Package: xserver-xorg-video-s3
Priority: optional
Section: x11
Installed-Size: 119
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: i386
Version: 1:0.6.5-0ubuntu4
Provides: xorg-driver-video
Depends: libc6 (>= 2.3.6-6~), xorg-video-abi-15, xserver-xorg-core (>= 2:1.14.99.902)
Filename: pool/main/x/xserver-xorg-video-s3/xserver-xorg-video-s3_0.6.5-0ubuntu4_i386.deb
Size: 28690
MD5sum: fa003464d07d21e02803e840d3b94cc9
SHA1: 63f43606b6e456c86cf557df86f60c0e1aebcd59
SHA256: ca1e67675af372ee8e0c9d2f449c0338aa882d9f9cb30a8a83dbf572df1ac6b8
Description-en: X.Org X server -- legacy S3 display driver
 This package provides the driver for certain legacy S3 video card chipsets,
 including the Trio64 and 96x cards.  It does not provide support for
 ViRGE/Trio3D or Savage chipsets; support for these cards is provided by
 xserver-xorg-video-s3virge and xserver-xorg-driver-savage, respectively.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-video-s3 driver module.
Description-md5: 08333113374682cbc50a4f18cf30d8c4
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-active, kubuntu-active-desktop, kubuntu-active, edubuntu-desktop, edubuntu-usb, xubuntu-desktop, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, lubuntu-core, ubuntustudio-desktop, ubuntu-gnome-desktop


N: Unable to locate package /var/lib/dpkg/info
fr0sti3@fr0sti3:~$ 

```

Ubuntu 14.04 LTS

---

### Post by buzzingrobot on 2015-03-19
Do ```
ls /var/lib/dpkg/info/xserver-xorg-video-s3.list
```

to see if the file "xserver-xorg-video-s3.list" exists in that directory.

---

### Post by joe163 on 2015-03-19
```
fr0sti3@fr0sti3:~$ ls /var/lib/dpkg/info/xserver-xorg-video-s3.list
/var/lib/dpkg/info/xserver-xorg-video-s3.list
fr0sti3@fr0sti3:~$ ls -la /var/lib/dpkg/info/xserver-xorg-video-s3.list
s---rwSrwx 1 2735674540 2215625287 0 &#1491;&#1510;&#1502; 30  2003 /var/lib/dpkg/info/xserver-xorg-video-s3.list

```

Thanks.

---

### Post by Vladlenin5000 on 2015-03-19
I wonder why you're having this issue with a S3 driver (from 2003!!!) that shouldn't be there in the first place considering that your graphics chip is ```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```

---

### Post by joe163 on 2015-03-20
Well, thank you, but how do I resolve the issue so I will be able to install packages once again?

---

### Post by dino99 on 2015-03-20
hello joe

may i ask which ubuntu release is ran on your system ?
it looks like you are using a very very old fully dead version.

---

### Post by joe163 on 2015-03-20
Ubuntu 14.04 LTS

---

### Post by dino99 on 2015-03-20
then it seems that dist-upgrade has been used a lot, successively dist-upgrading older release to new one.
search for `xserver-xorg-video-s3' (without quotes) into your file manager (nautilus or else), then delete (purge) them all

---

### Post by joe163 on 2015-03-20
Thank you, I will try that.  And no, this is a fresh install of 14.04 made less than a month ago.

---

### Post by joe163 on 2015-03-20
Tried to do as you suggested:

```
installArchives() failed: (Reading database ... 
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `xserver-xorg-video-s3': No such device or address
Error in function: 

```

After I tried to install build-essential:

```
Do you want to continue? [Y/n] y
Selecting previously unselected package libstdc++-4.8-dev:i386.
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `xserver-xorg-video-s3': No such device or address
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by joe163 on 2015-03-22
No one has any other ideas what I need to do, or do I, for the umpteenth time, have to re-install Ubuntu?

Not to complain, it just seems that the last several months of using Ubuntu, it just always has something that breaks after just a few weeks of normal use. :(

---

### Post by buzzingrobot on 2015-03-22
This thread ([http://ubuntuforums.org/showthread.php?t=2247453](http://ubuntuforums.org/showthread.php?t=2247453)) suggests:

```
 sudo rm -f /var/lib/dpkg/info/format
```

then...

```
sudo dpkg --configure -a
```

Note that the OP in the thread didn't report back.

---

### Post by joe163 on 2015-03-26
Same problem still.

---

