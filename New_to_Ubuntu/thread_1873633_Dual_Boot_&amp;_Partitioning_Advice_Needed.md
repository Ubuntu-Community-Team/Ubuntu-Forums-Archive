---
title: "Dual Boot &amp; Partitioning Advice Needed"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by djevans3 on 2011-11-01
I've installed 11.10 on another system using the entire HDD and love it, so I'm getting ready to try it as a dual boot on my family machine.  I have a 160GB internal drive running XP and it is partitioned to take up the entire drive.  I'm installing a 1TB unformatted drive on which I'd like to install 11.10 on a partition as well as create an NTFS partition to backup my music/pics/etc from the 160GB drive.  I do not hibernate my machine either.
 
So my question is, how many partitions do I need to create on the new drive and what format do they need to be in?  Lastly, since I'm dual booting from two different drives with each OS on its isolated drive, will I need Easy BCD to install or just used the advanced option from the LiveCD?
 
Thanks in advance!

---

### Post by djevans3 on 2011-11-02
Bueller?....Bueller?....Bueller?  :)

---

### Post by F.G. on 2011-11-02
so, it sounds like you should be able to install it, just using the manual partition option. also, btw, you can store you music and pics, from your ntfs drive on an ext partition, it doesn't have to be ntfs, so you'r probably better off making the whole terrabyte ext (although you may need to make special arrangements if you want to access it *from* Windows).

---

### Post by fantab on 2011-11-02
> **djevans3 said:**
> I've installed 11.10 on another system using the entire HDD and love it, so I'm getting ready to try it as a dual boot on my family machine.  I have a 160GB internal drive running XP and it is partitioned to take up the entire drive.  I'm installing a 1TB unformatted drive on which I'd like to install 11.10 on a partition as well as create an NTFS partition to backup my music/pics/etc from the 160GB drive.  I do not hibernate my machine either.
 
So my question is, how many partitions do I need to create on the new drive and what format do they need to be in?  Lastly, since I'm dual booting from two different drives with each OS on its isolated drive, will I need Easy BCD to install or just used the advanced option from the LiveCD?
 
Thanks in advance!

Partitioning HDD is a very personal thing, it totally depends on what your needs are. Here's what I did with my 1TB HDD
[COLOR=DarkGreen]/dev/sdb1 - 20 GB       - ext4 - Primary - ubuntu "/ and /Home"
/dev/sdb2 - 20 GB       - ext4 - Primary - 
/dev/sdb3 - 20 GB       - ext4 - Primary - 
/dev/sdb4 - 871.51 GB - Extended
/dev/sdb5 - 861.51 GB - ext4 - Logical  - Data
/dev/sdb6 - 4 GB         - swap - Logical[/COLOR]

You can create a NTFS partition for your required Size.

Use Gparted from LiveCD or create a **[Gparted Boot CD]("http://gparted.sourceforge.net/livecd.php")** (recommended) to partition your unformatted HDD, and use DOS Partition Table before you Partition and format.

Choose to Partition your HDD manually... 'something else' option (I think) when installing from LiveCD.

Remember to install **GRUB** on dev/sdb or your 1 TB HDD whatever /dev/sd? 

and **CHANGE HDD boot order in your BIOS** to boot from 1TB HDD where you will install your GRUB otherwise it will boot to first HDD only or to windows only. 

