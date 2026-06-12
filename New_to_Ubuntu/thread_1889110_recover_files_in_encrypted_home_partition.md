---
title: "recover files in encrypted home partition"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by jsmtrd on 2011-11-30
I just realized I somehow overwrote the content of my /home/user/Documents/ directory. The /home/ directory is in a separate encrypted partition. I was thinking how I could possibly recover some of those files, and then I looked at the partition in gparted and that partition has over 50 gb of data in it yet. That makes me think the data may still be there some place. Please help. How can I go about figuring this out?  Right now I am using dd_rescue to copy the partition to a usb drive.

---

### Post by Redblade20XX on 2011-11-30
Don't write to the partition before looking a this!
Take a look at this : [http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/)
Before using scalpel, make sure you read the manual in depth!
Hopefully it helps! :)

- Red

---

### Post by Mark Phelps on 2011-12-01
If you can no longer access the encrypted partition, there is nothing you can do to recover files from it -- if there was, there would be no point in encryption.

---

### Post by jsmtrd on 2011-12-01
> **Redblade20XX said:**
> Don't write to the partition before looking a this!
Take a look at this : [http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-recover-deleted-filesdata-in-ubuntu-linux/)
Before using scalpel, make sure you read the manual in depth!
Hopefully it helps! :)

- Red

Thanks for the link. Scalpel looks useful. I will check it out more.

---

### Post by jsmtrd on 2011-12-01
I still have full access to partition. Since I do, it might not make any difference that the partition is encrypted, but then it might, I do not know.

---

### Post by Redblade20XX on 2011-12-01
> **jsmtrd said:**
> I still have full access to partition. Since I do, it might not make any difference that the partition is encrypted, but then it might, I do not know.

If you have full access to the drive, you should be alright. I had some files to recover on an encrypted, separate drive and scalpel got me the files I needed! :)

- Red

---

### Post by jsmtrd on 2011-12-02
> **Redblade20XX said:**
> If you have full access to the drive, you should be alright. I had some files to recover on an encrypted, separate drive and scalpel got me the files I needed! :)

- Red


That sounds good. I was afraid that scalpel would not work on an encrypted drive since those kind of tools tend to read the raw data. I am going to first figure out how to mount the partition up on another system so I do not accidentally over write any more data on it.

---

### Post by jsmtrd on 2011-12-10
I finally got started on this project. It is taking me a long time since  I have to do a lot of Goggling to figure out every step of the way.  What I have done so far:

[LIST]
[*] I used dd_rescue to make a copy of my home partition and put it on a usb drive.
[*] I mounted this file copy of the partition read only on another computer under /recoverydisk.
[*] I mounted my encrypted home, that is in the above partition under /recoveryhome.
[/LIST]
 
All the files I lost were inside the encrypted home.

So now I need to know what partition to tell extundelete to scan. It  does not seem like scanning the img file of the partition will work  since all the data on there is encrypted. Is there a virtual encrypted partition that I can point extundelete to? Or how is this suppose to work? Thanks for your help.

---

