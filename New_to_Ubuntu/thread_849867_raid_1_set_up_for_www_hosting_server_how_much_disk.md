---
title: "raid 1 set up for www hosting server how much disk space..."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mspIggy on 2008-07-04
how much disk space should i allocate for the system partitions ina raid 1 setup with 80 gb drives...

i have no idea...

i pulled a number of 6gb out of thin air and have been owrking now for 4 hours, setup is going ok...

but i would hate to find out in a week, or month after log files start ti build i am out of space...

if i need to re-partition these drives 0 i have to do this now --

any thoughts on this?

many thanks

8.04 server amd64

---

### Post by cariboo on 2008-07-05
This is the wrong place to ask this question, it should be in the server forum, but because you asked, the root directory for apache2 is located in /var/www which is part of the root file system. You should give your / file system the whole disk,as this is a server you don't need a seperate home partition. All the log files and kernels plus archived packages are located there. The log files rotate weekly, so it is up to you how many weeks of log files you want to keep. Keep an eye on /var/cache/apt/archives and clean it up every week or two using:

```
sudo apt-get clean
```

Another way to save space is don't bother installing any gui as that is a waste of space and cpu cycles. Get familiar with the commad line. I use a program called mc, which is available in the repositories, it is similar to Norton Commander from the preSymantec days you can move, copy, delete and edit files with mc. it even has a builtin ftp client.

Jim

---

### Post by mspIggy on 2008-07-05
no gui...

sorry -- maybe i missed the mark...

this is installed in a g6b raid 1 array

is 6 gb enough space for all of this to run on?

manye i wll head over to the server forum -- many thanks

---

