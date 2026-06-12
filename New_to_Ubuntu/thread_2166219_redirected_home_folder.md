---
title: "redirected home folder"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by AIM Systems on 2013-08-08
Some background info:
In the interest of privacy and saving space, I've relocated my home directory as such:
/dev/sda1     /                  15G
/dev/sda2     swap            8G
/dev/sda3     /datastore     1.66T

/etc/passwd records my home directory as /home/<myusername> but I've moved it to /datastore/<myusername> and put a (dereferenced) symbolic link in its place.
i.e. I own the link, not root

lrwxrwxrwx 1 myusername myusergroup 21 May 4 10:05 myusername -> /datastore/myusername

Here is a noob question.
When I open a terminal, my prompt is:
myusername@PC-Name:/datastore/myusername$
pwd: /datastore/myusername

What I want is my prompt to be:
myusername@PC-Name:~$
pwd: /home/myusername

I don't want any hint that my home directory is other than where it ought to be.
any ideas?

p.s. my .bashrc is unaltered so I have not posted it here

---

### Post by linuxonbute on 2013-08-08
Could you post the results of the following:
```


sudo fdisk -l

mount

```

---

### Post by SlugSlug on 2013-08-08
You'd be a lot better off moving home to the other partition
[https://help.ubuntu.com/community/Partitioning/Home/Moving#Copy_.2BAC8-home_to_the_New_Partition](https://help.ubuntu.com/community/Partitioning/Home/Moving#Copy_.2BAC8-home_to_the_New_Partition)

Makes your next install a lot nicer easier too

---

### Post by 3rdalbum on 2013-08-08
What you need to do is to mount /dev/sda3 into /home and change /etc/passwd back to what it should be (because your home directory will be literally mounted under /home/<username>

So, change the /etc/passwd entry, go into /etc/fstab and create a new line there mounting /dev/sda3 to /home/ and reboot.

---

### Post by oldfred on 2013-08-08
I use data partitions but link the folders in the data partitions back into /home. 

 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

