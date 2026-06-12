---
title: "no write access to extra partition."
date: 2008-08-22
forum: New to Ubuntu
---

### Post by pjones0404 on 2008-08-22
i recently got a new laptop and installed ubuntu on it. I have a partition for windows, a partition for ubuntu and one other partition. I do not have access to the extra partition. it is formatted ext3 and i can access it but can not add files or folders. what do i need to do to change the permissions on this partition? I have full access to the windows partition though.

thanks in advance fro any help.

---

### Post by alienexplorers on 2008-08-22
you could run in terminal:
> gksudo nautilus
go to the root file where that partiton is and
look at the permissinons for that directory.  If
it is set to root then change it to your name and group.
close nautilus and see if you can write to that directory.

---

### Post by pjones0404 on 2008-08-22
thanks for the reply.

i ran the command and changed the owner from root to my name and the group as well. after closing nautilus and trying again i am still unable to access the partition with write permission. I looked in the properties and it changed back to root for owner and group. 

any other things that i can try. I had a separate partition on a different laptop and it worked right away no issues. I created this partition during the install of ubuntu to save all of my media to.

---

### Post by alienexplorers on 2008-08-22
I had a partition like that and using the gksudo natilus fixed the problem.  Sorry it did not work for you.

---

### Post by Too Late on 2008-08-22
Go to terminal and type:
```
ls -ld /mountpoint
```
where the /mountpoint is the full path to your partition.

edit: Sorry, didn't notice that you've already said that it changed the owner back to root. So nothing to see here...

edit 2: Ok, I don't understand, why Nautilus doesn't work. However, go to terminal and type:
```
sudo chown $USER: /mountpoint
```
That should do the same thing.

---

### Post by Too Late on 2008-08-22
nothing... edited my previous post

---

### Post by pjones0404 on 2008-08-22
thanks again for the responses. I restarted x and it did save the information. i am now able to access it no problem. i appreciate the help. 

one other question regarding this extra partition. how can i rename it? currently it is called 105 GB media. is there a way to change this to something else?

---

### Post by tuxulin on 2008-08-22
this might be dumb but can you try this

cd to the mountpoint of the partition (maybe in the /media directory

once there do a ls -l and look again at the owner and group for that partition

if what you see is not your user names then do this
sudo chgrp <your-user> <the mount directory>
chown <your-user> <the mount directory>

then do "ls -l" again

are you saying the owner and group has reverted back to what it was before. if not then type "nautilus" and now try to copy some files 
to the partition.

can you also print here you fstab here and recheck your own permissions

thanks
Tuxulin

edit i posted too late --- problem solved

---

### Post by tuxulin on 2008-08-22
to change the partition name i think its done in 3 ways, by the way,
fstab sees drives by uuid. so 1st thing to do is backup 
your fstab

then use fdisk -l, gparted or do it in fstab to change the name

to get your uiid number do this in termail
ls /dev/disk/by-uuid -alh

Tuxulin

---

