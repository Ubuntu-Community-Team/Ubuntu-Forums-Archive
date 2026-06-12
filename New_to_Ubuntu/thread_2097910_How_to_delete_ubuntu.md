---
title: "How to delete ubuntu?"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by Mijuca on 2012-12-24
Hi,

i recently bought my toshiba notebook without OS. And i only installed ubuntu 12.04, now i want to completely remove ubuntu from my notebook. like the day he went out from factory. without any of ubuntu files on hdd.

Please dont aks me why, i love ubuntu and i will keep using it, i just need to do that.

Thank you :)

---

### Post by SuperFreak on 2012-12-24
If you installed Ubuntu with a CD or USB Live version you can boot to that, open GParted and choose the partitions you wish to delete(depending on your install it may be one partition or several-root,home,SwAP could be separate or one) and then right click those partitions and choose delete. This is not a secure delete though, for that you would need to burn a copy of Darik Boot and Nuke ([http://www.dban.org/](http://www.dban.org/)) and boot to that and securely delete Ubuntu partitions.

---

### Post by SuperFreak on 2012-12-24
Beware if you have a Dual boot with Windows above direction will lead to problems only follow if Ubuntu is only OS on system

---

### Post by Mijuca on 2012-12-24
> **SuperFreak said:**
> If you installed Ubuntu with a CD or USB Live version you can boot to that, open GParted and choose the partitions you wish to delete(depending on your install it may be one partition or several-root,home,SwAP could be separate or one) and then right click those partitions and choose delete. This is not a secure delete though, for that you would need to burn a copy of Darik Boot and Nuke ([http://www.dban.org/](http://www.dban.org/)) and boot to that and securely delete Ubuntu partitions.


i dont get it, why it's not secure... And is there any better guide step by step for some secure complete uninstall? 

Can you explain me what i have to do?

---

### Post by Mijuca on 2012-12-24
> **SuperFreak said:**
> Beware if you have a Dual boot with Windows above direction will lead to problems only follow if Ubuntu is only OS on system

ubuntu is my only os on system

---

### Post by SuperFreak on 2012-12-24
By secure delete, I mean that it  is possible that files could be recovered by someone later. Thne way to avoid this is through overwriting the files you delete. That is why I suggested Darik Boot and Nuke
I would recommend it if you have any sensitive information on your hard drive such as financial records

---

### Post by Mijuca on 2012-12-24
Hi,

i recently bought my toshiba notebook without OS. And i only installed   ubuntu 12.04, now i want to completely remove ubuntu from my notebook.   like the day he went out from factory. without any of ubuntu files on   hdd.

Please dont aks me why, i love ubuntu and i will keep using it, i just need to do that.

Thank you :smile:

p.s. I dont have any other OS on my notebook.... only ubuntu


p.s.s and after that because i have 500gb hdd, i want to install windows 7 first on 300gb partition and on the rest ubuntu 12.04

---

### Post by howefield on 2012-12-24
Threads merged.

---

### Post by srikanthganta on 2012-12-24
did you install only ubuntu? or any other OS is there in dual boot?
IF DUAL BOOT IS THERE..u have to be very careful..
[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-using-gparted-to-partition-a-hard-disk/]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-using-gparted-to-partition-a-hard-disk/")

google this "using gparted to partition a hard disk ubuntu" there are so many tutorials.Hope this helps

---

### Post by Mijuca on 2012-12-24
> **srikanthganta said:**
> did you install only ubuntu? or any other OS is there in dual boot?
IF DUAL BOOT IS THERE..u have to be very careful..
[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-using-gparted-to-partition-a-hard-disk/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-using-gparted-to-partition-a-hard-disk/)

google this "using gparted to partition a hard disk ubuntu" there are so many tutorials.Hope this helps


read the post, i dont have dual boot. I only have ubuntu on my notebook, my notebook don't even know what is windows xD

---

### Post by srikanthganta on 2012-12-24
> **SuperFreak said:**
> Beware if you have a Dual boot with Windows above direction will lead to problems only follow if Ubuntu is only OS on system

Hi SuperFreak,
please let me know how to delete ubuntu from dual boot system? i have windows7 and ubuntu 12.04
I found some info by googling..but not clear with that.

---

### Post by Mijuca on 2012-12-24
> **SuperFreak said:**
> By secure delete, I mean that it  is possible that files could be recovered by someone later. Thne way to avoid this is through overwriting the files you delete. That is why I suggested Darik Boot and Nuke
I would recommend it if you have any sensitive information on your hard drive such as financial records

ok, tnx, is there any guide or tutorial how to do that?

---

### Post by sffvba[e0rt on 2012-12-24
> **srikanthganta said:**
> Hi SuperFreak,
please let me know how to delete ubuntu from dual boot system? i have windows7 and ubuntu 12.04
I found some info by googling..but not clear with that.

Please start a new thread in the appropriate sub-forum.


404

---

### Post by deadflowr on 2012-12-24
Follow the earlier advice and load the LiveCD of Ubuntu and open gparted.
From there click on Devices and then Create Partition Table. This will mark the drive to be reset when the operation is applied.
Since you want to re-order your partition scheme, open partition and click new. 
From there it should be fairly simple, remembering that the windows partition should be ntfs, and the linux drives can be ext4, or several other types.(ext4 recommended if you're reinstalling Ubuntu after the win7 install)
When you feel that you've set the system as you'd like it, click on the edit and click apply all operations.
So in order:
1)boot the live disk
2)open gparted
3)click on Devices and select create partition table
4)click on Partition and select new(select this for each per partition made)
5)make your partition scheme(if making an Ubuntu partition, suggest you save anywhere from 500MB to 6GB for swap)
6)apply all operations.

