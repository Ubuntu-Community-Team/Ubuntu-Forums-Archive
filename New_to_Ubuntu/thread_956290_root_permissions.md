---
title: "root permissions"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by kilroy423 on 2008-10-23
sudo su

or just login as root


it is not recommended to run as root

---

### Post by Hexagoon on 2008-10-23
You have to edit the sudoers file, launch

```
visudo
```

and change your user line to

```
username ALL=(ALL) NOPASSWD:/bin/whatever
```

then you will be able to use sudo without password, you still have to enter the command sudo though.

---

### Post by Hexagoon on 2008-10-23
> **kilroy423 said:**
> sudo su

or just login as root


it is not recommended to run as root

sudo su will still ask for password, and it is not possible (by default) to login with root user account in ubuntu.

---

### Post by hermes0710 on 2008-10-23
Besides, it is not safe to do something like this...

---

### Post by kilroy423 on 2008-10-23
> sudo su will still ask for password

yah....but it will only ask you once...

---

### Post by hyper_ch on 2008-10-23
sudo -i will ask only once also... so you should use that.

---

### Post by Christmas on 2008-10-23
Running as root can have grave consequences on your system and you can eventually end up either hacked or with an unusable system. Any script with some mistakes in it can ruin your entire system, like running the remove command as root on an essential directory, like /usr/bin etc. And trust me, even in well-tested scripts errors may slip. Example:
```

cd /path/to/dir
rm *

```
If /path/to/dir doesn't exist, all the files in the current directory will be removed. Linux is built in a way which allows you to perform only system-wide configuration tasks as root (like installing packages using APT), but I strongly advise against running as root.

If you however, decided to experiment, I think what Hexagoon recommended will work (never tried, only  heard of it before), but you'll need to run visudo as *sudo visudo* and replace username with your user and /bin/whatever with /bin/bash.

I also recommend reading about security on Linux, and you can start [here](https://help.ubuntu.com/community/RootSudo).

---

### Post by Hexagoon on 2008-10-23
> **Christmas said:**
> 
If you however, decided to experiment, I think what Hexagoon recommended will work (never tried, only  heard of it before), but you'll need to run visudo as *sudo visudo* and replace username with your user and /bin/whatever with /bin/bash.

I agree on that,  i've tried it too, but in previous versions of ubuntu. Not on 8.04(/8.10) that's current now.

---

### Post by overdrank on 2008-10-23
Forums policy on root
> Tutorials explaining how to enable the root account for a graphical login or autologin will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding graphical Ubuntu root logins; such tutorials do not have to be hosted on the Ubuntu Forums.

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Thread closed as answer.

---

