---
title: "Can't install Ubuntu 12.04 LTS alongside win7 x64 :("
date: 2013-05-17
forum: New to Ubuntu
---

### Post by peshmerge on 2013-05-17
Hello everybody, i am a newbie with Linux. I have " Asus R500VD-SX403H ", and i tried to install Ubuntu 12.4 LTS, but i couldn't do that . During the installation i don't have the selection "Install alongside win7 ".Although i have just 2 primary partitions and the others are logical.When i choose " something else "" it just shows me a whole hard disk.
I have tried many solutions but i cann't install it !!!!!!!

Anyone can help me with that ?????

---

### Post by Shivakumara on 2013-05-17
Best solution would be to create separate partition for the Ubuntu and install. you can make some space with disk shrink option of disk management in windows 7. you will get some unallocated space. create a new partition out of this unallocated space and install in that.

Thanks
Shivu

---

### Post by Mark Phelps on 2013-05-17
BEFORE you do that, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that in order to restore the Win7 boot capability, should that become damaged as a result of your dual-boot installation.

---

### Post by uzumakifahim on 2013-05-17
Actually you need to create a separate partition for Ubuntu first. To do that, clean up one of your partition's data, then boot ubuntu from USB or CDROM. After this follow the steps mentioned in the link below : 
[http://opensource-sidh.blogspot.com/2012/04/ubuntu-1204-installation-dual-boot-with-windows.html](http://opensource-sidh.blogspot.com/2012/04/ubuntu-1204-installation-dual-boot-with-windows.html)

Keep in mind that, in the step 3 choose something else and click next. Now you'll see all your partitions, select your desired partition and follow the step 5 and go on.

Hope you'll enjoy the great experience of Linux. Wecome to this world.

---

### Post by peshmerge on 2013-05-19
First Thanks for all ^_^
Second sorry for being late to replay :(

> **Shivakumara said:**
> Best solution would be to create separate partition for the Ubuntu and install. you can make some space with disk shrink option of disk management in windows 7. you will get some unallocated space. create a new partition out of this unallocated space and install in that.

Thanks
Shivu
I have already done this step !!!! but it didn't worked. Thanks a lot bro!

> **Mark Phelps said:**
> BEFORE you do that, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that in order to restore the Win7 boot capability, should that become damaged as a result of your dual-boot installation.
Thanks a lot  bro!
> **uzumakifahim said:**
> Actually you need to create a separate partition for Ubuntu first. To do that, clean up one of your partition's data, then boot ubuntu from USB or CDROM. After this follow the steps mentioned in the link below : 
[http://opensource-sidh.blogspot.com/2012/04/ubuntu-1204-installation-dual-boot-with-windows.html](http://opensource-sidh.blogspot.com/2012/04/ubuntu-1204-installation-dual-boot-with-windows.html)

Keep in mind that, in the step 3 choose something else and click next. Now you'll see all your partitions, select your desired partition and follow the step 5 and go on.

Hope you'll enjoy the great experience of Linux. Wecome to this world.

Thanks a lot bro!


These are fotos describe my situation : this my laptop's bios 
[ATTACH=CONFIG]242771[/ATTACH][ATTACH=CONFIG]242772[/ATTACH][ATTACH=CONFIG]242773[/ATTACH][ATTACH=CONFIG]242774[/ATTACH][ATTACH=CONFIG]242775[/ATTACH]


Ohers fotoes in the next post !

---

### Post by peshmerge on 2013-05-19
You can notice  that i have 19 GB free ,but when i try to choose " something else " during installation, it shows me the whole hard disk , not the 19GB ...
i AM JUST confused, i have tried all solutions on the web !!!!!!!!!!!



[ATTACH=CONFIG]242776[/ATTACH][ATTACH=CONFIG]242777[/ATTACH][ATTACH=CONFIG]242778[/ATTACH][ATTACH=CONFIG]242779[/ATTACH]

---

### Post by peshmerge on 2013-05-20
> **Mark Phelps said:**
> BEFORE you do that, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need that in order to restore the Win7 boot capability, should that become damaged as a result of your dual-boot installation.

Bro!! can u help me??? :icon_frown: i have posted all pics about my situation!!

---

### Post by fantab on 2013-05-21
Did this laptop come pre-installed with Windows8 and that you later installed Windows 7?

Firstly, you have 'Secure Boot' enabled in BIOS. This usually indicates that you had Windows8, but its not a must. Try 'disabling' "Secure boot".
Secondly, your laptop appears to have UEFI enabled, which means the HDD had GPT table, Did you change the table to MBR/msdos? 

Its bit confusing. Please clarify the above.

---

### Post by peshmerge on 2013-05-21
> **fantab said:**
> Did this laptop come pre-installed with Windows8 and that you later installed Windows 7?

Firstly, you have 'Secure Boot' enabled in BIOS. This usually indicates that you had Windows8, but its not a must. Try 'disabling' "Secure boot".
Secondly, your laptop appears to have UEFI enabled, which means the HDD had GPT table, Did you change the table to MBR/msdos? 

Its bit confusing. Please clarify the above.

Hi :) Thanks for replay !!
My laptop came with pre-installed Win8 and then i replaced win8 with Win7 .I tried before to disable Ubuntu with disabling 'Secure Boot' but also didn't work :(
My laptop has UEFI enabled,i agree with u bro !. But how can i change it to MBR/msdos??

---

### Post by fantab on 2013-05-21
I suspect that you have already changed it to 'msdos' and that is what is perhaps, causing the problem. Can you boot Windows 7, is it working? 
Boot with Ubuntu CD/DVD/USB that you have and "Try Ubuntu", let the desktop load. Establish connection to internet. Open Terminal, Ctrl+Alt+T, and run the following command and post its output:

```
sudo parted -l
```

---

### Post by peshmerge on 2013-05-21
> **fantab said:**
> I suspect that you have already changed it to 'msdos' and that is what is perhaps, causing the problem. Can you boot Windows 7, is it working? 
Boot with Ubuntu CD/DVD/USB that you have and "Try Ubuntu", let the desktop load. Establish connection to internet. Open Terminal, Ctrl+Alt+T, and run the following command and post its output:

```
sudo parted -l
```

This is output :

```
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?
```



when i choose yes :

```
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!  

```

When i choose no :

```
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!  

```

---

### Post by fantab on 2013-05-21
As suspected your partition table is corrupted. Instead of trying to fix I suggest you recreate the partition table. Recreating partition will wipe out the entire disk. If there is any data to to saved then do so now.

Before I tell you how to create new partition table, it will be good if you know about MBR/msdos table and GPT.

MBR is Legacy, its part of BIOS and more than 30yrs. old and has limitations with newer hardware. Plus, with MBR you can only have FOUR primary partitions. If we want more then we have create FOURTH partiton as EXTENDED and within it we can create upto 128 LOGICAL Partitions. It cannot support Hard Drive more than 2TB

GPT is new. Built to overcome the limitations of 'msdos'. It is the future. It is part of UEFI, the alternative to BIOS. Almost all newer computers and MotherBoards come with UEFI... The immediate advantage of GPT is that it can have upto 128 PRIMARY partitions and it is compatible with both BIOS and UEFI. It supports Hard Drives more than 2TB.

With GPT windows will only boot with UEFI. Ubuntu can boot from GPT in both BIOS and UEFI. But to dual boot both OS must be either in BIOS or UEFI.

How do you want it? If you ask me, go with UEFI. We can also go BIOS way if you insist. You can read on www all about BIOS and UEFI and decide.

But First, Go into your UEFI/BIOS set up and DISABLE "Secure Boot". If you Don't want UEFI then disable that as well.

Creating New partition table:
1. Boot with Ubuntu CD/USB and "Try Ubuntu". After the desktop is ready, establish internet connectivity.
2. [Download and run FIXPARTS]("http://www.rodsbooks.com/fixparts/") to cleanup your Hard Disk of leftover GPT from Windows8 time. Running Fixparts is simple just read the link carefully.
3. Open GPARTED. From the right hand side choose the correct Drive. Select the partition, right click and Delete. Delete all the partitions. From the Menu Bar choose Device and then "Create new partition table". The default will be 'msdos', to choose GPT you have to Advanced. (Choose one wisely).
4. close Gparted and shutdown.

If you chose UEFI then to install Windows 7 follow this: [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

Some computers have a problem installing Windows7 from UEFI with DVD, in that case you have to install Windows7 from USB.

Once you have Winodows 7 installed as instructed get back here and we'll tell you how to go about Ubuntu_UEFI_GPT.

(If you choose BIOS then you don't need any special instructions. Go ahead and install both OS)


If you have anymore doubts then you are welcome to clear them.

Good Luck...

---

### Post by peshmerge on 2013-05-22
> **fantab said:**
> As suspected your partition table is corrupted. Instead of trying to fix I suggest you recreate the partition table. Recreating partition will wipe out the entire disk. If there is any data to to saved then do so now.

Before I tell you how to create new partition table, it will be good if you know about MBR/msdos table and GPT.

MBR is Legacy, its part of BIOS and more than 30yrs. old and has limitations with newer hardware. Plus, with MBR you can only have FOUR primary partitions. If we want more then we have create FOURTH partiton as EXTENDED and within it we can create upto 128 LOGICAL Partitions. It cannot support Hard Drive more than 2TB

GPT is new. Built to overcome the limitations of 'msdos'. It is the future. It is part of UEFI, the alternative to BIOS. Almost all newer computers and MotherBoards come with UEFI... The immediate advantage of GPT is that it can have upto 128 PRIMARY partitions and it is compatible with both BIOS and UEFI. It supports Hard Drives more than 2TB.

With GPT windows will only boot with UEFI. Ubuntu can boot from GPT in both BIOS and UEFI. But to dual boot both OS must be either in BIOS or UEFI.

How do you want it? If you ask me, go with UEFI. We can also go BIOS way if you insist. You can read on www all about BIOS and UEFI and decide.

But First, Go into your UEFI/BIOS set up and DISABLE "Secure Boot". If you Don't want UEFI then disable that as well.

Creating New partition table:
1. Boot with Ubuntu CD/USB and "Try Ubuntu". After the desktop is ready, establish internet connectivity.
2. [Download and run FIXPARTS]("http://www.rodsbooks.com/fixparts/") to cleanup your Hard Disk of leftover GPT from Windows8 time. Running Fixparts is simple just read the link carefully.
3. Open GPARTED. From the right hand side choose the correct Drive. Select the partition, right click and Delete. Delete all the partitions. From the Menu Bar choose Device and then "Create new partition table". The default will be 'msdos', to choose GPT you have to Advanced. (Choose one wisely).
4. close Gparted and shutdown.

If you chose UEFI then to install Windows 7 follow this: [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

Some computers have a problem installing Windows7 from UEFI with DVD, in that case you have to install Windows7 from USB.

Once you have Winodows 7 installed as instructed get back here and we'll tell you how to go about Ubuntu_UEFI_GPT.

(If you choose BIOS then you don't need any special instructions. Go ahead and install both OS)


If you have anymore doubts then you are welcome to clear them.

Good Luck...

Hello Bro! thanks for ur efforst :)
i have converted my disk to GPT and installed Win7 in UEFI Mode :)
(U can notice that !!)

[ATTACH=CONFIG]242877[/ATTACH]

What is the next step ??

---

### Post by fantab on 2013-05-22
There is an 'unallocated space' of about 20GB and your 'F' partitions is about 80gb. Using Windows Disk Management 'shrink' the F partiton to have at least 34GB of 'unallocated space'.

Ubuntu main install needs about 25-30GB partition + you will need another 4GB for SWAP partition. Together it will be, say, 34GB. Partitioning is a very personal thing based on YOUR needs. I just gave  you a minimum idea. In fact, if I were you, I would delete the F  partition and merge the space with E just leaving aside 34GB as  unallocated)

Boot with Ubuntu Disc and "Try Ubuntu", open GPARTED, disk management. From the 'unallocated space' of 34 GB create two partitions:
30 GB Ext4
4 GB SWAP.

(Ubuntu can Read and Write to NTFS partiton, so we neither need a separate /home nor a separate Data partition for Ubuntu. You can use your E and F to store DATA from Ubuntu. However if you want a separate partition to Linux only then create another partiton in addition to the two already mentioned and format is as ext4). 

Close Gparted. From Desktop 'Install Ubuntu'.
At the dialog when the Installer asks your preference for 'Installaiton Type' select "SOMETHING ELSE". Another dialog will open, here select the 30GB partition and click 'Change' and select for 'Use As"= ext4, select 'format' and for Mountpoint= /. That is all continue with your install.

After rebooting, if you see any problems then, boot with Ubuntu Disc, "Try Ubuntu" and use [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") to fix any and all boot issues.

---

### Post by peshmerge on 2013-05-23
> **fantab said:**
> There is an 'unallocated space' of about 20GB and your 'F' partitions is about 80gb. Using Windows Disk Management 'shrink' the F partiton to have at least 34GB of 'unallocated space'.

Ubuntu main install needs about 25-30GB partition + you will need another 4GB for SWAP partition. Together it will be, say, 34GB. Partitioning is a very personal thing based on YOUR needs. I just gave  you a minimum idea. In fact, if I were you, I would delete the F  partition and merge the space with E just leaving aside 34GB as  unallocated)

Boot with Ubuntu Disc and "Try Ubuntu", open GPARTED, disk management. From the 'unallocated space' of 34 GB create two partitions:
30 GB Ext4
4 GB SWAP.

(Ubuntu can Read and Write to NTFS partiton, so we neither need a separate /home nor a separate Data partition for Ubuntu. You can use your E and F to store DATA from Ubuntu. However if you want a separate partition to Linux only then create another partiton in addition to the two already mentioned and format is as ext4). 

Close Gparted. From Desktop 'Install Ubuntu'.
At the dialog when the Installer asks your preference for 'Installaiton Type' select "SOMETHING ELSE". Another dialog will open, here select the 30GB partition and click 'Change' and select for 'Use As"= ext4, select 'format' and for Mountpoint= /. That is all continue with your install.

After rebooting, if you see any problems then, boot with Ubuntu Disc, "Try Ubuntu" and use [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") to fix any and all boot issues.

 
Hello Bro! Finally Linux is installed on my Laptop (Oh my God ), thanks a a lot a lot bro! i appreciate ur effort :)
But now i have a small problem that i can't choose between OS's when my laptop boots so i should enter the setup and choose " Windows boot " to be able to log on win7, and if i want to logon Ubuntu i should go back to Setup and choose " Ubuntu boot ".As u see in the foto below :
[ATTACH=CONFIG]242928[/ATTACH]

I must use Boot-Repair to fix this problem ???? i will do that and i will inform u :)

---

### Post by fantab on 2013-05-23
Yes, Boot-Repair can fix it for you. Just run the 'recommended repair'. 

Good Luck...

---

### Post by peshmerge on 2013-05-23
> **fantab said:**
> Yes, Boot-Repair can fix it for you. Just run the 'recommended repair'. 

Good Luck...
I have downloaded a copy of Boot-Repair iso x64, and it fix it.
When Boot-Repair finished the fix, it gave me this message :
[ATTACH=CONFIG]242934[/ATTACH]

so i entered the  Setup and created new boot option with this : sda2/EFI/ubuntu/grubx64.efi. And gave it name ***efi*** as shown below in the foto :
[ATTACH=CONFIG]242935[/ATTACH]
 
i made it th first boot chooes !

And now i get this screen always when i turn on my laptop :
[ATTACH=CONFIG]242936[/ATTACH]


Note: I posted this thread using ¨¨ Ubuntu 12.04 LTS ¨¨¨¨¨¨¨"
Thanks for every one replayed and tried to help me ! especailly thanks to _**[FONT=arial black][SIZE=5]fantab[/SIZE][/FONT]**_:razz:

---

