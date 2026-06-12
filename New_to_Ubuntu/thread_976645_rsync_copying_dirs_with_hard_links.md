---
title: "rsync copying dirs with hard links"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by daniel3ub on 2008-11-09
Hi, folks!

First, I know rsync do not move dirs. But I can copy them and them delete the source, right?

I am making backups from a directory (let's say /Daily/)in the following way:

I make a full copy into a /Daily.1/ directory, using 
```
rsync -azSvyP
```

Then, the next day, I make a backup into /Daily.2/ using hard links, with
```
rsync -azSvyPpE --link-dest=/Daily.1
```

And so on, until I have 8 /Daily.?/ directories. Then, I want to move the oldest /Daily.?/ (in this case it would be /Daily.1/) to a /Weekly.1/

The problem is that I cannot do this using cp or mv, because of the hard links. I need to keep them. So, I am trying this:
```
rsync -HzSvrpPE /Daily.1/ /Weekly.1/ 
```
as the -H says it keeps the hard links.

The copy goes on, but I've noticed that the dirs' sizes are different beetween the original copy (Daily ones) and the Weekly ones. It seems rsync is not keeping the links, but making new full copies. If, after a few days, I look into the Daily dirs, their total size will be smaller than the Weekly dirs' total size (even if the copies are supposed to be exactly the same -- a test situation, of course)) 

My questions:
1. Is there a way to prove that? Can I tell if a file is a hard link or a full copy of another file?
2. Do I have to use any other option to make the -H option work this way I need?

Thanks a lot!
As soon as I get this to work I'll share with the comunity and maybe make a GUI to my backup script :guitar:

---

### Post by unutbu on 2008-11-09
The problem is that -H requires that "both parts of the link are in the list of files being sent". See the man page for rsync. 
> 
1. Is there a way to prove that? Can I tell if a file is a hard link or a full copy of another file?

Yes. Suppose you were to run
```

% touch /tmp/a
% ln /tmp/a /tmp/z
% ls -l /tmp/{a,z}
-rw-r--r-- 2 innov innov 0 2008-11-09 15:16 /tmp/a
-rw-r--r-- 2 innov innov 0 2008-11-09 15:16 /tmp/z
           ^
           ^ This 2 indicates the number of hard links made to the same inode.
```

So if you use ls -l /Weekly.1 and don't see a number greater than 1, then you know you don't have hard links.


> 2. Do I have to use any other option to make the -H option work this way I need?

hyper_ch has written a clever backup script that uses rsync and hard links:
[http://ubuntuforums.org/showpost.php?p=6024283&postcount=7](http://ubuntuforums.org/showpost.php?p=6024283&postcount=7)

Here is a basic summary of what it does (ignoring the mysqldump'ing):
It uses rsync to copy /source to /backup/current
It then uses cp -al to make a hard-link copy of /backup/current to /backup/old/2008-11-09. Unlike what you are trying to do, he just makes a hard-link of everything.

If you delete a file in /source, it will still be in /backup/current and /backup/old/2008-11-09.

If you run the script again tomorrow, rsync will update /backup/current to look like /source. 
This copying is efficient because rsync can do incremental backup. The deleted file will no longer be in /backup/current, but it will still be in /backup/old/2008-11-09.

Now cp -al is used to make a hard-link copy from /backup/current to /backup/old/2008-11-10.
Because everything in /backup/old is a hard link, they do not take up a lot of additional space compared to the originals. Of course, if the original gets deleted, then the hard drive space is not recovered until the last hard link is deleted, but there is no getting around that -- it is a backup after all.

After a certain number of days, directories in /backup/old get deleted.

I'm not sure if this is what you are trying to do, but perhaps it may give you an idea.

Hope this helps.

---

### Post by daniel3ub on 2008-11-09
> **unutbu said:**
> The problem is that -H requires that "both parts of the link are in the list of files being sent". See the man page for rsync.

Yep, I saw this :(

> Yes. Suppose you were to run
```

% touch /tmp/a
% ln /tmp/a /tmp/z
% ls -l /tmp/{a,z}
-rw-r--r-- 2 innov innov 0 2008-11-09 15:16 /tmp/a
-rw-r--r-- 2 innov innov 0 2008-11-09 15:16 /tmp/z
           ^
           ^ This 2 indicates the number of hard links made to the same inode.
```

So if you use ls -l /Weekly.1 and don't see a number greater than 1, then you know you don't have hard links. 

Exactly. they are not hard links, as I thought...

> 
It uses rsync to copy /source to /backup/current
It then uses cp -al to make a hard-link copy of /backup/current to /backup/old/2008-11-09. Unlike what you are trying to do, he just makes a hard-link of everything.

Well, I WAS trying to make hard links of everything, too. The problem is that I was not getting hard links :)

In fact, my solution is very close to his, but I am doing this in purpose to learn a little of shell scripting, so I am using functions, file verifications and so on, trying to be the more generical possible.

Using cp -al to copy the files from the Daily dir to the Weekly dir works like a breeze.

I'll do more tests, just to make sure everything is going as planned!

> Hope this helps.
It surely helps!
Thanks a lot!

---

### Post by scheuref on 2012-09-17
yes cp -al daily.1 weekly.1 will keep the hardlinks.

but why don't you use simply mv daily.1 weekly.1 ?
it will also keep the hard links.

rsync -H folder1 folder2 keep the hard-links between files of folder1 and copy that relations into folder2.
there will be no hard links between folder1 and folder2, but the existing hard links between files of folder1 will be reproduced in folder2. 

--

you can find a script to backup the whole disk with rsync here: [http://blog.pointsoftware.ch/index.php/howto-local-and-remote-snapshot-backup-using-rsync-with-hard-links/](http://blog.pointsoftware.ch/index.php/howto-local-and-remote-snapshot-backup-using-rsync-with-hard-links/)
It uses file deduplication thanks to hard-links, uses also MD5 integrity signature, 'chattr' protection, filter rules, disk quota, retention policy with exponential distribution (backups rotation while saving more recent backups than older).
It was already used in Disaster Recovery Plans for banking companies, in order to replicate datacenters, using only little network bandwidth  and transport encryption tunnel.
Can be used locally on each servers or via network on a central remote backup server.

it is free and i hope it can suit your needs ^^ 
Francois Scheurer

---