---

### Post by SuperFreak on 2012-12-24
@Mijuca I would suggest you go to the link I provided and have a look at the instructions there. You are basically going to burn a copy of Darik Boot and Nuke, boot to that disk and then follow the instructions on your screen. I'm sorry I can't give you a more detailed descrition

---

### Post by Georgia boy on 2012-12-24
> **Mijuca said:**
> ok, tnx, is there any guide or tutorial how to do that?

I ran across these links that might be of help to you.

[http://askubuntu.com/questions/162602/how-do-i-remove-ubuntu-wipe-hard-drive-and-install-windows-xp](http://askubuntu.com/questions/162602/how-do-i-remove-ubuntu-wipe-hard-drive-and-install-windows-xp)


[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/)



[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/some-help-removing-ubuntu-please-544966/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/some-help-removing-ubuntu-please-544966/)

Read them and see if they are of use to you.

GB

---

### Post by sffvba[e0rt on 2012-12-24
Seeing as the user is going to be re-partioning and installing Windows as well as Ubuntu after he wipes Ubuntu from his HDD I don't think the added step of using DBAN is needed.  I suggest OP simply follows deadflowr's instructions above.


404

---

### Post by SuperFreak on 2012-12-24
The OP has stated that this not a dual booting computer. 
I have given two suggestions 1) He can delete the Ubuntu partitions from a Live session of Ubuntu through GParted
2) If he needs a Secure removal of Ubuntu to  use Darik Boot and Nuke

Be aware if you use Darik it will take a bit of time to carry out the secure deletion (possibly overnight depending on the size of the hard drive), but once it is started there is no need to do anything but let it finish overwriting files

---

### Post by Georgia boy on 2012-12-24
> **SuperFreak said:**
> The OP has stated that this not a dual booting computer. 
I have given two suggestions 1) He can delete the Ubuntu partitions from a Live session of Ubuntu through GParted
2) If he needs a Secure removal of Ubuntu to  use Darik Boot and Nuke

Be aware if you use Darik it will take a bit of time to carry out the secure deletion (possibly overnight depending on the size of the hard drive), but once it is started there is no need to do anything but let it finish overwriting files


While you're talking about that, which is the better of the two? I've heard a lot of both but not in a comparison stand. Just idle curiosity in case I need something like that.

---

### Post by SuperFreak on 2012-12-24
@Georgia boy just to repeat the 2nd method with Darik Boot & Nuke is for a secure delete where there is some concern about sensitive files being recovered later( for example if you sold the computer or hard drive or gave it to charity).

we don't know why the OP wants to uninstall Ubuntu or if there are sensitive files on the disk.

---

### Post by deadflowr on 2012-12-24
> **srikanthganta said:**
> Hi SuperFreak,
please let me know how to delete ubuntu from dual boot system? i have windows7 and ubuntu 12.04
I found some info by googling..but not clear with that.

Simply boot a live disk and open gparted then select the Ubuntu partition and right-click dropdown to format to and select ntfs. Apply all operations(in the edit menu)
Reformatting will wipe out Ubuntu. And reformat it for for an extra drive for windows.

Also, I don't ever download unnecessary software to completely wipe a hard drive when dd is right there:
[http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill]("http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill")

Yes it is slow, but it does the job.

---

### Post by SuperFreak on 2012-12-24
srikanthganta is not the OP.I have  been trying to answer Mijuca

---

### Post by Georgia boy on 2012-12-24
> **SuperFreak said:**
> srikanthganta is not the OP.I have  been trying to answer Mijuca


Boy did you get stuck.;)
Look at the side ones you got.

Happy holidays

GB

---

