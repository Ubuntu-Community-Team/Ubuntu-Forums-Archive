---
title: "[SOLVED] Changing group ownership."
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Aximilli on 2008-06-05
I'm attempting to use 8.04 server edition to make a centralized storage computer in my house, and I've encountered a pretty big problem right off the bat. 

The storage partition on my first drive is mounted into /share/public (which i created). I made a new user group to include the other members of my house, but when I try to change the folder's group ownership I am denied, even as root. 

```

root@storage:/# chgrp 666 /d1storage/ -R
chgrp: changing group of `/d1storage/music': Operation not permitted
chgrp: changing group of `/d1storage/installers': Operation not permitted
chgrp: changing group of `/d1storage/video/gamow.wmv': Operation not permitted
chgrp: changing group of `/d1storage/video': Operation not permitted
chgrp: changing group of `/d1storage/': Operation not permitted


```

this method doesn't work either.

```

root@storage:/share# chown -hR alex:sharers /share/public/
chown: changing ownership of `/share/public/music': Operation not permitted
chown: changing ownership of `/share/public/installers': Operation not permitted
chown: changing ownership of `/share/public/video/gamow.wmv': Operation not permitted
chown: changing ownership of `/share/public/video': Operation not permitted
chown: changing ownership of `/share/public/': Operation not permitted

```

I can't figure out what I'm doing wrong. Sorry to be such a noob, but I need to get past this.

Thanks
Alex

---

### Post by PinkFloyd102489 on 2008-06-05
Either become root or use sudo in front of the command.


EDIT: Didnt read the last part. Unmount the share, chown it, then remount.

---

### Post by Aximilli on 2008-06-05
Please take a look at the code. note that I am logged in as root.

I'm noob, but not *that* noob

EDIT - ok saw your edit, trying that now, thanks

---

### Post by Aximilli on 2008-06-05
Awesome, thanks so much!

---

### Post by Aximilli on 2008-06-05
I spoke to soon on this one. When I unmount and run a recursive chgrp on the parent folder of the mount i get no errors, but when I remount the folder is still owned by the plugdev group, not my sharers group. Any more thoughts?

---

### Post by iaculallad on 2008-06-05
> **Aximilli said:**
> I spoke to soon on this one. When I unmount and run a recursive chgrp on the parent folder of the mount i get no errors, but when I remount the folder is still owned by the plugdev group, not my sharers group. Any more thoughts?

To change group ownership, follow this format:

```
sudo chgrp system_groupname /location_of_files_or_folders
```

---

### Post by Aximilli on 2008-06-05
I thought it might help to show step by step what is happening to me.

