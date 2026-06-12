---
title: "Trying to add/mount a second hard drive"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-17
Sorry if this is a silly post, but I have tried searching and can never quite find what I need...maybe I am not using the search very well.

But simply, I have a computer with a 80gb HDD and a 250GB HDD. The 80GB is partitioned into 3 for '/', '/home' and swap. This is my main working HDD.

I have formatted the second 250GB HDD to primary ext2 in gparted.

Now I want to simply be able to use this second 250gb hdd as extra storage space as this is on a server. I was thinking, if it just mounted as a simple directory or something, I could just create a 'link' in my shared directory to that 250gb hdd.

Basically, I have shared a directory in my /home with samba, for people to use as storage space on the server. So whether ubuntu or windows users log on, they will see this shared folder and within that there will be a directory they can go into which is really reading into the larger 250gb hdd.

Am I explaining myself ok?

Cheers in advance.

---

### Post by kpkeerthi on 2008-06-17
** I suggest you format the 250Gb volume as **ext3** instead of ext2 **

1. Create a folder, where you want to mount your 250 GB volume
```
sudo mkdir /media/Data
```

2. Connect the drive to your PC and find the device name using 
```
sudo fdisk -l
```
* I assume fdisk reports the new 250 GB volume as **/dev/hdb1**

3. Edit /etc/fstab
```
gksudo gedit /etc/fstab
```

4. Add this line to the end of the file
```
/dev/hdb1  	/media/Data  	ext3  	defaults  	0 2
```

5. Save and Exit.

6. To mount the new partition, type
```
sudo mount -a
```
If this works, the partition should mount automatically next time you reboot.

7. /media/Data will be owned by root. If you would like to change that
```
sudo chown -R user_name:group_name /media/Data
```
  * Usually group_name is same as your user_name 

Now, create a shortcut in your $HOME directory to /media/Data.

**EDIT:** Be sure to change /dev/hdb1 to whatever appropriate in your set up, as reported by fdisk from Step 2.

---

### Post by jcr1 on 2008-06-17
Brilliant! Thanks for that. I will try that out as soon as I get home. Just what I needed.

Can I ask for a little explanation to why ext3 is preferable to ext2?

Thanks again.

---

### Post by ByteJuggler on 2008-06-17
> **jcr1 said:**
> Brilliant! Thanks for that. I will try that out as soon as I get home. Just what I needed.

Can I ask for a little explanation to why ext3 is preferable to ext2?

Thanks again.

EXT3 is EXT2 with journaling added on.  Basically it helps maintain a consistent state in the filesystem at all times.  If the filesystem experiences a partial update/crash (e.g. power outtage during filesystem structure update) then the journal helps recover from this, and recovery takes a fraction of the time it would take without it (e.g. on EXT2.)  For more see [here.]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html")

---

### Post by jcr1 on 2008-06-17
Hmm, On my main HDD (the 80gb one) where '/' and '/home' are located, I think that is a ext2 partition... Should and can I reformat this to ext3 without having to reinstall? 

Sounds like a 'no' to me, but linux keeps surprising me.

---

### Post by kpkeerthi on 2008-06-17
> **jcr1 said:**
> Hmm, On my main HDD (the 80gb one) where '/' and '/home' are located, I think that is a ext2 partition... Should and can I reformat this to ext3 without having to reinstall? 

Sounds like a 'no' to me, but linux keeps surprising me.

No. If you reformat to ext3, you'll loose your data. I suggest you reinstall and choose ext3 this time.

---

### Post by MasterSander on 2008-06-17
> **kpkeerthi said:**
> 
4. Add this line to the end of the file
```
/dev/hdb1  	/media/Data  	ext3  	defaults  	0 2
```


Shouldn't that be 0 1 at the end, doesn' it start counting at 0? (I could be wrong here, looking for confirmation)

---

### Post by bumanie on 2008-06-17
Re converting ext2 to ext3 without data loss, is apparently possible. I would backup before doing it though. Here's a guide - do at own risk. [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)
Please be aware it is a conversion _not_ a format. A format would definitely get rid of your data.

---

### Post by kpkeerthi on 2008-06-17
> **MasterSander said:**
> Shouldn't that be 0 1 at the end, doesn' it start counting at 0? (I could be wrong here, looking for confirmation)

Good catch. Basically it should be +1 of the previous ext3 entry.

---

### Post by jcr1 on 2008-06-17
Brilliant!! All working!

Thank you ever so much!

---

### Post by bodhi.zazen on 2008-06-17
> **MasterSander said:**
> Shouldn't that be 0 1 at the end, doesn' it start counting at 0? (I could be wrong here, looking for confirmation)

> **kpkeerthi said:**
> Good catch. Basically it should be +1 of the previous ext3 entry.

No. The 6th column is asking if the partition should be checked for errors at boot.

0 = no

1 = check first and is used for your root partition /

2 = check after root.

There are no additional options.

> The sixth field, (*fs_passno*), is used by the ***[fsck]("http://linux.die.net/man/8/fsck")**(8)* program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a *fs_passno* of 1, and other filesystems should have a *fs_passno* of 2. Filesystems within a drive will be checked sequentially, but filesystems on different drives will be checked at the same time to utilize parallelism available in the hardware. If the sixth field is not present or zero, a value of zero is returned and **fsck** will assume that the filesystem does not need to be checked.[http://linux.die.net/man/5/fstab](http://linux.die.net/man/5/fstab)

---

