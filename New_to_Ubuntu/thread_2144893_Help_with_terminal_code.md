---
title: "Help with terminal code"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by rdksek844 on 2013-05-13
Trying to install xfi audio driver. Downloaded the tarball and extracted it in the desktop. Now the readme file says


> 
Quick install


=============
In terminal,


1) Goto source directory
2) Execute make command as root
make
make install






Can someone show me the proper commands to use in the terminal to accomplish this? Thanks.

---

### Post by overdrank on 2013-05-13
Hi and welcome, please do not create multiple threads on the same issue. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=2144560").  Thread closed

---

### Post by lisati on 2013-05-13
Once you've started a terminal session, type in the following:
```
cd /path/to/files
sudo make
sudo make install

```
If you are asked for your password, use the password you'd use to login to your machine. Nothing will show on the screen when you type it, this is normal.
Don't forget to replace **/path/to/files** with the proper folder name.

---

