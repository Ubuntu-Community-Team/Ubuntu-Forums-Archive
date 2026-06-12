---
title: "Share second hard drive with all users on my computer"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by i0ls on 2014-02-18
Hi
I am looking to replace our slow core 2 duo imac with a rig I pieced together and all is going well until I ran into this issue.
I have a second hard drive on the system I plan to store all of our stuff on to keep the room on the ssd for os and apps. The hard drive is set up to mount automatically in /etc/fstab and that works fine for one user. I have never had more than one account on any of my boxes before but with this I need one for the kids, wife, and myself.

I have tried to unmounted the drive so that I can set permissions and remount it but I get a drive busy error
I have also tried to   chmod 777 /dev/sda1   and   chmod 777 /media/mount   from separate accounts without luck.
Is there some way I can make this happen without setting permissions in each account? suggestions would be greatly appricated
Thanks

---

### Post by sudodus on 2014-02-18
If you have a partition with a linux file system on the second drive, you can set the permissions 'as you wish' for every directory and file, while Microsoft file systems get their permissions in linux when they are mounted.

So I suggest that you make a linux file system, for example ext4, in the partition that you want to share, and then modify the mount options in fstab.

---

### Post by oldfred on 2014-02-18
I do not know details, but you are into groups. Linux is a multi-user system, but you have to create groups and give permissions & ownership to each group.

 Group Permissions - posts by Morbius1
[http://ubuntuforums.org/showthread.php?t=2138476](http://ubuntuforums.org/showthread.php?t=2138476)
      
 See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

 Two users to share music folder - group & permissions - posts by BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)

---

### Post by i0ls on 2014-02-18
thank you guys for the reply. I should have mentioned that its a ext4 partition

Ill have a read through the links you posted up, just glancing they look like something that I will need to know regardless

---

### Post by i0ls on 2014-02-18
ok 
 i have tried to accomplish this unsuccessfully by.

create a group for the users accessing the drive
mount the drive with the acl option
set ownership and privileges to read and write on the drive for the group.
end results are nothing changed.

here's the instructions I followed:
sudo chown root.stone /mnt/mynewdrive
sudo chmod 0775 /mnt/mynewdrive
sudo chmod g+s  /mnt/mynewdrive
sudo chmod +t   /mnt/mynewdrive
sudo setfacl -d -m u::rwx,g::rwx,o::r-x /mnt/mynewdrive
Above...

Change owner to root and group owner to stone
Give write ability to the stone group
Cause all new files to be group-owned by stone
Restrict delete and rename to all but the user who created the file
By default, allow user and group rwx, others: rx

where have I gone wrong?
and how do i give access to delete anything?

---

### Post by fdrake on 2014-02-18
@OP:
can you paste here your fstab
```
cat  /etc/fstab
```

---

### Post by i0ls on 2014-02-20
So after accidentally messing the entire install up (or at least beyond my level of knowledge to repair) setting up the latest drivers for my gt 650 ti and re installing the entire os. 
I followed the directions as I did before and it works! I am one step closer to having my large user files on a second hard drive and booting off the ssd.
thanks guys for all of your help, if anyone has a great walk through for setting up home dir's or at least most of them post it up (although off topic)
Thanks again!

---

