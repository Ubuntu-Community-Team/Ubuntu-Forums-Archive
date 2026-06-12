---
title: "[SOLVED] Rest of /home on another drive, how?????"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-10
Hi Gang

I asked this a few weeks ago but in a different way.
So I thought I would reword it and simplify my question.

On the main hard drive sda1 I made a separate partition for /home
Here also resides /home/user1 /home/user2 etc.

If I wanted to move or add more users and have the data on a second hard drive, should the partition read

/home/user3
or just
/user3

OR

Do I have to make a folder on sda1 first named /home/user3 and then BIND it to sdb1 /user3
OR is their a FILE similar to fstab where I have to POINT TO the location for /user3 ?????

Then of course comes the tricky part, fstab should always MOUNT either the entire drive or the /home directory, BUT there is already a home directory on sda1 so I know I can't do that.

Maybe I could make a file on sda1 called /home/allusers
then on sdb1 have /allusers/user3  /allusers/user4 so I could MOUNT the file /allusers ?????

I've already tried the things in my previous post and it didn't work, messed things up royally in fact.

So, how do folks spread user data out across several hard drives anyhow?????

Just point me to something to read on doing this, because I can't find anything using this search or google search.  Everything I read is pointing to a partition on sda1, sda2, etc.

Thanks
TTUL
Gary

---

### Post by handydan918 on 2008-11-10
/home and symlinks [explained here.]("http://sblinux.org/pages/symlink-home.html")

---

### Post by Kellemora on 2008-11-19
Hi HandyDan

I've studied this web site for a week now, and although it does an excellent job of explaining how to link the symlinks and set up fstab, it still fails completely to show HOW to name the files.

Silverbear is using the normal /home/user directory and has sub directories of /home/user/music, /home/user/documents/, etc.  on sda.

But nowhere does he say exactly HOW he is using sdb for these files.

I've already tried (as example only) /home/user/music on sdb.  Error, more than one /home directory!
So then I tried just /user/music.  Error, user by that name already exists.

I'm doing something wrong, just haven't figured out what yet.

TTUL
Gary

---

