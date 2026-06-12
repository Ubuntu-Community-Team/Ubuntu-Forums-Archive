---
title: "Permanent Swap File problem"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by dumasb on 2008-07-16
How do I set a permanent swapfile that will be loaded automatically at start?  I partitioned my hard drive into four segments with Windows XP on one, Ubuntu on another, Muppy on another and swapfile on the fourth.  Sometime later I changed the sizes of the partitions and and moved the swapfile around.  Now Ubuntu will not automatically use a swapfile.  I assume that it is being directed to the wrong partition.  I must terminal swapon /dev/sda3 after it has loaded to have it work with a swapfile.  It would be great if it worked as before my partition moves.  Thanks in advance for any help offered....

---

### Post by Elfy on 2008-07-16
Run this command

```
df -h
```
Make sure that swap is on first, note which partition is the swap one
Run this command to find UUID
```
sudo blkid
```
Then open the fstab file to edit it after backing it up

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Use the info from df- h and blkid to get the right UUID for the swap partition and change the fstab line's UUID to match.

Close and save

Check it's ok with 
```
sudo mount -a
```

---

### Post by cdtech on 2008-07-16
forestpixi is so correct.

Here's the way mine looks:
```
########## swap partition sda5 - 5G
UUID=895c93de-63d5-468f-99b7-d0f70696928b	 none            swap    sw     0       0
```

---

### Post by drs305 on 2008-07-16
Once you have identified the correct UUID of the swap partition, you should probably do these as well to give suspend/hibernation the best chance of working ;-)

```
gksu gedit /etc/initramfs-tools/conf.d/resume

```
Make sure the UUID is correct.

Then run this:
```
sudo update-initramfs -u
```

---

### Post by Elfy on 2008-07-16
> **drs305 said:**
> Once you have identified the correct UUID of the swap partition, you should probably do these as well to give suspend/hibernation the best chance of working ;-)

```
gksu gedit /etc/initramfs-tools/conf.d/resume

```
Make sure the UUID is correct.

Then run this:
```
sudo update-initramfs -u
```

I shall write that down in my little book of things I've got written down.

I never use hibernate or suspend so have never had to look at doing anything other than turning it on - swap that is :)

Didn't even know that file existed.

---

### Post by dumasb on 2008-07-16
> **forestpixie said:**
> Run this command

```
df -h
```
Make sure that swap is on first, note which partition is the swap one
Run this command to find UUID
```
sudo blkid
```
Then open the fstab file to edit it after backing it up

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Use the info from df- h and blkid to get the right UUID for the swap partition and change the fstab line's UUID to match.

Close and save

Check it's ok with 
```
sudo mount -a
```
You are the man!!!  Thank you very much!  It all worked perfectly.

---

### Post by dumasb on 2008-07-16
> **cdtech said:**
> forestpixi is so correct.

Here's the way mine looks:
```
########## swap partition sda5 - 5G
UUID=895c93de-63d5-468f-99b7-d0f70696928b	 none            swap    sw     0       0
```
You are correct.  Forestpixi was right on.  Thanks for your reply

---

### Post by dumasb on 2008-07-16
> **drs305 said:**
> Once you have identified the correct UUID of the swap partition, you should probably do these as well to give suspend/hibernation the best chance of working ;-)

```
gksu gedit /etc/initramfs-tools/conf.d/resume

```
Make sure the UUID is correct.

Then run this:
```
sudo update-initramfs -u
```
I did as you recommended and it was a nice follow-up to my original problem.  Thanks for your help and suggestions.

---

