---
title: "Can't boot 11.10 anymore"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by bob brazie on 2012-03-12
It was working fine for months and now it won't boot into the gui.

I can't take a screen shot so I took a picture. <g>

Mentions sata quite a bit. Hard drive?

Any help would be greatly appriciated.

Thanks in advance. Bob.

---

### Post by NikTh on 2012-03-12
Hi , 
Its seems that something wrong here with your partitions. Try something : 
Boot from Ubuntu LiveCD and " Try Ubuntu" .
Open terminal and do ```
sudo fdisk -l
sudo fsck -f -p dev/sd? 
```where dev/sd? must be your linux partition. From fdisk -l output you can locate linux patrition by number 83
Good Luck

---

### Post by bob brazie on 2012-03-13
Thanks I will try this afternoon. (usa pst) When I installed Ubuntu was the only partition. Will this matter?

---

### Post by NikTh on 2012-03-13
> **bob brazie said:**
> 
 When I installed Ubuntu was the only partition. Will this matter? I don't think so. That you have only Ubuntu partitions will do thinks less tricky. I mentioned the number 83 , because you will see 82 number also. But 82 is swap memory and fsck will not check or repair it. 
From screenshot seems that you have problem with Ext4 filesystem . So 83 number refers either to /home or /root partitions. Try to Check them and repair them with fsck.

---

### Post by bob brazie on 2012-03-13
OK it is 83.

What is the command to use. 

sudo fsck -f -p 83

Thanks, Bob.

---

### Post by bob brazie on 2012-03-13
OK sorry.

I enter fsck -f -p dev/sd2 and all it tells me:

fsck from util-linux 2.19.1

Help! <g>

Bob.

---

### Post by bob brazie on 2012-03-13
OK, sorry again.

The command is: fsck -f -p /dev/sda2

Linux is on 1 so I tried fsck -f -p /dev/sd1 and it said the system clock was set sometime in the future and it said it fixed that. Still can't boot.

I have a /dev/sda 1,2 and 5. 5 is the swap file. No 4 is shown.

Any ideas?

Thanks, Bob.

---

### Post by NikTh on 2012-03-15
Hi ,
Please , try again 
```
sudo umount /dev/sda1 
sudo fsck -p /dev/sda1
``` 
Thanks

---

### Post by bob brazie on 2012-03-15
I was desperate to get back up and running so I did another clean install and in the end lost some data that was not backed up.

Live and learn I guess.

Bob.

---

