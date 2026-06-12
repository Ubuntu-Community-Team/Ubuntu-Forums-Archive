---
title: "Root partition seems double"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by happyusers on 2013-11-08
It seems that I have made something unusual on my root partition.
I was afraid to loose my system so I created a same size partition and, booting from my installation USB key, I copied the root partition on its clone.
When I booted again on my HDD, I was surprised to remark, running Gparted, that my TWO partitions were mounted on the same UNIQUE point (/).
It is therefore very difficult to know what is going on on each of those partitions. Whitch one is really affected by the modifications on my system? I created a new directory on my user account and surprisingly that directory was not on the main root partition but on the clone!
I am a little frightned and does not dare to do anything. Could I suppress the clone? could I prevent the system to mount both on the same point? Do you have an explanation about why are those two partitions mounted on the same point? Thank you for any clue.

---

### Post by deadflowr on 2013-11-08
What's the output of
```
sudo blkid
```
and what does the file /etc/fstab say...

---

### Post by happyusers on 2013-11-08
blkid produces that list :
/dev/sda1: UUID="532446a1-8ad2-4ffc-b659-35adcf781ec7" TYPE="ext4" 
/dev/sda3: UUID="532446a1-8ad2-4ffc-b659-35adcf781ec7" TYPE="ext4" 
/dev/sda4: LABEL="data" UUID="44ca09f6-bdba-4b70-9f14-67e446514da2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="08cacf52-91ac-4ac3-b29a-f03520f1d098" TYPE="swap" 
and /etc/fstab doesn't say anything about the mentionned partitions.
It simply states that dev/sda1 was mounted on / during installation and mounts / and swap with the UUID of sda1 and sda5 but as you can see, the UUID of sda1 and sda3 are the same.
Is it usual and isn't the UUID supposed to be unique?

---

### Post by sandyd on 2013-11-08
You can change the uuid by using
```

sudo tune2fs -U random /dev/sdXY

```
, but you have to find which drive is the original first.

The file creation you tested doesn't show which one is the original

I would take a tentative guess that it is sda1 that is your original.

If that is the case, I would run
```
sudo tune2fs -U random /dev/sda3
```
Since both partitions are identical anyways, both partitions will have all of the data before the crash, and it doesn't matter which one you pick to be your root partition. The changes that you have made after the creation of the other partition, will be lost unless you manually do a diff between the two filesystems.

---

### Post by happyusers on 2013-11-08
Thank you Sandy.
The original root partition was sda1. I built sda3 from it.
I shall try what you suggest but I suppose it's better to do it from outside booting on an USB disk.
I shall keep you informed.

edit:
Good guess it works.
I have got my 2 partitons back. Many thanks.

---

