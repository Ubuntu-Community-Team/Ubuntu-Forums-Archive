---
title: "[SOLVED] Problem with permissions (again)"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-05
I thought I had sorted this out with a previous post  but unfortunately not.

I have an external vfat drive, (/media/seagate) containing all my data files & music. I have added appropriate entries to fstab to auto mount it on boot up. 

```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c64ef25f-d19f-42f2-93a4-829da848c4a9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=79dd635c-adee-4702-a5e0-b4cc9ace54a5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


[COLOR=Blue]/dev/sdc1   /media/seagate   vfat   user,fmask=0111,dmask=0000   0   0[/COLOR]

```

That works fine. However the permissions of the drive and all contained folders are set to root:root 
and when I use chown to try to change the ownership and then the mode this is what I get 

```
douglas@desktop:~$ sudo chown douglas:douglas /media/seagate
chown: changing ownership of `/media/seagate': [COLOR=Blue]Operation not permitted[/COLOR]
douglas@desktop:~$ 

```

1st question, why is the operation not permitted?
2nd question how do I set my box up that as the owner and administrator of it, I can do the things I need to do? 
3rd question, what do I need to do, to be able to access the files on /media/seagate for read and write and execute purposes as the owner?

Thanks for any help

---

### Post by riven0 on 2008-05-05
Okay, try logging in as root: **sudo -s -H**

then: **chmod ugo+rwx /media/seagate**

Does that work?

---

### Post by jimv on 2008-05-05
Change this

/dev/sdc1   /media/seagate   vfat   user,fmask=0111,dmask=0000   0   0

to this

/dev/sdc1   /media/seagate   vfat   defaults   1   0


and then type this in a terminal

sudo chown douglas /media/seagate

---

### Post by sdennie on 2008-05-05
I believe you can specifically set the owner of a vfat mount using the uid and gid options.  So, if you are the only user on your box (or the first user added), changing your fstab for the vfat partion to:

```

/dev/sdc1   /media/seagate   vfat   user,fmask=0111,dmask=0000,uid=1000,gid=1000   0   0

```

---

### Post by hyper_ch on 2008-05-05
I might be wrong but chmodding and chowning on a fat32 partition does not have any effect as it does not support linux files permissions.

As pointed out above, you'll have to add the according stuff in your fstab.

---

### Post by tropdoug on 2008-05-05
riven0 I did this and nothing appeared to change. I also thought of something after I executed the command, can you please explain what that command is, and what its syntax is telling the computer to do? I like to try and learn what it is I am doing. Thanks.

---

### Post by tropdoug on 2008-05-05
Thanks guys, (and maybe gals!) 

Jimv I decided not to try yours without first finding out what the defaults would be? could you explain a little please. 

vor, specifically setting the fstab made a lot of sense, and so I did that and rebooted and everything is fine. I did have to use the button in the properties box of seagate to set the enclosed folder permissions to the same as the drive, but now I can read and write to all my files. Again like the others could you explain a little or point me in the right direction for more learning on this subject? 

Thanks for all the help.

---

### Post by sdennie on 2008-05-05
A decent place to learn about mounting things would be to open a terminal and type:

```

man mount

```

The general information at the top and scrolling down to the section about vfat should help you understand more about mounting things (although, the information might be sometimes hard to understand if you aren't very familiar with linux).

---

