---
title: "Manage Disk Space"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Mike.B on 2008-09-07
I have always maintained 2 Hard Drives under windows. A small one to hold the system files, installed apps etc. and a larger one to hold all data. Now that I have installed Kubuntu, I dont know how to manage my disk space, can anyone help?

---

### Post by meindian523 on 2008-09-07
What you call hard drives are actually partitions.Look up Wikipedia for an explanation.In Kubuntu(and all *nix),your small partition for system is called / and the bigger one to hold data is called /home.Only difference is that you can access /home through / (that is /home is actually a directory home which is under /,therefore /home).Still,that doesn't mean /home can be overwritten by something written to / when / is full(that's a situation to be avoided,BTW)Look up [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html).

---

### Post by cdtech on 2008-09-07
What organizational plans do you have?

Copy and paste the output of "df -H" and the output of "sudo fdisk -l"

---

