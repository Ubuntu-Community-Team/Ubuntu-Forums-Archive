---
title: "Installation to external USB drive"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by darb78 on 2014-10-15
I successfully (or so it appeared) installed Ubuntu 12.04 (32 bit) on an external hard drive so that I could carry it between two different macs. Installation seemed to go very smoothly, all hardware is now working, but when I attempt to install new software I receive a host of errors and it refuses. I have attached a screen shot of a couple of recent install attempts of two different programs. Can someone point me in the correct direction to resolve this matter?

Thank you in advance!

 [ATTACH=CONFIG]257223[/ATTACH][ATTACH=CONFIG]257224[/ATTACH]

---

### Post by mastablasta on 2014-10-15
check the software sources in software center. make sure proper sources are ticked. then try again.

also try to search for GNOME partition editor in software center. see if you can install that.

---

### Post by mc4man on 2014-10-15
All new installs require that you, (or something) updates your sources before installing anything

---

### Post by yancek on 2014-10-15
Start with Number 1 in the instructions at the site below to.  The rest is optional.

 [http://www.unixmen.com/top-things-installing-ubuntu-14-0413-1013-0412-1012-04/](http://www.unixmen.com/top-things-installing-ubuntu-14-0413-1013-0412-1012-04/)

Usually it is better to put GParted on a CD/flash drive as you cannot modify partitions from a running system.

---

### Post by frank75 on 2014-10-15
First thing I see is that you forgot the "install" command.  Should be "sudo apt-get install gparted"  Also, make sure that you've did a "sudo apt-get update" and "sudo apt-get upgrade" to get everything up to date.   Since I've sold off my #3 "Play" laptop I've started using external hard drives to do installs of Distros to play around with and it seems to work pretty well. Just remember when you do that to point GRUB at the correct place(should normally be sdb IIRC and not internal sda) and do your updates and stuff on the external hard drive same as you would your internal.  Hope you get this worked out.

---

### Post by darb78 on 2014-10-16
Ran sudo apt-get update and received the following errors:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  Hash Sum mismatch
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  Hash Sum mismatch
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Hash Sum mismatch
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

