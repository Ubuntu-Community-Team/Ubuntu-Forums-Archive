---
title: "Ubuntu - windows partions not visible"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by HNovice47 on 2012-09-22
hello,
 
i have downloaded ubuntu 12.04 (32-bit) and was trying to install it on my HP 630 Notebook PC. i made a bootable pendrive of it and booted it on the laptop. but when the page to select partions (to install ubuntu) comes, i am unable to see my partions (created in windows). i had 3 partions - C, D, E of 116gb, 116gb and 232gb resp. but it shows something else only in ubuntu. it shows only two partitions. - 400gb and smthing else.
when i select live boot, it boots up nicely into ubuntu. but i want to install it on my harddisk.
pls tel me how do i fix this. how do i install ubuntu on my laptop?

---

### Post by Bucky Ball on 2012-09-23
Weclcome.

Do you have a 64bit processor? If so I advise you use the 64bit version (the AMD64 version is for ALL 64bit processors, not just AMD).  

Which version of Win are you using? Has started using EFI which apparently changed things. I don't know much about it but there's others here that do and can help. That could be the problem and somewhere to start looking. (UEFI I believe)

Something to remember: You can only have four primary partitions on one physical drive normally (EFI I think changes this). Generally, you might have three primary with an extended, inside which  you can put as many logical drives as you like (or your hardware can handle). Ubuntu happy on a logical drive inside extended, Win not.

---

### Post by HNovice47 on 2012-09-23
well, my HP 630 has intel core i3 m370 which is 64bit. but i am having windows 7 pro 32bit installed on one of the partions which runs pretty fine. i'll try downloading 64bit ubuntu as u said and see if it works......

---

### Post by Bucky Ball on 2012-09-23
Yep, even if it doesn't fix your issue that is the one you want. Run from the LiveCD then install if all good. Let us know. ;)

---

### Post by HNovice47 on 2012-09-23
no man. i tried with 64bit also. its showing the same thing. same problem.
i have a 500gb hard disk and i have made 4 partions C, D, E, F of 116gb, 96gb, 232gb and 20gb (for installing ubuntu) resp. but in ubuntu instalation setup it shows only two partions (actually 4) one 124.8gb and 374.4gb which is weird! other two are i think the hidden system partions which are 1gb and 4mb smthing.
i dont understand how to install this thing. it use to run fine on my desktop PC.
or shud i try burning it to disk or smthing?

---

### Post by coffeecat on 2012-09-23
Usually Ubuntu can see partitions that Windows will hide, so I think we need to see exactly what Ubuntu is seeing. Boot up the live CD and choose "try Ubuntu" to get to the live desktop (not "install Ubuntu"). Once you have the live desktop running, tap the super (windows) key or click on the topmost icon in the launcher at left. The dash will open. Type "gparted" and then click on the Gparted icon to open that application - it's a partitioning tool. Once it is open, don't try to do anything with it, but press the Alt and PrintScr keys together to get a screenshot of the open Gparted window. If I remember correctly, the screenshot is saved to the Pictures folder. Open the home folder by clicking on the orange folder icon in the launcher and then open the Pictures folder. Save the *png screenshot file to an external drive so that you can upload it to your post. (Unless you can post directly from the live session.)

Attach the screenshot to your next post and, hopefully, we can see what might be going on. Use the "Manage Attachments" button below the message field when you post to upload the screenshot - that will produce a thumbnail.

By the way, you said you made partitions in Windows for installing Ubuntu to. That's not the way to do it. Windows created partitions are formatted NTFS, which is not suitable for Linux, but we should be able to sort that out when we see your screenshot.

---

### Post by NikTh on 2012-09-23
Hi , 

can you give the results of bellow commands in terminal ? (Ctrl+Alt+T)

```
sudo fdisk -l 
sudo parted -l 
sudo lshw -businfo | grep scsi
``` 

Put the results between the brackets **[noparse]```
Here
```[/noparse]** 

Thanks

---

### Post by HNovice47 on 2012-10-24
this is how my laptop HDD partions appear in Ubuntu......

---

### Post by HNovice47 on 2012-10-24
and this is how they actually are in windows 7.....

---

### Post by Bucky Ball on 2012-10-24
Well, not sure what the problem is. Everything's showing up fine. You have nowhere to install Ubuntu to, though. You already have the disk filled with NTFS and FAT partitions and Ubuntu won't go there. You need free space and you need to make that free space into an extended partition then install Ubuntu there. You currently have not EXT4 partition, which is what Ubuntu uses.

---

