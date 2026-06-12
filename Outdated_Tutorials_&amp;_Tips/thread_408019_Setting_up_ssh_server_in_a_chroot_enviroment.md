---
title: "Setting up ssh server in a chroot enviroment"
date: 2007-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by whtet on 2007-04-12
Step 1:

    * sudo apt-get install dchroot debootstrap
    * sudo mkdir /chroot/
    * sudo gedit /etc/dchroot.conf
          o Add this line: hoary /chroot
    * sudo debootstrap --arch i386 hoary /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
    * sudo chroot /chroot/
    * dpkg-reconfigure locales

Step 2:
In another terminal window (or by existing chroot):

    * sudo gedit /chroot/etc/apt/sources.list
    * Add the following lines:
          o deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
          o deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse

(We do this step because gedit has yet to be installed in the chroot environment)

Step 3:
In your chrooted environment (chroot /chroot):

    * apt-get update ; apt-get upgrade

Step 4:
In another terminal window (or by existing chroot):

    * sudo cp /etc/passwd /chroot/etc/
    * sudo cp /etc/shadow /chroot/etc/
    * sudo cp /etc/group /chroot/etc/
    * sudo cp /etc/sudoers /chroot/etc/
    * sudo cp /etc/hosts /chroot/etc/
    * sudo gedit /etc/fstab
    * Add the following lines:
          o /tmp /chroot/tmp none bind 0 0
          o /dev /chroot/dev none bind 0 0
          o /proc /chroot/proc proc defaults 0 0
          o /usr/share/fonts /chroot/usr/share/fonts none bind 0 0

Step 5:

chrootshell will be installed setuid root, so first audit the source ([chrootshell.c]("http://kegel.com/crosstool/current/chrootshell.c")) for security problems, then compile and install it with the commands

          o cc chrootshell.c -o chrootshell
          o sudo install -o root -m 4755 chrootshell /sbin/chrootshell

You probably need to add the line

/sbin/chrootshell

to /etc/shells, else login may refuse to run it.

Step 6:

Create outer /etc/passwd entry
For each user you want to give access to a chroot enviroment, create a new /etc/passwd entry for each user/chroot combination, with home directory set to the chroot directory, and the shell set to /sbin/chrootshell, e.g.

fred2:x:1000:1000:Fred Smith:/chroot:/sbin/chrootshell

Step 7:

Create inner /etc/passwd entry
For each user created in the previous step, create a new /etc/passwd entry in the chroot's /etc/passwd. This entry should list a real home directory inside the chroot, and a real shell, so it'll be quite different from the one in the system /etc/passwd. For example:

fred2:x:1000:1000:Fred Smith:/home/fred2:/bin/sh

Then create a home directory in the chroot enviroment and change the ownership to the user

          o sudo mkdir /chroot/home/fred2
          o sudo chown fred2 /chroot/home/fred2
          o sudo chmod 700 /chroot/home/fred2

Step 8:

Try logging in as a jailed user via telnet, e.g.

          o telnet localhost
          o username: fred2
          o password: xxxx

---

### Post by frodon on 2007-04-13
Nice guide but please add a warning at the beginning that **this guide is for ubuntu hoary 5.04.**

---

### Post by whtet on 2007-04-16
Here are the reference links:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
[http://kegel.com/crosstool/current/doc/chroot-login-howto.html](http://kegel.com/crosstool/current/doc/chroot-login-howto.html)

---

