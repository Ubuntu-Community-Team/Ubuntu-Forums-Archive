---
title: "home partition"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by jhackett on 2008-10-21
Hello all....I have been in the process of revamping an old computer that crashed on me a while back, and everything is going fine, save my command of the computer box thingy. I am wondering about something in the installation directions about partitioning the home partition.

the entry here: [https://help.ubuntu.com/8.04/switching/installing-partitioning.html]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html")
"Creating the home partition

This step is not necessary but will allow you to keep your settings and files in the event you reinstall Ubuntu. Set it up as you would the *home* partition but choose /home as the mount point."

should this be 'Set it up as you would the ROOT partition but choose /home as the mount point'? ROOT as opposed to HOME? I think it is, but I just wanted to see if anyone could clarify this for me...

thanks
//j

---

### Post by Elfy on 2008-10-21
Yes it would logically need to read as you think it should.

mmm - extended and logical partitions are mixed up as well

---

### Post by Duck2006 on 2008-10-21
Set

/                  (root)
/ home             (home)
swap partition     (swap partition)


So yes it would.

---

### Post by buixuanduong1983 on 2008-10-21
Look like a typo mistake, I think it should be "ROOT".

As far as I know, ROOT (/) is the very first starting point of all folders in your system. Starting from ROOT, you have your home folder, normally in /home/<your_username>, all mounted device (like C:, D: in Windows) in /media/, and many more.

---

