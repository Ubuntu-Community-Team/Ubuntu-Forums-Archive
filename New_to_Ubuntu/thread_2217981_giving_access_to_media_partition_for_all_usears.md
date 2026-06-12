---
title: "giving access to media partition for all usears"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by rahul_bhise on 2014-04-19
i have a media partition on my hard disk on which i store all the photoes, videoes, and music. i have 4 usears.
i mount the media partition on /mnt/media . 
fstab......
```
# media was on /dev/sda6 during installation
UUID=52b3caf3-17d3-4b85-9762-f0c81052701d	/mnt/media	ext4	defaults		0	2
```
i want all the usears should be able to read, delete and copy.
now they can only read the files. cant delete or copy.

---

### Post by 3rdalbum on 2014-04-19
```
sudo chmod a+rwx /mnt/media
```

All users (a) will gain (+) the ability to read, write and execute (rwx) the contents of the mountpoint /mnt/media.

---

### Post by kc1di on 2014-04-19
Hi rahul_bhise, 

One way is to go to a terminal and type the following command:

```
sudo chmod 777 -R /mnt/media
```

That gives everyone permission to read/write and exicute those files. 
good luck. 

Another Way would be to go to a Terminal and type the following:
```
sudo nautilus <assuming your using unity>
```
Enter your password when asked.  
When nautilus comes up navigate to the media folder > right click on the folder and click on the properties line.  
When the dialogue box comes up > click on the permissions tab and change the permissions for each category.

---

### Post by rahul_bhise on 2014-04-25
```
sudo chmod 777 -R /mnt/media
```
this did the job. thankys friends
and sorry for the late responce

---