### Post by deadflowr on 2012-12-24
> **SuperFreak said:**
> srikanthganta is not the OP.I have  been trying to answer Mijuca

You're right on that.
My bad, call it the Christmas spirit becomes me.

Happy holidays

---

### Post by Mijuca on 2012-12-24
> **deadflowr said:**
> Follow the earlier advice and load the LiveCD of Ubuntu and open gparted.
From there click on Devices and then Create Partition Table. This will mark the drive to be reset when the operation is applied.
Since you want to re-order your partition scheme, open partition and click new. 
From there it should be fairly simple, remembering that the windows partition should be ntfs, and the linux drives can be ext4, or several other types.(ext4 recommended if you're reinstalling Ubuntu after the win7 install)
When you feel that you've set the system as you'd like it, click on the edit and click apply all operations.
So in order:
1)boot the live disk
2)open gparted
3)click on Devices and select create partition table
4)click on Partition and select new(select this for each per partition made)
5)make your partition scheme(if making an Ubuntu partition, suggest you save anywhere from 500MB to 6GB for swap)
6)apply all operations.

i cant find ntfs partition type in ubuntu create new partition... is there any other name for ntfs? fat 32 maybe?

---

### Post by Mijuca on 2012-12-24
i downloaded 12.04 form ubuntu web site, and put it on dvd, and boot it with f12 on toshiba, from cd/dvd, and select third option something else and change partition.... 1. fat 32, 2. ext4.... is that ok?

---

### Post by Mijuca on 2012-12-24
please help....

---

### Post by deadflowr on 2012-12-24
> **Mijuca said:**
> i cant find ntfs partition type in ubuntu create new partition... is there any other name for ntfs? fat 32 maybe?

It's in the "file system" dropdown menu.

If you've started out and already create partition table, and are now beginning to redesign your partition layout.
The partition's  table should say unallocated.
When you create the first one it will then say /dev/sda, next row /dev/sda1, next row unaollocated. This will repeat until all space on disk has a partition set up.
Something like this

/dev/sda
 /dev/sda1
 unallocated

then this 

/dev/sda
 /dev/sda1
 /dev/sda2
 unallocated

and so forth.


Note: Hard drives have basically two types of partition, primary and logical(Some say extended, but an extended partition is a primary partition.) 
Disks can only have four primary partitions, so if need be, you can change one and only one of those primary partitions into an extended partition which can house multiple logical partitions.

It's really beyond me if it makes any sense, cuse to me it makes twilight zony perfect sense.

---

### Post by Mijuca on 2012-12-24
> **deadflowr said:**
> It's in the "file system" dropdown menu.

If you've started out and already create partition table, and are now beginning to redesign your partition layout.
The partition's  table should say unallocated.
When you create the first one it will then say /dev/sda, next row /dev/sda1, next row unaollocated. This will repeat until all space on disk has a partition set up.
Something like this

/dev/sda
 /dev/sda1
 unallocated

then this 

/dev/sda
 /dev/sda1
 /dev/sda2
 unallocated

and so forth.


Note: Hard drives have basically two types of partition, primary and logical(Some say extended, but an extended partition is a primary partition.) 
Disks can only have four primary partitions, so if need be, you can change one and only one of those primary partitions into an extended partition which can house multiple logical partitions.

It's really beyond me if it makes any sense, cuse to me it makes twilight zony perfect sense.

I already started....
1. I boot install cd from ubuntu web site
2. i selected third option, name: other, something like that...
3. make new table
4. make 2 partition. first fat32 windows, and ext4 /
5. and i clicked continue, there was error at the begining and intalation make no progres for more than  half hour...

what to do?

---

### Post by deadflowr on 2012-12-24
Wait, hold up.
If the goal is to install Windows then Ubuntu I think it would probably be easier to install windows and then follow the advice listed here:

[http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk]("http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk")

Installing Windows and then partition using the disk management feature is probably the safest way to go.

Simply installing Windows will reformat the drive ntfs, and later on you can resize and make partitions for Ubuntu.
It really is better to install windows first anyway.

---

### Post by Mijuca on 2012-12-24
> **deadflowr said:**
> Wait, hold up.
If the goal is to install Windows then Ubuntu I think it would probably be easier to install windows and then follow the advice listed here:

[http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk]("http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk")

Installing Windows and then partition using the disk management feature is probably the safest way to go.

Simply installing Windows will reformat the drive ntfs, and later on you can resize and make partitions for Ubuntu.
It really is better to install windows first anyway.

Ok, so first install windows 7 over ubuntu, and that will format whole hdd? Then use this [http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk](http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk), and after that install ubuntu?

---

### Post by Mijuca on 2012-12-24
i am now at the win 7 installation process and there is 30gb missed files? xD

