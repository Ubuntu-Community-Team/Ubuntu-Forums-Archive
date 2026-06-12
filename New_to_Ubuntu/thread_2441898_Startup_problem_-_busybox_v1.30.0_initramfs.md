---
title: "Startup problem - busybox v1.30.0 initramfs"
date: 2020-04-27
forum: New to Ubuntu
---

### Post by ediano on 2020-04-27
Hello,


I have been using Ubuntu 20.04 LTS since 04/24/2020, since that time my system had twice the following error when restarting (busybox v1.30.0 initramfs) the first time I reinstalled the system from scratch, because I chose a better choice. Today, the error occurred again, instead of reinstalling, I chose to correct the error with the following command (fsck -y dev / sda2). I did some checks to rule out a problem on the hard drive and, according to the report, everything is fine, in this case, I believe it may be a small bug in the system.


NOTE: The error was repeated after I tried to copy a file to the pendrive (to no avail), I ejected the pendrivve and restarted the system at the time the error occurred.

---

### Post by ediano on 2020-04-28
Hello, I had another problem that I believe is linked to the previous reported problem.


Still trying to copy files to a predrive (without success), I noticed that my home folder has a lock symbol, denying any type of software execution and command in the terminal, so I also can't save new files.


At this point I started using Ubuntu 19.10 again

---

### Post by CelticWarrior on 2020-04-28
Either the permissions are seriously messed up or the drive is about to fail.

---