You can install Grub to your First HDD too (in this scenario you don't have to change your boot order) but then it will overwrite Windows MBR, its your choice.

---

### Post by chandanreddy on 2011-11-02
I have installed windows7 64bit on my lenovo B460 Laptop. After that i have installed ubuntu 11.04 

Can I remove windows7 without losing ubuntu.

Please help me . . . .

---

### Post by garyed on 2011-11-02
If you want to back up your Windows files while working in Windows to the other drive then I would recommend making a separate NTFS partition on your new drive for that purpose. If you just want to backup your Windows drive from Ubuntu then NTFS wouldn't be necessary on the new drive. With 1tb I would probably make the first partition a primary NTFS partition for Windows back ups & then make an extended partition for ext4 & swap partitions. This way you could even make a windows batch file to do quick incremental backups to the new drive. 
I like to use Gparted live to make my partitions before I install Ubuntu. It may be an extra step but I feel more comfortable mapping out things that way first.

---

### Post by garyed on 2011-11-02
> **chandanreddy said:**
> I have installed windows7 64bit on my lenovo B460 Laptop. After that i have installed ubuntu 11.04 

Can I remove windows7 without losing ubuntu.
Please help me . . . .

Yes you can BUT you will probably have to reinstall Grub because more than likely when you remove Windows you will also remove the MBR & you won't be able to boot from the HD any more. So be sure you have a way to boot Ubuntu from CD or usb before doing anything. I would do a little searching on reinstalling Grub2 first.

---

### Post by oldfred on 2011-11-02
@chandanreddy
Please do not highjack someone else thread. If you have additional questions start your own thread. But if you have installed with wubi, deleting Windows will also delete Ubuntu as it is inside the NTFS partition. Generally best not to delete it, just shrink it.

@djevans3
Good advice posted above. You do need to use manual install to make sure you can choose to install the grub2 boot loader to the new 1TB drive. I prefer to partition in advance, then use manual install.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

I have XP in a 160GB drive and then purchased a new 640GB drive. But I created a NTFS shared and put Firefox & Thunderbird profiles in the NTFS shared as my spouse wanted to see email & use Internet while I was trying to learn Ubuntu and had to keep rebooting into XP. 
I did not format entire drive initially. I did put all unallocated into the extended partition. I created a 100GB NTFS shared and another 100GB for ext3 formated partition /mnt/data. I only used a small part of those data partitions and had lots of space.  Now each new Ubuntu I install and use a new 25GB / (root) partition so I can copy settings from older install. But I now keep adding 25GB partitions as I have the space.

I have decided all new drives will use gpt not MBR(msdos). But if you ever want Windows do not use gpt. You do have to create one extra bios_grub partition. I have used gparted to create a 160GB drive with gpt and have my current Maverick install in it. I plan to convert my 640GB drive next to gpt.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by djevans3 on 2011-11-02
Thanks for all the great advice! I think I am going to put Grub on the 1TB drive for sure and change the boot order of the drive since my wife will still want to boot into Windows and I'd prefer to not mess with the MBR on that drive. I'll post back if I have any issues...now if the UPS man would just hurry up with my SATA cables!!!!
 
Last quick question...what is difference between ext3 and ext4?  This is my first venture into Linux so I'm learning.

---

### Post by houseworkshy on 2011-11-02
Just a small additional detail.  When you format the drives make sure that you make both bootable.  In gparted this is under "flags" just tick the box.  The easiest way with two drives ( which is how mine is set up ) is simple: just make sure that windows is on first ( sounds like yours already is ) then let the Ubuntu installer do it's automatic thing on the other drive.  It will set up the bootloader and the partitions for you.  What you format the new drive to is not so important as it would be over writen anyway if you choose automatic use of the entire disc.  All you are really after is the bootable flag in gparted.  Admitedly the lazy way.  There are some handy tricks like putting home in it's own partition but it's not crucial.
  
This free pdf is very handy when you get to the setting things up stage  [http://ubuntupocketguide.com/index_main.html](http://ubuntupocketguide.com/index_main.html)

The official documentation is also excellent, I'd recomend going to it as a first port of call.  It has a method of installing called apt:url, which I'm not sure of elsewhere but trust on the official site.  So one can read through and think "oh yes I'll want that in" and set up at the same time as you learn the basics.

Extra thought and as I'm still on the LTS I may be out of date ( sort of hope so really ) Ubuntu has a firewall installed in it's straight of the cd install but it is not turned on by default.  So before going online open a terminal and type "sudo ufw default deny" then after the password "sudo ufw enable".  Another tip which may or may not matter yet is after using the sudo comand ( eg as above after using apt:urls, other kinds of install or any admin rootlike activity ) enter "sudo -k in the terminal.  sudo gives tempory root privalages which are on a 15 minet timer and sudo -k ends those privalages early.  The danger which I haven't yet heard of happening is that one may use an apt:url for example then within 15 minets be tricked into using a dodgy hidden one while still in, effectively, root mode.  As the things one downloads must be in the repositories you have chosen anyway it's a small danger but as even repositores can be added with this method .... someday ......Might as well start with good habits.

Though you can do almost everything in the graphic user interphase there will be times when you use the terminal.  One of the most useful commands in the terminal is "man".  If it is typed in front of any command it brings up that commands manual page.  So I suggested above you used "ufw" in the terminal, you could enter "man ufw" in the terminal to double check my suggestion and for more details.  The man page is displayed in the terminal, to close it type "q".  The built in command help is really good.  "man man" for details "man apropos" is worth a look at too.  Guess that paragraph is a bit off topic but you have just started out and sooner or later you'll be seeing advice about entering things in the terminal.  I haven't seen vandalistic advice yet ( excellent forum this ) but there is a sticky about it from the moderators so might as well play safe, good way to learn anyway.

---

### Post by Mark Phelps on 2011-11-02
I too, have a multi-drive system with various versions of Windows and Ubuntu.  

My advice is the following:
1) Keep Windows on its own drive.  Don't install GRUB there. Don't mess with the MBR or partitioning. Don't have it connected to the PC when you install Ubuntu.
2) Install Ubuntu to the large drive. Install GRUB there, only.
3) Add a large NTFS partition to the large drive -- for sharing data.
4) Connect up both drives, boot using the Ubuntu drive.
5) Open a terminal and enter "sudo update-grub".

NOW, you will have a GRUB menu that allows you to select either OS, and each drive is bootable on its own.

---

### Post by djevans3 on 2011-11-04
I paritioned my 1TB drive and installed 11.10 with no issues tonight.  I did use GParted to do the partitioning because the LiveCD option doesn't allow for the creation of NTFS partitions.
 
My only issue is that my Dell A07 BIOS on Intel 945G chipset won't let me manually control which SATA drive boots first.  I can disable drives, which is how I got into Ubuntu, but not shift the boot order. I was able to update GRUB and it found windows XP, however, I have Ubuntu on the SATA2 slot so I may have to switch the cabling around so that it will boot to GRUB on SATA1 and provide the OS choice.
 
Thanks again for all the help!

---

### Post by oldfred on 2011-11-04
I thought all SATA based systems have to have a way to set drive to boot. SATA drives do not have the jumpers on the drive to set boot order like PATA systems.

Some systems hide the hard drive boot order separate from the device boot order, maybe on a different BIOS page, others make it part of hard drive selection in device boot order as a sub menu. If you use the one time boot key (f12 on my system) do you get a choice of hard drives to boot? My bootable flash drives also appears in the one time boot key menu as a hard drive.

Windows 7 may be ok with a drive order change, but XP has the drive number in boot.ini and may need boot.ini updated if you change which drive it is on.

---

