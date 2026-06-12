---
title: "Measuring hardware temperature in 12.04"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by vasa1 on 2012-05-05
If anyone is doing so on 12.04, please explain how in detail. What worked for me in [11.10]("https://launchpad.net/indicator-sensors") doesn't seem to be a simple matter anymore :( 

This code has [been offered]("http://askubuntu.com/questions/30334/what-application-indicators-are-available/48288#48288") but it gives me an error when I try to run it:
```
cd /tmp ; a=$(uname -p) ; if [[ "$a" = "x86_64" ]] ; then wget https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_amd64.deb ; else https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_i386.deb ; fi ; chmod +x /tmp/indicator-sensors_0.1-1* ; sudo dpkg -i /tmp/indicator-sensors_0.1-1*
```

And here's the error:
```
chmod: cannot access `/tmp/indicator-sensors_0.1-1*': No such file or directory
[sudo] password for user: 
dpkg: error processing /tmp/indicator-sensors_0.1-1* (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /tmp/indicator-sensors_0.1-1*
user@user-Inspiron-1545:/tmp$ 

```
On the face of it, it doesn't look like there's been recent activity. The last release is dated 2011-11-13.

And I don't understand the code but isn't one **wget** missing?

Edit: but work **is in progress** so all maybe well soon:
[https://code.launchpad.net/~alexmurray/indicator-sensors/master](https://code.launchpad.net/~alexmurray/indicator-sensors/master)

---

### Post by pqwoerituytrueiwoq on 2012-05-05
yes wget it missing
```
#!/bin/sh
cd /tmp
a=$(uname -p)
if [ "$a" = "x86_64" ];then
    wget https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_amd64.deb
else 
    wget https://launchpad.net/~alexmurray/+archive/indicator-sensors/+files/indicator-sensors_0.1-1_i386.deb
fi
chmod +x /tmp/indicator-sensors_0.1-1*
sudo dpkg -i /tmp/indicator-sensors_0.1-1*
exit
```

here is a install script run it with sh

---

### Post by vasa1 on 2012-05-05
> **pqwoerituytrueiwoq said:**
> yes wget it missing...here is a install script run it with sh
Hi! Have you installed it on your system (12.04)?

---

### Post by vasa1 on 2012-05-07
The code from the askubuntu.com link has been modified and works according to [this thread]("http://ubuntuforums.org/showpost.php?p=11914190&postcount=1"). I'm using Psensor for now.

---

