---
title: "Mounting Unkown USB hard drive"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Pethegreat on 2008-07-02
I am running Ubuntu 8.04 and I have a 320gb external no-name hard drive that i want to use. The light shows that the drive is working properly. I can't find the drive listed in my computer. 

A generic USB drive files shows up in my /dev/disk/by-id I have a sdb listed in /dev I made a directory for sdb in /media and used the command to mount it

```
sudo mount /dev/sdb /media/sdb
```

I got a red light on the drive, and the error 
```
mount: mount point /media/sbd does not exist

```

The drive enclosure does not state that is supports linux. Am I screwed?

---

### Post by Dr Small on 2008-07-02
Does this disk have anything on it? If not, you need to partition in with gParted and give it a filesystem. Then, mount the partition on it:
```
sudo mount /dev/sdb1 /media/sdb
```


Edit,
And of course, /media/sdb must exist.

---

### Post by sayakb on 2008-07-02
```
sudo mkdir /media/sdb
```
And then mount it.

---

### Post by Pethegreat on 2008-07-02
I made sure i had /media/sdb created before I tried what I did. So I was heading in the right direction. 

So I am going to let it format the drive in ext3. 

Now what is the best way to copy a whole drive over to the usb drive? I am upgrading to a larger drive in my laptop.

---

### Post by james_vanb on 2008-07-02
This might point you in the right direction:

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

Found thread through K.Mandla's Tip of the Week - You might want to Bookmark - Good stuff:

[http://ubuntuforums.org/showthread.php?t=655207&page=2](http://ubuntuforums.org/showthread.php?t=655207&page=2)

---