Disk 0 partition 1: System reserved   100mb   free space 86mb  system
Disk 0 partition 2                    465.7gb  free space 465.7gb primary

where is 500.1gb-465.8gb? where is 35 gb? my hdd is 500

---

### Post by deadflowr on 2012-12-24
> **Mijuca said:**
> Ok, so first install windows 7 over ubuntu, and that will format whole hdd? Then use this [http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk](http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk), and after that install ubuntu?

Yes, the drive will have to be reformatted because windows can't run on an ext4 file system.
Hopefully when Windows is installed successfully, you can post back and proceed from there.

Installing Windows first saves you the expected hassle of dealing with the windows bootloader and Ubuntu problems which are sure to come up.(Windows bootloaders don't like linux file systems, but linux bootloader 'grub' is far nicer)

---

### Post by Mijuca on 2012-12-24
> **Mijuca said:**
> i am now at the win 7 installation process and there is 30gb missed files? xD

Disk 0 partition 1: System reserved   100mb   free space 86mb  system
Disk 0 partition 2                    465.7gb  free space 465.7gb primary

where is 500.1gb-465.8gb? where is 35 gb? my hdd is 500

ok but what about this?

and when installing windows do i have to make 2 partitions? one for system, and one for other.... like c is for system and installation files, and d for files... and after that where i put ubuntu?

---

### Post by deadflowr on 2012-12-24
> **Mijuca said:**
> i am now at the win 7 installation process and there is 30gb missed files? xD

Disk 0 partition 1: System reserved   100mb   free space 86mb  system
Disk 0 partition 2                    465.7gb  free space 465.7gb primary

where is 500.1gb-465.8gb? where is 35 gb? my hdd is 500

This might explain it:

[http://www.howtogeek.com/123268/windows-hard-drive-wrong-capacity/]("http://www.howtogeek.com/123268/windows-hard-drive-wrong-capacity/")

---

### Post by Mijuca on 2012-12-24
> **deadflowr said:**
> This might explain it:

[http://www.howtogeek.com/123268/windows-hard-drive-wrong-capacity/]("http://www.howtogeek.com/123268/windows-hard-drive-wrong-capacity/")


but now i am @ ubunutu try abd GParted shows me unallocated only, and it's 465.7gb

---

### Post by Hadaka on 2012-12-24
Hi, a very simple and effective way to wipe the drive is to write zero's 
across the entire drive..all sectors, all partitions. Insert a live CD or USB
at terminal issue this command..BE ADVISED ONCE ENTERED ALL DATA
WILL BE DESTROYED AND CANNOT BE RECOVERED.

```
dd if=/dev/zero of=/dev/sda conv=notrunc 
```

This takes time,so be patient.

---

### Post by deadflowr on 2012-12-24
Gparted reads as GIB which stands for gibibyte which is slightly larger than gigabyte.

When you get to the Windows disk management tool and resize(shrink the partition), you can decide to allocate some space for a D drive if you want.
You can probably leave the rest unallocated for when you install Ubuntu(use the something else feature to assign the space for Ubuntu and some swap.)

When you get to the Ubuntu installation, you probably will need to set the space as an extended partition, and then create a logical partition for Ubuntu and a linux-swap partition for the rest.

Remember once you hit 3 primary partitions, if you want to add more than one more partition, you will need to make the 4th partition an extended.

---

### Post by Mijuca on 2012-12-24
> **deadflowr said:**
> Gparted reads as GIB which stands for gibibyte which is slightly larger than gigabyte.

When you get to the Windows disk management tool and resize(shrink the partition), you can decide to allocate some space for a D drive if you want.
You can probably leave the rest unallocated for when you install Ubuntu(use the something else feature to assign the space for Ubuntu and some swap.)

When you get to the Ubuntu installation, you probably will need to set the space as an extended partition, and then create a logical partition for Ubuntu and a linux-swap partition for the rest.

Remember once you hit 3 primary partitions, if you want to add more than one more partition, you will need to make the 4th partition an extended.


ok i get it and for ubuntu partion from unalloacted change to ext4 or swap?

and thank you very much!

---

### Post by deadflowr on 2012-12-24
> **Mijuca said:**
> ok i get it and for ubuntu partion from unalloacted change to ext4 or swap?

and thank you very much!

When you set the Ubuntu partition, resize it and leave maybe 1 or 2 gb aside and select the filesystem as ext4.
Then with the remaining 1 or 2 gb select the filesystem linux-swap.
You'll know when you resize it if you set it right, and if not try again.

Of course you can skip all of this and after finishing installing windows, go and install Ubuntu and select the first install option side by side. You can scale the Ubuntu size with the graphical bar up top.

---