```


alex@storage:/share$ cd /
alex@storage:/$ ls -al
total 104
drwxr-xr-x  24 root root     4096 2008-06-05 15:45 .
drwxr-xr-x  24 root root     4096 2008-06-05 15:45 ..
drwxr-xr-x   2 root root     4096 2008-06-02 20:17 bin
drwxr-xr-x   3 root root     4096 2008-06-03 20:02 boot
lrwxrwxrwx   1 root root       11 2008-06-02 20:00 cdrom -> media/cdrom
drwxr-xr-x   2 root root     4096 2008-06-02 20:00 d1storage
drwxr-xr-x  14 root root    14460 2008-06-03 21:00 dev
drwxr-xr-x 127 root root    12288 2008-06-05 23:31 etc
drwxr-xr-x   5 root root     4096 2008-06-02 20:23 home
drwxr-xr-x   2 root root     4096 2008-06-02 20:01 initrd
lrwxrwxrwx   1 root root       32 2008-06-02 20:04 initrd.img -> boot/initrd.img-2.6.24-16-server
drwx------   3 root root     4096 2008-06-03 20:53 .kde
drwxr-xr-x  16 root root     4096 2008-06-03 19:37 lib
drwx------   2 root root    16384 2008-06-02 20:00 lost+found
drwxr-xr-x   4 root root     4096 2008-06-02 20:00 media
drwxr-xr-x   2 root root     4096 2008-04-15 01:53 mnt
drwxr-xr-x   2 root root     4096 2008-06-02 20:01 opt
dr-xr-xr-x 106 root root        0 2008-06-03 20:59 proc
drwxr-xr-x   5 root root     4096 2008-06-03 20:26 root
drwxr-xr-x   2 root root     4096 2008-06-03 19:36 sbin
**drwxr-xr-x   3 root sharers  4096 2008-06-05 15:57 share**
drwxr-xr-x   2 root root     4096 2008-06-02 20:01 srv
drwxr-xr-x  12 root root        0 2008-06-03 20:59 sys
drwxrwxrwt  10 root root     4096 2008-06-05 07:35 tmp
drwxr-xr-x  11 root root     4096 2008-06-02 20:21 usr
drwxr-xr-x  17 root root     4096 2008-06-03 19:59 var
lrwxrwxrwx   1 root root       29 2008-06-02 20:04 vmlinuz -> boot/vmlinuz-2.6.24-16-server
-rw-------   1 root root        0 2008-06-03 20:52 .Xauthority
alex@storage:/$ cd /share/
alex@storage:/share$ ls -al
total 40
drwxr-xr-x  3 root sharers  4096 2008-06-05 15:57 .
drwxr-xr-x 24 root root     4096 2008-06-05 15:45 ..
**drwxrwx---  5 root plugdev 32768 1969-12-31 19:00 public**
alex@storage:/share$ sudo umount /share/public/
**alex@storage:/share$ sudo chgrp -R sharers /share/public/**
alex@storage:/share$ ls -al
total 12
drwxr-xr-x  3 root sharers 4096 2008-06-05 15:57 .
drwxr-xr-x 24 root root    4096 2008-06-05 15:45 ..
**drwxr-xr-x  2 alex sharers 4096 2008-06-05 15:57 public**
alex@storage:/share$ sudo mount -a
alex@storage:/share$ ls -al
total 40
drwxr-xr-x  3 root sharers  4096 2008-06-05 15:57 .
drwxr-xr-x 24 root root     4096 2008-06-05 15:45 ..
**drwxrwx---  5 root plugdev 32768 1969-12-31 19:00 public**


```

I assume this means that at every reboot the folders group ownership will change back to plugdev. I hope this information is helpful, despite being overly verbose. 

Thanks a lot for your time.

Alex

---

### Post by Aximilli on 2008-06-05
> **iaculallad said:**
> To change group ownership, follow this format:

```
sudo chgrp system_groupname /location_of_files_or_folders
```


I do believe that is the format I'm using, is it not?

---

