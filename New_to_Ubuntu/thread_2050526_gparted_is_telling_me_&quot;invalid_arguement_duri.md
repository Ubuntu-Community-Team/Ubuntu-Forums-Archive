---
title: "gparted is telling me &quot;invalid arguement during seek for read on /dev/sda"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by Splodg3 on 2012-08-31
im having a problem with Gparted i have 4 OS on my laptop 
```

haydn@haydn-Satellite-Pro-T130:~$ sudo blkid
/dev/sda2: LABEL="Windows XP" UUID="9CD8FCBED8FC982A" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="38c289c7-c009-4c8b-8885-172f00c984c0" TYPE="ext4" 
/dev/sda6: LABEL="Lubuntu" UUID="ab244b09-997c-4627-9d9f-5f301e910672" TYPE="ext4" 
/dev/sda7: LABEL="Linux Mint" UUID="2eea42c8-a878-44fb-9fe6-dd2c349f6c10" TYPE="ext4" 

```
also i can boot into all the partitions and mint even shows me the partitions in its disk utility but I am unable to edit them

Any help would be appreciated

Haydn

---

### Post by androssofer on 2012-08-31
> **Splodg3 said:**
> im having a problem with Gparted i have 4 OS on my laptop 
```

haydn@haydn-Satellite-Pro-T130:~$ sudo blkid
/dev/sda2: LABEL="Windows XP" UUID="9CD8FCBED8FC982A" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="38c289c7-c009-4c8b-8885-172f00c984c0" TYPE="ext4" 
/dev/sda6: LABEL="Lubuntu" UUID="ab244b09-997c-4627-9d9f-5f301e910672" TYPE="ext4" 
/dev/sda7: LABEL="Linux Mint" UUID="2eea42c8-a878-44fb-9fe6-dd2c349f6c10" TYPE="ext4" 

```
also i can boot into all the partitions and mint even shows me the partitions in its disk utility but I am unable to edit them

Any help would be appreciated

Haydn

what where you trying to achieve? resizing?

this thread is kinda similar, give it a scan for useful info:

[http://ubuntuforums.org/showthread.php?t=1744799](http://ubuntuforums.org/showthread.php?t=1744799)

---

### Post by Splodg3 on 2012-09-01
yes I am trying to achieve resizing 

I've read through that thread and i tried sudo fdisk -l but it gave me a really strange response, then after further reading I came to the conclusion that my hard drive is corrupted, am i right?

I now can no longer run f disk to give you the result because it doesnt run on my live boot usb any more for some strange reason

---

