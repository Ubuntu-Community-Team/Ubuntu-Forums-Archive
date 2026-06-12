---
title: "Lost the Archive Manager"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by trebor7_1 on 2008-10-02
Hi, I've had some errors with 8.04 recently, the system hung up and I had to power down. On start up the system failed with drive errors. Fixed these by booting from live Cd and running fdisk -f, it took a long time but now boots.

Problem is some things are not working as they were before, for example archive manager is not working when I double click a rar file for example.

The command line gives this message

The program 'file-roller' is currently not installed.  You can install it by typing:
sudo apt-get install file-roller
Tried this but that results in 

file-roller is already the newest version

Any ideas on how to fix this please ?

:confused:

---

### Post by whizbaby on 2008-10-02
Does (in a terminal)
```
sudo updatedb
```
and then
```
locate file-roller|grep bin
```
come up with a binary file? If yes, try running it
```
/usr/bin/file-roller
```
if not, try
```
sudo dpkg -r file-roller --force-all
```
and if that works then reinstall with apt-get, as you tried before.

---

### Post by trebor7_1 on 2008-10-02
You are a star whizbaby...
The file was missing from usr/bin. Tried your suggestions reinstalled and all working again.

Thank you very much.

---

