---
title: "Replace Ubuntu with newer version"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Krabby.Linux on 2012-04-28
I need to replace Ubuntu 11.10. I dont want to talk about the reasons why i cant use 11.10 and why i cant use update-manager. I asked and nobody in this forum could help me :-).

So I have installed Windows 7 AND Ubuntu 11.10.

I have the Install CD of Ubuntu 12.04 LTS. Now i want that Ubuntu 12.04 formats the partition of ubuntu 11.10 WITHOUT touching Windows7.

Now i start the installation and there i have a window where i have to chose where to install Ubuntu.

sda1 unknown
sda2 ntfs
sda3 ntfs
sda6 ext4
sda7 swap
sda5 fat32

I guess sda2 and/or sda3 are Windows partitions because of the NTFS.

I dont understand what i have to to. It seems that my old ubuntu installation is sda6. Do i need to DELETE sda6 first? There is no button where i can say use THIS Partition :(.

Thanks

---

### Post by kc1di on 2012-04-28
> **Krabby.Linux said:**
> I need to replace Ubuntu 11.10. I dont want to talk about the reasons why i cant use 11.10 and why i cant use update-manager. I asked and nobody in this forum could help me :-).

So I have installed Windows 7 AND Ubuntu 11.10.

I have the Install CD of Ubuntu 12.04 LTS. Now i want that Ubuntu 12.04 formats the partition of ubuntu 11.10 WITHOUT touching Windows7.

Now i start the installation and there i have a window where i have to chose where to install Ubuntu.

sda1 unknown
sda2 ntfs
sda3 ntfs
sda6 ext4
sda7 swap
sda5 fat32

I guess sda2 and/or sda3 are Windows partitions because of the NTFS.

I dont understand what i have to to. It seems that my old ubuntu installation is sda6. Do i need to DELETE sda6 first? There is no button where i can say use THIS Partition :(.

Thanks
just choose sda6 it's the only linux partion on the system ubuntu will format it and replace 11.10 with 12.04.
good Luck and as Always [COLOR="Red"]**(BACK UP IMPORTANT DATA FIRST!)**[/COLOR]

---

### Post by Paqman on 2012-04-28
One of the options the install disk gives you should be to install over your old 11.10 without having to get down to individual partitions. Have you selected manual partitioning? (as in the "do something else" option?)

If you are doing it manually all you need to is assign sda6 the mount point / and tick the option for it to be formatted. You can tell it to use your existing swap partition.

---

### Post by grahammechanical on 2012-04-28
There is another way. In Linux we have choice.

1) Load 11.10.

2) put the 12.04 DVD in the drive.

3) you should get an option to upgrade 11.10 from the 12.04 DVD.

If you are going to use the other method you must first select the partition (click on the line that says sda6, it will change colour to orange) then select Change. Then from the dialogue box you select the partition to be ext4 and you tick format and then give it a mount point of /  then click continue.

Regards.

---

### Post by Krabby.Linux on 2012-05-03
> **grahammechanical said:**
> There is another way. In Linux we have choice.

1) Load 11.10.

2) put the 12.04 DVD in the drive.

3) you should get an option to upgrade 11.10 from the 12.04 DVD.

If you are going to use the other method you must first select the partition (click on the line that says sda6, it will change colour to orange) then select Change. Then from the dialogue box you select the partition to be ext4 and you tick format and then give it a mount point of /  then click continue.

Regards.

My 11.10 does not work. I dont have a GUI. Only the console :-)

---

### Post by TBABill on 2012-05-03
Then best bet is to fire up a live session of 12.04 and do as stated above by manually directing the install to sda6. Sometimes it'll just pick up your existing swap partition without having to assign it, but in either 11.10 or 12.04, can't remember which, it actually created a new one when I did that so you may want to actually assign it to prevent wasting additional space on the HDD with an unnecessary partition.

---

### Post by Krabby.Linux on 2012-05-03
> **grahammechanical said:**
> There is another way. In Linux we have choice.

1) Load 11.10.

2) put the 12.04 DVD in the drive.

3) you should get an option to upgrade 11.10 from the 12.04 DVD.

If you are going to use the other method you must first select the partition (click on the line that says sda6, it will change colour to orange) then select Change. Then from the dialogue box you select the partition to be ext4 and you tick format and then give it a mount point of /  then click continue.

Regards.

I did exactly what you told me. It worked perfectly! Thank you.

THANKS to all of you :-)

How can i mark this thread as solved ?

---

### Post by QIII on 2012-05-03
Toward the top, look for the "Thread Tools" drop down selection.

---

