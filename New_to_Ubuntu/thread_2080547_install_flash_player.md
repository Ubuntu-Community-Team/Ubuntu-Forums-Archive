---
title: "install flash player"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by sayou on 2012-11-04
When ever I try to install flash player on ubuntu 12.10 or any other app : this message appear : Can some body help me please 
nstallArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Selecting previously unselected package libnspr4-0d:amd64.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
dpkg: unrecoverable fatal error, aborting:
 files list file for package `ubuntu-docs' contains empty filename
Error in function:

---

### Post by overdrank on 2012-11-04
Hi and welcome, moved to Absolute Beginners Section with more descriptive title :)

---

### Post by Abhinav Kumar on 2012-11-04
> **sayou said:**
> When ever I try to install flash player on ubuntu 12.10 or any other app : this message appear : Can some body help me please 
nstallArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Selecting previously unselected package libnspr4-0d:amd64.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
dpkg: unrecoverable fatal error, aborting:
 files list file for package `ubuntu-docs' contains empty filename
Error in function:

Hi,
You can try installing flash in some other way too. 
Go to adobe site 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and download flash player as tar file.

Now extract the contents of tar file using archive manager.

say you extracted and you created folder named install_flash at the Desktop.
You can see there will be a file named libflashplayer.so in install_flash folder.
execute the following command in terminal
```
sudo cp ~/Desktop/install_flash/libflashplayer.so /usr/lib/mozilla/plugins/

```
and then give the password.
restart firefox

---

### Post by monkeybrain2012 on 2012-11-04
OP says he experiences the same problem installing other apps so telling him to download and install flash manually is not the solution.

It seems that this thread may be useful [http://ubuntuforums.org/showthread.php?t=1422921](http://ubuntuforums.org/showthread.php?t=1422921)

---