### Post by myrs2 on 2008-06-05
[cheap runescape equipment](http://www.gprunescape22.com/runescape-equipment)
[runescape accounts](http://www.gprunescape2.com/runescape-accounts.html)
[runescape accounts](http://www.mmors2.com/index.html)
[cheap runescape gold](http://www.myrs2.com/) 
[cheap runescape gold](http://www.gprunescape22.com/runescape-runes)
[cheap runescape items](http://www.gprunescape2.com/runescape-equipment2.html)
[cheap runescape gold](http://www.mmors2.com/)
[buy runescape items](http://www.myrs2.com/index.html)  
[runescape gold](http://www.gprunescape22.com/runescape-logs)
[runescape items](http://www.gprunescape2.com/runescape-equipment3.html)
[runescape powerleveling](http://www.mmors2.com/runescape-powerleveling.html)
[runescape equipment](http://www.myrs2.com/runescape-equipment.html)
[buy runescape accuonuts](http://www.gprunescape22.com/index)
[buy runescape item](http://www.gprunescape2.com/runescape-equipment4.html)
[buy runescape gold](http://www.mmors2.com/Runescape-gold.html)
[runescape equipments](http://www.myrs2.com/runescape-equipment2.html)
[runescape powerleveling](http://www.gprunescape22.com/runescape-powerleveling)
[runescape item](http://www.gprunescape2.com/runescape-equipment5.html)
[cheap runescape accounts](http://www.mmors2.com/runescape-othergoods1.html)
[runescape items](http://www.myrs2.com/runescape-equipment3.html)
[cheap ruenscape account](http://www.gprunescape22.com/runescape-accounts)
[cheap runescape equipments](http://www.gprunescape2.com/runescape-equipment6.html)
[buy runescape account](http://www.mmors2.com/runescape-runes1.html)
[runescape item](http://www.myrs2.com/runescape-equipment4.html)
[cheap runescape power leveling](http://www.gprunescape22.com/runescape-news)
[runescape equipments](http://www.gprunescape2.com/runescape-equipment7.html)
[cheap rs2 accounts](http://www.mmors2.com/runescape-party-hat1.html)
[rs2 equipments](http://www.myrs2.com/runescape-equipment5.html)
[runescape guides](http://www.gprunescape22.com/runescape-guides)
[buy runescape equipment](http://www.gprunescape2.com/runescape-equipment8.html)
[cheap runescape power leveling](http://www.mmors2.com/runescape-bargain-sets1.html)
[rs2 items](http://www.myrs2.com/runescape-equipment7.html)
[cheap runescape gold](http://www.gprunescape22.com/runescape-gold)
[runescape equipment](http://www.gprunescape2.com/runescape-equipment9.html)
[rs2 powerleveling](http://www.mmors2.com/Aboutus.html)
[rs item](http://www.myrs2.com/runescape-equipment8.html)
[buy runescape moeny](http://www.gprunescape22.com/runescape-contactus)
[cheap rs equipments](http://www.gprunescape2.com/runescape-equipment10.html)
[runescape equipments](http://www.mmors2.com/runescape-equipment8.html)
[buy runescape moeny](http://www.myrs2.com/runescape-Gold.html)
[cheap rs gold](http://www.gprunescape22.com)
[rs equipments](http://www.gprunescape2.com/runescape-equipment11.html)
[runescape equipment](http://www.mmors2.com/runescape-equipment7.html)
[buy runescape equipments](http://www.gprunescape22.com/runescape-equipment2)
[cheap runescape power leveling](http://www.myrs2.com/Orderstep.html)
[buy rs2 items](http://www.gprunescape2.com/runescape-equipment111.html)
[runescape items](http://www.mmors2.com/runescape-equipment6.html)
[cheap rs2 powerleveling](http://www.myrs2.com/services.html)
[cheap runescape items](http://www.gprunescape22.com/runescape-equipment3)
[rs items](http://www.gprunescape2.com/runescape-equipment.html)
[runescape item](http://www.mmors2.com/runescape-equipment5.html)
[cheap rs items](http://www.myrs2.com/aboutus.html)
[buy runescape item](http://www.gprunescape22.com/runescape-equipment4)
[buy runescape gold](http://www.gprunescape2.com/runescape-logs.html)
[runescape2 items](http://www.mmors2.com/runescape-equipment4.html)
[cheap runescape2  items](http://www.myrs2.com/runescape-logs.html)
[runescape items](http://www.gprunescape22.com/runescape-equipment5)
[cheap rs2 gold](http://www.gprunescape2.com/runescape-othergoods2.html)
[runescape2 equipments](http://www.mmors2.com/runescape-equipment3.html)
[runescape powerleveling](http://www.myrs2.com/runescape-powerleveling.html)
[runescape equipments](http://www.gprunescape22.com/runescape-equipment6)
[cheap runecape gold](http://www.gprunescape2.com/runescape-othergoods.html)
[cheap rs items](http://www.mmors2.com/runescape-equipment2.html)
[cheap rs gold](http://www.myrs2.com/runescape-othergoods.html)
[buy runescape items](http://www.gprunescape2.com/runescape-party-hat.html)
[buy rs2 items](http://www.mmors2.com/runescape-equipment1.html)
[cheap runescape accounts](http://www.myrs2.com/runescape-runes.html)
[runescape powerleveling](http://www.gprunescape2.com/runescape-powerleveling.html)
[cheap runecape equipments](http://www.gprunescape2.com/runescape-runes.html)
[cheap runescape power leveling](http://www.gprunescape2.com/services.html)
[cheap rs2 power leveling](http://www.gprunescape2.com/western-union.html)
[runescape account](http://www.gprunescape2.com/accounts/combat54.html)


Runescape items,equipment,powerleveling,accounts Selling, We sell Runescape 2 Gold, RuneScape Money, RuneScape GP, 24/7 online support and Fast Delivery.

---

### Post by Aximilli on 2008-06-05
well, Yay. My thread has just been spammed. Yippy for me.:confused:

EDIT: Looks like this guy is spamming alot of other threads. Ban time.

---

### Post by PmDematagoda on 2008-06-05
> **Aximilli said:**
> well, Yay. My thread has just been spammed. Yippy for me.:confused:

EDIT: Looks like this guy is spamming alot of other threads. Ban time.

Don't worry, he's been taken care of. But in future, if you actually want spam to be taken care of then you should report it instead of going around posting threats to the spammer since it is pointless and is just wasting time.

---

### Post by Aximilli on 2008-06-05
> **PmDematagoda said:**
> Don't worry, he's been taken care of. But in future, if you actually want spam to be taken care of then you should report it instead of going around posting threats to the spammer since it is pointless and is just wasting time.

I did report him, on this and several other threads. And where exactly did I threaten anybody? The main point of that post was just a bump so I could get an answer.

---

### Post by iaculallad on 2008-06-05
What about going inside your share directory and just issue the command:

```
sudo chmod -R 755 *
```

to change all files and folders.

---

### Post by Aximilli on 2008-06-06
> **iaculallad said:**
> What about going inside your share directory and just issue the command:

```
sudo chmod -R 755 *
```

to change all files and folders.

Well, I don't think that will help me in my ultimate goal. Let me give a little detail on what I'm trying to do, and maybe that will help to determine if that is indeed the fix I want.

This box is going to be a headless storage server for my house. Ultimately I am going to have my machine as well as both my parents (who use windows) have a network drive that points to this /share directory. I want them to have full access to add, edit, and remove files in this dir. But I do want to keep it as secure as I can since it is accessible on the internet via ssh and webmin.
 So I created a sharers group, to which I am trying to add user accounts for my parents (hopefully without passwords, to make it easier on them) which are synchronized with the Samba users group. Which is why I'd like the /share folder and all it's sub directories to be owned by that group.

I hope this explanation helps you in helping me.

Thanks
Alex

---

### Post by iaculallad on 2008-06-06
What if you just edit your smb.conf file and inlcude the following lines below:
```

[sharers]
  path = /share
  writable = yes
  printable = no
  write list =@sharers
  create mode=0770
  directory mode=0770
```

---

### Post by Aximilli on 2008-06-06
well I added that code to my smb.conf file and updated it, restarted samba, and am still unable to access my share/public directory. 

Why am i not able to just permanently change the group ownership of that dir?

Alex

---

### Post by iaculallad on 2008-06-06
Why would it not give you explicit folder ownership :confused: What about using ACL?

```
sudo apt-get install acl
```

Try changing /etc/fstab for mountpoints you wish to use the ACL.

change /etc/fstab for the mountpoint you wish to use acl.

Sample:

> /dev/sda1 /media/share ext3 defaults,**acl** 0 2

Unmount and Mount your /media/share in order to activate the ACL. Use [setfacl]("http://linuxcommand.org/man_pages/setfacl1.html") command to set your shared folder permission.

---

### Post by Aximilli on 2008-06-06
> **iaculallad said:**
> Why would it not give you explicit folder ownership :confused: What about using ACL?

```
sudo apt-get install acl
```

Try changing /etc/fstab for mountpoints you wish to use the ACL.

change /etc/fstab for the mountpoint you wish to use acl.

Sample:



Unmount and Mount your /media/share in order to activate the ACL. Use [setfacl]("http://linuxcommand.org/man_pages/setfacl1.html") command to set your shared folder permission.


I've never used ACL before and don't know how it works. I really want to try and keep this server as simple as possible. 

Is it the case that I just can't change the group ownership of this folder permanently? and why not?

and also this folder isn't in media or mnt, it's mounted into /share


Thanks for your advice
Alex

---

### Post by iaculallad on 2008-06-06
What about using thunar? I'm our of suggestions :confused::confused:

---

### Post by Aximilli on 2008-06-06
> **iaculallad said:**
> What about using thunar? I'm our of suggestions :confused::confused:

True Linux server, no gui :(

---

### Post by Aximilli on 2008-06-06
Well, the dawn of a new day brought new inspiration. I used webmin to change owner and group of my folder, remounted it and the new permissions stuck! who would have thought webmin for the win?

Thanks very much though for your suggestions.

---

