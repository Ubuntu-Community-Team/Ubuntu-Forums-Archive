---
title: "Can't read data CD in Ubuntu 16.04"
date: 2017-01-12
forum: New to Ubuntu
---

### Post by 22qubed on 2017-01-12
I have a data CD that can be read on other computers but not on my Ubuntu 16.04 machine. My DVD drive works because I installed Ubuntu using the DVD drive. 

When I place the data CD into my DVD drive, I get the following errors:
"Unable to mount CD-R Disc - Location is already mounted". I then get a message informing me that I have just inserted a blank CD.

 The problem is that the CD is not blank. I have confirmed on other machines that the CD has data on it.

How can I get Ubuntu to read the data on my CD?

---

### Post by leunam12 on 2017-01-12
Can you read other CDs

---

### Post by yancek on 2017-01-12
> "Unable to mount CD-R Disc - Location is already mounted"

Try mounting it to a different location.  Did you remove a CD without unmounting and then put another in the drive?

---

### Post by 22qubed on 2017-01-12
No - I can not read any CDs or DVDs

---

### Post by 22qubed on 2017-01-12
> **yancek said:**
> Try mounting it to a different location.  Did you remove a CD without unmounting and then put another in the drive?

I have typed the following command in the terminal:
```
sudo lshw -C disk


``` 
which gives this information:
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0

I then typed in this command:
```
sudo mkdir /mnt/dvdrw
```
Followed by this command:
```
sudo mount /dev/dvdrw /mnt/dvdrw
```

I get the following message:
mount: no medium found on /dev/sr0

However, I had a CD located within my DVD drive. So,I had no success trying to mount the DVD to my machine.

---

### Post by linux1pacman on 2017-01-14
I had this same issue with my install years ago with install ubuntu 12.04lts used the same rom drive later to burn backup and it wouldnt detect it fixed it I removed the sata cable from raid sata  port and used a non raid motherboard port, so try another sata outlet on your motherboard. maybe?

---

