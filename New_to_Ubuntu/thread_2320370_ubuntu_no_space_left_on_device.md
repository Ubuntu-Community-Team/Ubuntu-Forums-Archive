---
title: "ubuntu no space left on device"
date: 2016-04-13
forum: New to Ubuntu
---

### Post by parahakoo on 2016-04-13
I move from Windows to Linux
I think I have less space in my drive for updates and installation.

I'm trying to install D-space when this error display "ubuntu no space left on device"
df-h result
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.1G  7.0G     0 100% /
udev             10M     0   10M   0% /dev
tmpfs           793M  9.4M  784M   2% /run
tmpfs           2.0G  172K  2.0G   1% /dev/shm
tmpfs           5.0M   16K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs           397M   16K  397M   1% /run/user/120
tmpfs           397M   12K  397M   1% /run/user/1000

Please help me to solve this problem.

I have another drive sda3 217 GB

---

### Post by grahammechanical on 2016-04-13
If I understand correctly, you have installed Ubuntu into a partition that is only 7.1 GB in size. I am not surprised you are unable to install this application or any application for that matter. 7.1 GB is really a very minimal size for Ubuntu.

From the relevant web site this application needs lamp-server, tomcat-server & postgresql-server installed as pre-requisites. I have never installed any of them but I cannot imagine these packages to be small in size.

Is this Ubuntu server? Ubuntu server edition will install into 1 GB of space but once we start installing other things 7.1 GB can prove to be too small. As you have found out.

Regards

---

### Post by TheFu on 2016-04-13
7G is fine, if you run a few specific services and ZERO GUI.
7G is nowhere near enough if you run Ubuntu Desktop, Xubuntu, Lubuntu. Those all need more storage for non-toy installs.
25G is a normal, reasonable, / for a desktop provided /home is placed on a different partition.

So ... the solution that I have is to make a 25G partition somewhere else and use rsync to mirror the data on /sda1 to that, remove sda, then run grub install and update-grub so that other disk is recognized with a partition that has Linux.  I'd make another partition for /home - whatever size you need. More if you do video or audio files. Less if not.  Use a live-CD to do this work. Do NOT boot off the full OS.

For example, here is my daily-use desktop. It is very stripped down and only used for email, web, and documentation.
```
$ df
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        17G   13G  2.8G  83% /
```
See how things line up nice because I used 'code' tags? It is 17G and always almost full.
Everything fits into that 1 partition. OS, GUI apps (very limited) and my documents.

If this is a server, you can get by on much less.  I have a few 4G servers, but they do 1 thing only. ZERO GUI programs.

---

### Post by ajgreeny on 2016-04-13
I think if we are to assist you it would be very helpful to us to see your partition layout by posting a screenshot from gparted, which you can find in the live media you used for installing Ubuntu.  It can be installed in your OS normally, though can not then be used to manage the OS's partitions, but it is still useful to see the partition arrangement on disk.  It sounds as if that may be impossible for you, as there is insufficient space available.

Post back here a screenshot, as an attachment, using the paperclip icon in the toolbar of the reply text-box.

---

### Post by TheFu on 2016-04-13
Or post the output from **sudo parted -l** in "code tags" .

---

