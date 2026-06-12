---
title: "NTFS mounting in Ubuntu"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Anden1986 on 2008-10-05
Hi guys!

I am totally new to the Linux scene so go easy on me ok? :-) I finally got tired of WinXP and migrated to Linux and bo it it something different! My first (of probably many) problem is that my two NTFS formatted external drives wont open! I tried following a guide from in here telling me to install something called ntfs-config. I did that and also launched the app and aparently activated writing to NTFS drives from in there but I still get the error "Cannot mount volume" when I click on one of my drives! What am I doing wrong? :-(

Cheers!

-Anders

---

### Post by The Cog on 2008-10-05
I've never tried ntfsconfig so can't comment on that. Here's how I mount my windows partitions:

First, you need to make s directory that the drive contents will appear in - the "mount point". The normal place to do this would be a subdirectory in /mnt. Make a directory using a command like this:
```
sudo mkdir /mnt/windows
```
naming the directory whatever you want it to be. Having 2 partitions, you will want to make two such directories. Actually, mine are called /mnt/C and /mnt/E. 

Next you need to know the device names of the two partitions. The commmand 
```
sudo fdisk -l
```
will list all the partitions and their types. You need the names of the two partitions, something like /dev/sda1.
You can try and mount these manually with a command like this:
```
sudo mount /dev/sda1 /mnt/windows
``` 
just to see it work.
To make the nount happen every time you boot, you need to add a line in /et/fstab. The lines you need to add look like this:
```
/dev/sda2 /mnt/C ntfs nls=iso8859-1,umask=000 0 0
```
Be careful to note where there are spaces and where not in that line - it's important. You can edit the file with this command:
```
sudo gedit /etc/fstab
```

---

