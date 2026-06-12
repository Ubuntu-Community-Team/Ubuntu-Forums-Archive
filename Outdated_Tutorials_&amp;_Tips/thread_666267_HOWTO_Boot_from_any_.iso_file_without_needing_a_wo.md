---
title: "HOWTO Boot from any .iso file without needing a working CD-ROM - REALLY USEFUL!"
date: 2008-01-13
forum: Outdated Tutorials &amp; Tips
---

### Post by john_spiral on 2008-01-13
**_BOOT ANY OS USING THE [[COLOR="Blue"]Gujin [/COLOR]]("http://gujin.sourceforge.net/")BOOTLOADER_ **

Below is a faster method for installing/running any OS / LIVE-CD directly from a separate hard disc partition. 

I was spurred into discovering the below method while trying to install various distros on an old Sony Vaio that didn't have a CD-ROM drive.

I currently use the below method to test various Distro's I find on [_DistroWatch.com_]("http://distrowatch.com/").

_**Advantages of the below method**_

[LIST]Runs quicker than booting from a physical CD[/LIST]
[LIST]Reduces the number of dead CD's thrown into our landfills.[/LIST]
[LIST]No need to find the correct vmlinuz & initrd.gz files to boot the .iso file.[/LIST]

_**Disadvantages**_

[LIST]You will need a floppy drive (get a USB drive on eBay) and a floppy disk (ask your gran ;-) [/LIST]

_**Method**_

[LIST]Download the operating system .iso file - check with md5sum if there is a signature available.[/LIST]
[LIST]Set aside a partition for the .iso file.[COLOR="DimGray"]*[/COLOR][/LIST]

[COLOR="DimGray"]* Before booting from the .iso file you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software e.g GPARTED, QTPARTED... 

There are some older partition floppies hidden on the net I would appreciate some recommendations that support most file systems.[/COLOR]

[LIST]Use the below commands to copy the OS/LIVECD .iso file to a spare partition:[/LIST][COLOR="Red"][B]

```
[COLOR="DimGray"]**sudo su**[/COLOR]
```
[SIZE="2"]_WARNING THE BELOW COMMAND WILL OVERWRITE THE SELECTED PARTITION, MAKE SURE IT'S CORRECT!_[/SIZE][/B][/COLOR]
```
[COLOR="DimGray"]**cat filename.iso > /dev/sda3**[/COLOR]
```
In the above example I'm copying the .iso file **filename.iso** 
to the partition called **sda3** (3rd partition on the first hard disk). 

Tip: use the command ```
[COLOR="DimGray"]**sudo fdisk -l**[/COLOR]
``` from a prompt to discover the partitions in your computer.[/COLOR]

[LIST]Next boot from either a [[COLOR="Blue"]Gujin[/COLOR]]("http://gujin.sourceforge.net/") * floppy bootloader or install Gujin to your hard disk.[/LIST]

[COLOR="Gray"]**_[SIZE="3"]Quick method to install Gujin to a floppy[/SIZE]_**

Download the install-x.x.tar.gz file from [[COLOR="Blue"]_sourceforge_[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=15465").

Extract the boot.144 file.

Copy the above file to a floppy disc via the below command:

```
[COLOR="DimGray"]**cat boot.144 > /dev/fd0**[/COLOR]
```

Floppy disks are one of the least reliable media around, so be prepared for multiple bad disks. It's a good idea to compare (with cmp) the written floppy disk with the image file. If cmp finds a difference, throw that floppy away and try another one.

```
[COLOR="DimGray"]**cmp boot.144 /dev/fd0**[/COLOR]
``` [/COLOR]

[LIST]At the Gujin prompt select the required OS / LIVECD.[/LIST]
[LIST]You should now be booting from the .iso file directly off your hard disk.[/LIST]

_**POST INSTALL (if you install ubuntu using this method)**_

Use the below commands to get Synaptic working (thanks to [mlind]("http://ubuntuforums.org/member.php?u=52272") for the workaround):

sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -m add

_**Links**_

Boot from a MacOSX .iso file:
 
[http://forum.insanelymac.com/index.php?act=Print&client=printer&f=136&t=103507](http://forum.insanelymac.com/index.php?act=Print&client=printer&f=136&t=103507)

I would appreciate your help in refining/correcting this HOWTO and answering questions.

Thanks John

---

### Post by Forrest Gumpp on 2008-02-14
john_spiral,

Thank you for this tip.  (It appears you posted it before the 'Thanks' button became a feature on the Forum, and as a consequence the button does not show up in this thread.)

I have not explored it beyond a quick look at the gujin site, but it is of interest to me for something I would like to do in the near future.  My second-hand Dell Optiplex G X 240 P4 1.7GHz 768MB RAM desktop only has bay space for one internal 3.5" HDD, but has two IDE channels on the mobo and accommodated in the BIOS.  I have already modified it so that two externally powered IDE HDDs mounted in caddies sitting on top of the case are connected by an 80 wire cable-select ribbon cable to the primary IDE channel.

I had intended placing a third HDD in the presently vacant single internal drive bay as soon as I can obtain a ribbon cable with sufficient separation between the drive connectors to permit the third HDD and the CD ROM drive to be connected to the secondary IDE channel.  Under this arrangement the HDD would have been pegged back to the 33 ATA rating of the optical drive, even though the mobo will handle 133 ATA, which all my HDDs are.

Your tip has shown me a way whereby I may be able to demount the optical drive and possibly install a 3.5" IDE HDD in its 5.25" bay space, yet still be able to download and install from an ISO when I need to.  That will give me four IDE HDDs running at 133 ATA rating, two of them powered from the internal PSU, and two from an old AT PSU mounted externally and manually switched on in advance when booting.  I understand there is also a performance boost in terms of access time for a CD that has been copied to a HDD as against one running in a lower ATA rated optical drive.

If I need to access bootable CDs I can simply transfer one of the HDDs in its caddy to my son's desktop computer (which has CD R/W and DVD R/W drives and is also set up for HDD caddies) and copy the CD or DVD to that HDD.  If I nevertheless find I still require the convenience of a CD ROM drive on my own computer for simply viewing content or running/installing applications, I can always plug in an external USB CD drive.

Overall your tip promises me increased flexibility in the use of my older hardware, especially so far as backups and partition images on separate HDDs is concerned, as well as simply extra storage capacity.

You ask about older partitioning floppies.  I have used the DOS version of Paragon Partition Manager 2002 to view, clone, move, re-size, and create partitions for both Windows and Linux.  I obtained it from a computer magazine CD as a 'freebie' and created the floppy from that.  It seems to work OK, but I do not know whether it is looked upon with favour by Linux gurus.  I also do not know if it is downloadable from the internet.

Edit.  I now see a 'thanks' button I swear was not there before.  Perhaps it only appears if one is logged in.  I press the button.

---

### Post by john_spiral on 2008-02-17
Hi Forest,

Good to hear you are investigating the above method, hopefully you will like me find it extremely useful for both installing Ubuntu and testing various Live CD's. 

I've been using it for a while now and find it extremely useful for testing any new Linux Distro directly from my hd without the speed 
limitations of my CD-ROM.   

**The only major drawback is the dreaded [B]cat** command which has the potential to nuke your system. [/B]

Thanks for the tip on Paragon Partition Manager 2002, does it support Linux type partitions?

John

---

### Post by john_spiral on 2008-02-23
Just a bump to say I've made some updates to the HOWTO.

all those users looking to test the new Ubuntu 8.04 Alpha 5 might find this HOWTO useful.

John

---

### Post by Forrest Gumpp on 2008-02-24
Yes, Paragon Partition Manager 2002 does support Linux file systems.  I have used it to view, alter, create, and format Linux partitions before attempting to use install CDs for the first time.  I have also cloned both whole HDDs and individual partitions with it.

I first installed it under Windows, from a 'freebie' magazine CD, and then created the DOS version floppy which is now all that I use.

I have seen somewhere a reference to a list of partitioning tools that are not favoured by Linux gurus, but have not been able to find it again.  I do not know how Paragon Partition Manager is viewed within the Linux community, so be cautious.

I have not experienced any problem with it, but then again, how would I really know?  I'm not highly experienced with computers in general and Linux in particular.

It seems your topic has attracted a lot of views.  Thanks for the update info.

---

### Post by john_spiral on 2008-02-24
> **Forrest Gumpp said:**
> Yes, Paragon Partition Manager 2002 does support Linux file systems......

Thanks for that good info Forrest!

---

### Post by frankos44 on 2008-02-24
Another method would be to create a bootable Ubuntu pendrive from an installation iso.  Each time a new version of Ubuntu comes out or you wish to install a different variant of Ubuntu you could simply overwrite the pen from a previously downloaded iso image.

That would save 4 CD's every six months for starters. Desktop i383, Server i386, Desktop 64bit and Server 64 bit.

Another advantage is you could also store the cached files on there thus saving you the  bother of downloading what is currently 184 updates after the installation has completed on the target computer.

I assume you would need a FAT32 partition for booting and perhaps another for storing the files but im not sure how to make it bootable.

---

### Post by say2sky on 2008-03-05
> **john_spiral said:**
> **_BOOT ANY OS USING THE [[COLOR="Blue"]Gujin [/COLOR]]("http://gujin.sourceforge.net/")BOOTLOADER_ **
install Gujin to your hard disk


This is an interesting and simple way to test and try different linux distro and I will try this on my laptop.

But one thing is my laptop don't have floppy drive and I hope to not mess up my current used HDD by install new bootloader for try new system. So I think install Gujin bootloader onto USB flash jump drive is a good choice, I hope to know if it is possible to have Gujin and linux iso file both on USB drive or just Gujin bootloader on USB drive and linux iso file on internal HDD to achieve same boot.

thanx in advance!

---

### Post by frankos44 on 2008-03-06
This might be of interest

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by zvacet on 2008-03-11
@ **john_spiral**

Does this mean I can with this method use other distros not just for tryin.What I realy want to ask is:Using this method can I use other distros like I install them with CD(updates,upgrades.installing packages)?Thanks and sorry for my ignorance.

---

### Post by glenboarder99 on 2008-03-11
This Is really useful:):KS

---

### Post by john_spiral on 2008-03-16
> **say2sky said:**
> This is an interesting and simple way to test and try different linux distro and I will try this on my laptop.

But one thing is my laptop don't have floppy drive and I hope to not mess up my current used HDD by install new bootloader for try new system. So I think install Gujin bootloader onto USB flash jump drive is a good choice, I hope to know if it is possible to have Gujin and linux iso file both on USB drive or just Gujin bootloader on USB drive and linux iso file on internal HDD to achieve same boot.

thanx in advance!

did you get this to work?

---

### Post by john_spiral on 2008-03-16
> **zvacet said:**
> @ **john_spiral**

Does this mean I can with this method use other distros not just for tryin.What I realy want to ask is:Using this method can I use other distros like I install them with CD(updates,upgrades.installing packages)?Thanks and sorry for my ignorance.

I'm currently running off a Kubuntu 7.1 system I installed using this method.

I'm sure it's a good way to test 8.04 / 8.10 or any other LiveCD.

admittedly I can't seem to get the latest eLive CD working with this method.

---

### Post by Yes on 2008-03-20
I keep getting a "checksum error" when I boot from it.  I've tried two different floppies at least two times each.  Any idea why?

---

### Post by john_spiral on 2008-03-21
> **Yes said:**
> I keep getting a "checksum error" when I boot from it.  I've tried two different floppies at least two times each.  Any idea why?

Hi Yes,

what .iso are you trying to boot from?

did you check the floppy?

**cmp boot.144 /dev/fd0**

come back to us.

thanks John

---

### Post by john_spiral on 2008-03-21
> **Yes said:**
> I keep getting a "checksum error" when I boot from it.  I've tried two different floppies at least two times each.  Any idea why?

to test ubuntu-8.04-beta-desktop-i386.iso choose the 

**IDE/lba master@..... El Torito.... **

option, it worked a treat!

---

### Post by Yes on 2008-03-21
Well, I haven't actually gotten to the point where I boot from an iso.  I put the floppy in and turn the laptop on and it gives me the chesum error.

I totally forgot to check the floppy, and lo and behold it was different.  Unfortunately, it writes differently to all the floppies I've tried, all at the same line and same character.  Does this mean the boot.144 file is somehow corrupted?

---

### Post by Yes on 2008-03-21
Oops.. didn't mean to post that >.<

---

### Post by john_spiral on 2008-03-21
> **Yes said:**
> ...Does this mean the boot.144 file is somehow corrupted?

sounds like you need to download it again.

---

### Post by Yes on 2008-03-21
It keeps "differing" on different characters but always on the same line.  Three different floppies, and I've downloaded the file twice.

Any ideas?

---

### Post by john_spiral on 2008-03-22
> **Yes said:**
> It keeps "differing" on different characters but always on the same line.  Three different floppies, and I've downloaded the file twice.

Any ideas?

From a terminal cd (change directory) into the directory where the **boot.144** file is located (extracted from install-2.4.tar.gz). 

Then run the below command:

**md5sum boot.144**

it should give us:

d56a12e4bdcec03b4c59fc15f3eb7c3d

*the above line is the unique md5 signature for the file

If the boot.144 file gives the same md5sum then it's your floppy drive that's the problem. Clean the drive or try another drive or even an external usb floppy drive.

---

### Post by franestepona on 2008-03-22
Hi!

I have installed Gujin in myu hard drive. I downloaded the latest Hardy cd and mounted it, then I copied everything inside it to another partition. When i boot from Gujin it doesnt recognise the Hardy cd. Do I really need to overwrite the whole partition with cat? Is there any method that doesnt overwrite the partition?

---

### Post by john_spiral on 2008-03-22
> **franestepona said:**
> ... I downloaded the latest Hardy cd and mounted it, then I copied everything inside it to another partition. ...

No need to mount the CD image, 

Just use the cat command to copy the .iso file directly to the partition, 

Gujin should be able to boot from the partition now.

Unfortunately will will need to set aside a partition for the .iso file.

---

### Post by Yes on 2008-03-22
I finally got the file downloaded ok, and put boot.144 on it with dd (when I used cat cmp came up with an error).

I can't figure out what to do when I boot, though.  I have an iso on /dev/hda2.  How do I boot from it?

---

### Post by john_spiral on 2008-03-22
> **Yes said:**
> I finally got the file downloaded ok, and put boot.144 on it with dd (when I used cat cmp came up with an error).

I can't figure out what to do when I boot, though.  I have an iso on /dev/hda2.  How do I boot from it?

Hi Yes,

does your Gujin floppy boot?

If not use the below command to copy the .bin file to the floppy.

cat boot.144 > /dev/fd0

If your Gujin floppy is booting then you should see an option for the .iso file on "/dev/hda2".

If you are still struggling then re-read the howto and make sure you follow all steps in sequence.

come back to us.

John

---

### Post by Yes on 2008-03-22
Ok, I got it now.

FYI, cat boot.144 > /dev/fd0 didn't work.  I had to put it on with dd if=boot.144 of=/dev/fd0

---

### Post by franestepona on 2008-03-22
Seems that I cant get the cat to work.

```
[03:39:02]Fran@FransMachine: sudo fdisk -l
[sudo] password for fran:

Disk /dev/sda: 80.0 GB, 80023752704 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf30cf30c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1415    11365956    5  Extended
/dev/sda2            1416        8685    58396275   83  Linux
/dev/sda3            8686        9729     8385930   83  Linux
/dev/sda5            1306        1415      883543+  82  Linux swap / Solaris
/dev/sda6               1        1305    10482318   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS
[03:39:23]Fran@FransMachine: sudo cat /home/fran/Desktop/ubuntu-8.04-beta-desktop-i386.iso  > /dev/sda3
bash: /dev/sda3: Permission denied

```

I tried with the partition mounted, umounted, reformatted, etc... none worked. What am I doing wrong?

---

### Post by john_spiral on 2008-03-23
> **franestepona said:**
> 
[03:39:23]```
Fran@FransMachine: sudo cat /home/fran/Desktop/ubuntu-8.04-beta-desktop-i386.iso  > /dev/sda3
bash: /dev/sda3: Permission denied

```
Hi Fran,

It looks like fran is not in the sudoers list. i.e doesn't have permission to use the sudo command?

Can you use the **sudo su** command to become root?

---

### Post by john_spiral on 2008-03-23
> **Yes said:**
> Ok, I got it now.

FYI, cat boot.144 > /dev/fd0 didn't work.  I had to put it on with dd if=boot.144 of=/dev/fd0

I'm gald you got it working ;-)

strange how the cat boot.144 > /dev/fd0 didn't work on your machine (it's a command from the Gujin install.txt).

what size is your floppy, 1.44 megs?

---

### Post by franestepona on 2008-03-23
Hi again! :)
After rebooting I could copy the iso image with the cat command, booted from the iso and everything went good. I encountered a problem though, when I try to install the system it complains about a cd or hardisk failure at 78% of the process. I'm currently downloading the cd iso file again to redo the process, could it be the checksum of the file?

Thanks!

EDIT: I downloaded the cd again and redo the cat, now it's working! :)

---

### Post by Giving it a Try on 2008-04-06
I have my iso file on /dev/hda3 which a Linux bootable partition.

I have working copy of Gujin on a floppy and can boot to it.

the problem is that the analysis says not bootable disk of partition found. 

What gives?

---

### Post by john_spiral on 2008-04-06
> **Giving it a Try said:**
> I have my iso file on /dev/hda3 which a Linux bootable partition.

I have working copy of Gujin on a floppy and can boot to it.

the problem is that the analysis says not bootable disk of partition found. 

What gives?
Hi,

Did you follow the HOWTO or are you looking to boot from an existing partition?

John

---

### Post by Giving it a Try on 2008-04-06
Gujin is not booting partition. It doesn't recognize any bootable partition.

I have copied the Ubuntu install files directly to /dev/hda3. this partition is set to bootable. Should Gujin recognize this and boot on load?

---

### Post by john_spiral on 2008-04-07
> **Giving it a Try said:**
> Gujin is not booting partition. It doesn't recognize any bootable partition.

I have copied the Ubuntu install files directly to /dev/hda3. this partition is set to bootable. Should Gujin recognize this and boot on load?

did you copy the .iso file to the partition using the the **cat** command?


**cat xyz.iso > /dev/hda3**

xyz.iso being the name of the iso file.

---

### Post by Giving it a Try on 2008-04-07
> **john_spiral said:**
> did you copy the .iso file to the partition using the the **cat** command?


**cat xyz.iso > /dev/hda3**

xyz.iso being the name of the iso file.
No, I copied the files from the CD on a Windows machine to /dev/hda3.

I have no CD on the other machine (laptop) and I have no other Ubuntu machine.

What should I do?

---

### Post by john_spiral on 2008-04-08
> **Giving it a Try said:**
> No, I copied the files from the CD on a Windows machine to /dev/hda3.

I have no CD on the other machine (laptop) and I have no other Ubuntu machine.

What should I do?

Hi,

In essence you need to copy the .iso file directly to the /dev/hda3 partition using the below command

**cat xyz.iso > /dev/hda3**

Give us more information:

Is the Windows machine a different machine to the Linux one?

Does it have a CD-ROM, can you boot from it?

Can you move the hard disk between the Windows machine and the one you intend installing Linux on?

please come back to us with more info.

thanks John

---

### Post by ryan00davis on 2008-04-09
Im having the same problem as giving it a try.   im installing on my lenovo x61t (no cd drive) and only have windows installed currently.  i've created an ext3 file system that is about 5gb and have copied an iso over using FS driver (from fs-driver.org).

being that i dont have linux installed, i dont have access to the cat command to copy it to the new partition.

---

### Post by Giving it a Try on 2008-04-09
> **john_spiral said:**
> Hi,

In essence you need to copy the .iso file directly to the /dev/hda3 partition using the below command

**cat xyz.iso > /dev/hda3**

Give us more information:

Is the Windows machine a different machine to the Linux one?

Does it have a CD-ROM, can you boot from it?

Can you move the hard disk between the Windows machine and the one you intend installing Linux on?

please come back to us with more info.

thanks John

The windows machine is a deferent computer.

I can move the hard disk between the two computers.

I have tried copying the Ubuntu CD to /dev/hda3 (using the Windows computer), but I can't get that do boot.

---

### Post by john_spiral on 2008-04-09
> **Giving it a Try said:**
> The windows machine is a deferent computer.

I can move the hard disk between the two computers.

I have tried copying the Ubuntu CD to /dev/hda3 (using the Windows computer), but I can't get that do boot.

Connect the Linux hard disk to the Windows machine, hopefully you can boot off a Ubuntu CD on this computer.

This will give you access to a terminal where you can run the **cat** command.

Make sure you have two partitions on the Linux hard disk - one for the .iso and the rest of the disk for the installation of Linux. 

> **Giving it a Try said:**
> 
I have tried copying the Ubuntu CD to /dev/hda3 (using the Windows computer), but I can't get that do boot.

The above won't work as you need to copy the .iso file directly to the designated partition directly using the cat command.

see the HOWTO on the first page.

come back to us.

---

### Post by john_spiral on 2008-04-09
> **ryan00davis said:**
> Im having the same problem as giving it a try.   im installing on my lenovo x61t (no cd drive) and only have windows installed currently.  i've created an ext3 file system that is about 5gb and have copied an iso over using FS driver (from fs-driver.org).

being that i dont have linux installed, i dont have access to the cat command to copy it to the new partition.

how did create the ext3 file system?

can you boot off a linux floppy or USB stick?

---

### Post by ryan00davis on 2008-04-09
i used paragon partition manager to get the ext3 partition.

i can boot from a usb drive and use ultimate boot disk on the flash drive to get to gujin.

i know the easy solution would be to buy an usb cd drive, but if possible i would rather not spend the money as i really would rarely use it.

im sure i could download a live cd that would be bootable from my usb drive (512MB) but if anyone knows of a way to do it from windows that would save me some time.

if not, any suggestions on a small live cd, preferably with ntfs support already loaded in (but not manditory)?

thanks,
Ryan Davis

---

### Post by ryan00davis on 2008-04-10
ok, i finally got it working.  for whatever reason damn small linux didnt want to work, so i barrowed my roommates bigger usb drive and used knoppix.

thanks for the howto.
Ryan

---

### Post by munkyeetr on 2008-04-11
Very cool john_spiral :guitar:

The only issue I have come across is that for some reason using:

```

sudo cat foo.iso > /dev/bar

```
gives me a permission denied error, even though I am using sudo and I have sudo rights.

If I **su root** and then run:
```

cat foo.iso > /dev/bar

```
I have no problems. Very weird.

Anyway, kudos for the tip!

---

### Post by Trzone on 2008-04-11
Is there a cd image (.iso) for the gujin bootloader? Could anyone point me in the direction to said disk image?  thanks!

---

### Post by john_spiral on 2008-04-11
try the [_[COLOR="Blue"]**install-2.4.tar.gz**[/COLOR]_]("http://downloads.sourceforge.net/gujin/install-2.4.tar.gz?modtime=1202246533&big_mirror=0") file from SourceForge.

try the install.txt, I know it's a long read but hopefully you can shed some light on it for the rest of us.

---

### Post by Trzone on 2008-04-11
See below post.

---

### Post by john_spiral on 2008-04-11
> **Trzone said:**
> I continue to read through the install text, but it seems quite confusing.  Which one is the disk image? sorry.
It seems to me that one has to compile a disk image from the floppy images.
I know the point of this thread is to not use cds, but i do have some CD-rws around.

you got a working floppy?

Not sure about the CD bit though, anyone?

---

### Post by Trzone on 2008-04-11
This disk image runs the Gujin bootloader.  I created it using  mkisofs -o bootcd.iso -b boot.144 boot144

---

### Post by Giving it a Try on 2008-04-13
> **munkyeetr said:**
> Very cool john_spiral :guitar:

The only issue I have come across is that for some reason using:

```

sudo cat foo.iso > /dev/bar

```
gives me a permission denied error, even though I am using sudo and I have sudo rights.

If I **su root** and then run:
```

cat foo.iso > /dev/bar

```


I'm having the same issue.



I boot the Ubuntu CD so that I can run the terminal window and copy the iso to the extra partition.

Ok, I gotten as far as copying the iso to the extra partision

```
sudo cat ubuntu.iso > /dev/hda3
```
and
```
sudo cat ubuntu.iso > /media/disk
```

but i get a Permission denied message

what is the root password by default?

---

### Post by munkyeetr on 2008-04-13
"Give it a try"

I am a little confused, you're booting into the Ubuntu LiveCD and copying the .iso image to a partition? Correct me if I am wrong.

Do you get Permission denied errors on both commands you listed above, or just the last one? Because you don't need to do the last one as far as I know, that's basically copying it to a mount point, which we don't need. You just need to *cat* it onto the partition which you do with **cat ubuntu.iso > /dev/hda3**

As far as changing the password of the root account on the LiveCD (or a proper installation):
1) **System** -> **Administration** ->** Users and Groups**
2) Select the *root* account, and choose **Properties**
3) Under password, change and confirm the User Password
4) **OK** -> **Close**

---

### Post by Giving it a Try on 2008-04-13
Thanks munkyeetr



I figured out from GParted that the partition was /dev/sda3 

that helps.

it's copying now...

I should be able to pop the HDD back in the old laptop and boot???

---

### Post by munkyeetr on 2008-04-13
**EDIT: Just noticed that you figured that out while I was typing!**

**yes, it matters**...you don't want to overwrite your Windows partition or Windows will be gone (or maybe you do :lolflag:)

So, when you're in the LiveCD do the following (** I am assuming you have already created a partition on which to put the .iso files **):

1) **System** -> **Administration** ->** Partition Editor**
2) Find the partition you created for this and note it's /devnode (hda#, sda#), which you will then use with the **cat** command. Be very sure you have the right one.

---

### Post by Giving it a Try on 2008-04-13
Thanks for the warning munkyeetr. That was close!

Ok, I've found that if was /dev/sdc3

so it's copied. 

Now, I'm trying to boot with my Gujin floppy and all i get is a blank screen. The floppy worked before.

---

### Post by Giving it a Try on 2008-04-13
Never mind my last post. This is an old machin with many problems. One of them being a bad screen.

---

### Post by Giving it a Try on 2008-04-13
Ok, I booted Gujin and selected the partition to boot. Ubuntu booted displayed a menu. I chose the first option to start/install.

the computer launched the linux kernel and display the graphic install screen...
Then it just displays a blank screen with a cursor blinking.The HDD light flashes and blinks periodically.

What gives?

---

### Post by munkyeetr on 2008-04-13
Try starting in Safe Graphics Mode.

---

### Post by Giving it a Try on 2008-04-13
I tried that, but I got the same thing.

Hmmm....

---

### Post by munkyeetr on 2008-04-13
Hmmm. I don't know.

Which Ubuntu are you trying? 7.10? 8.04? I have had some distros not work for whatever reason like Fedora 7 and 8.

Not sure offhand. Maybe someone else will have some advice.

---

### Post by john_spiral on 2008-04-13
> **munkyeetr said:**
> Very cool john_spiral :guitar:

The only issue I have come across is that for some reason using:

```

sudo cat foo.iso > /dev/bar

```
gives me a permission denied error, even though I am using sudo and I have sudo rights.

If I **su root** and then run:
```

cat foo.iso > /dev/bar

```
I have no problems. Very weird.

Anyway, kudos for the tip!

thanks for pointing this out, I've changed the HOWTO.

---

### Post by john_spiral on 2008-04-13
> **Giving it a Try said:**
> I tried that, but I got the same thing.

Hmmm....

did you check the md5sum of the .iso?

---

### Post by Giving it a Try on 2008-04-13
> **john_spiral said:**
> did you check the md5sum of the .iso?

How do I check this?

---

### Post by munkyeetr on 2008-04-14
From a Terminal window type the following commands (press enter after each command):
NOTE: Obviously */path/to/isofile* is the full path to where the .iso file is stored and *foo.iso* is the real name of the iso file.
```

cd /path/to/isofile
md5sum foo.iso

```
This will output the md5sum of the iso. If you go to the download site where you got the .iso file you should also find a text file that contains the md5sum of the downloadable files. Check your output against this text file. If they are the same, you have an exact copy of the .iso file, if they are different, download the .iso again, and try again.

Hopefully this explanation is clear, and not too confusing.

---

### Post by soxs on 2008-04-14
Is it possible to create a second partition with about 100MB and install grub there and boot with your *original* grub via chainloader +1 into the second one, which will run the iso-live-cd?

---

### Post by john_spiral on 2008-04-15
**_EDIT: THANKS TO munkyeetr FOR ANSWERING Giving it a Try'S QUESTION!_**

> **Giving it a Try said:**
> How do I check this?

What .iso file are you trying to boot from? 

Nearly all Linux/BSD/.... distro's publish md5sums of their .iso files.

for example from a terminal type:

**md5sum ubuntu-8.04-beta-desktop-i386.iso**

it will spit out a long string of characters like 

523db182ecea4c929e4ab26ddaadfb40

Make sure the above string of random rubbish matches the Distro's md5sum. On a download page you should find a file called MD5SUMS detailing the above signature.

come back to us with the results.

---

### Post by john_spiral on 2008-04-15
> **soxs said:**
> Is it possible to create a second partition with about 100MB and install grub there and boot with your *original* grub via chainloader +1 into the second one, which will run the iso-live-cd?

Hi soxs can you give us more info on your partitions, do you have a floppy and ultimately what Distro/s you are trying to install?

thanks

John

---

### Post by soxs on 2008-04-15
That's the point,.. i don not have floppy nor an usb-stick (except for an iPod). What diestros I am going to try are, ubuntu and fedora aswell as suse.
I've got 32gb left ot do whatever I want with.. so I can play/test a lil..

---

### Post by hums07 on 2008-04-15
> **soxs said:**
> That's the point,.. i don not have floppy nor an usb-stick (except for an iPod). What diestros I am going to try are, ubuntu and fedora aswell as suse.
I've got 32gb left ot do whatever I want with.. so I can play/test a lil..

If you dont have floppy or USB, but you already have linux, you can try this:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
If you have Windows, you can try this, just installation:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by soxs on 2008-04-15
Well, I I prefer linux anyways :-P
thx, should, work pretty well as far as I've read

---

### Post by Raccoon1400 on 2008-05-19
This sometimes causes problems installing because the distro can't find the install media. Is there a way around this?

---

### Post by john_spiral on 2008-05-20
> **Raccoon1400 said:**
> This sometimes causes problems installing because the distro can't find the install media. Is there a way around this?

what are you trying to install Raccoon?

---

### Post by zvacet on 2008-05-31
I´m able to transfer iso to the partition and then boot with floppy.That way I can run Live CD,but I want to inastall it.It is like Catch-22.If I want to install I have to format to ext3,and that way Os remove itself.If I don´t format I can not install (obviously).I can feel that I missing something very simple but I don´t know what is it.

---

### Post by john_spiral on 2008-05-31
> **zvacet said:**
> I´m able to transfer iso to the partition and then boot with floppy.That way I can run Live CD,but I want to inastall it.It is like Catch-22.If I want to install I have to format to ext3,and that way Os remove itself.If I don´t format I can not install (obviously).I can feel that I missing something very simple but I don´t know what is it.

hi zvacet,

quote from another of my howto's

"(2) Before installing Ubuntu you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software. Create one new partition for the Ubuntu installation, one to hold the .iso file & additional boot files (say 700megs). You might need to resize your existing OS to make space for the above 2 partitions."

hope this helps.

come back to us.

---

### Post by zvacet on 2008-05-31
> You might need to resize your existing OS to make space for the above 2 partitions."

From **howto** it look like I need just one partition which I have.And like you may see from my post I have floppy and I can boot from it.But now in your response you are talking about 2 partitions and I´m confused,because I followed **howto **,and there I can find that I need one partition.Maybe I´m just little bit slow,so will you tell me exactly what I have to do.Tnx

---

### Post by soxs on 2008-05-31
I guess he wants to say, if you're going to install the OS from the life cd (which runs from your hd) to your hd you will need a second partition where you can place the os from the live cd.

---

### Post by john_spiral on 2008-06-03
> **soxs said:**
> I guess he wants to say, if you're going to install the OS from the life cd (which runs from your hd) to your hd you will need a second partition where you can place the os from the live cd.

Thanks for answering the question soxs.

---

### Post by kraymore on 2008-06-23
can you install gujin to the hard drive then add an entry to menu.lst for grub, update grub, then have a new boot from iso entry on boot?  i'm looking for something along those lines.

---

### Post by john_spiral on 2008-06-29
> **kraymore said:**
> can you install gujin to the hard drive then add an entry to menu.lst for grub, update grub, then have a new boot from iso entry on boot?  i'm looking for something along those lines.

Hi kraymore,

sorry for the long dely in my reply.

Can you explain what you trying to achieve or I suppose at this stage already achieved?

---

### Post by kraymore on 2008-06-29
yes sir.  i'd like to boot a ubuntu iso from a grub entry.  would sure be nice if grub allowed auto mounting of iso files, along with kernel images.

---

### Post by john_spiral on 2008-06-30
> **kraymore said:**
> yes sir.  i'd like to boot a ubuntu iso from a grub entry.  would sure be nice if grub allowed auto mounting of iso files, along with kernel images.

Hi kraymore,

Unfortunately the only method I've found to boot an .iso file is through the Gujin BOOTLOADER.

You could try making an entry in Grub to boot the Gujin BOOTLOADER off a floppy or another hard disk then set the .iso file as the default within Gujin.

Is there any particular reason why you are looking to boot the .iso within Grub?

thanks

John

---

### Post by kraymore on 2008-06-30
the times i've used floppies, my experience is they go bad easily :)

---

### Post by john_spiral on 2008-07-01
> **kraymore said:**
> the times i've used floppies, my experience is they go bad easily :)

install Gujin to a secondary hard disc in the machine, then get GRUB to boot this secondary disc.

---

### Post by daris on 2008-07-01
I followed instructions from this tutorial and now i can't run my debian. After sending iso data to the partition, I added it to /etc/fstab as ext3 and that was my mistake. Now while loading debian it tries to mount that partition but it can't and shows error.

I thought that formatting partition helps, so i formatted it to ntfs (using partition magic on windows) and it still can't mount that partition.

Now i can login as root and use basic linux command. I can't run nano.

I tried also run debian installer from cd but after booting it shows only one line of text and restarts my computer.

I need your help! I'm using XP right now but i don't want to using it ;]


Ealier i booted my pc from floopy disc and tried to boot partition with iso image, but it reads floopy all the time and monitor turns on and turns down (i'm not good at english but i think you'll understand ;] )


Sorry for my english, it isn't good ;]

**edit: **
I'm stupid ;] Why didn't I thought about formatting that partition to ext3 ealier? Problem solved

But i want to know how fix:
> **daris]i booted my pc from floopy disc and tried to boot partition with iso image, but it reads floopy all the time and monitor turns on and turns down (i'm not good at english but i think you'll understand  said:**
>  )

---

### Post by john_spiral on 2008-07-01
> **daris said:**
> Ealier i booted my pc from floopy disc and tried to boot partition with iso image, but it reads floopy all the time and monitor turns on and turns down (i'm not good at english but i think you'll understand ;] )


Hi Daris,

your best option is to post your question on the Gujin sourceforge forum:

[http://sourceforge.net/forum/forum.php?forum_id=49128](http://sourceforge.net/forum/forum.php?forum_id=49128)

thanks

John

---

### Post by Jose Catre-Vandis on 2008-08-12
Woah - what "fun" have I had with this! Ultimately it does work, but I should have applied the old adage of let sleeping dogs lie! 

I have had a server running 6.06 LTS for the last two years, just sat there chugging away. mostly for an internal LAN. Thought it was about time to upgrade, but it has four hard drives in it and no CDRom connected up.

Created a small logical partition in an extended partition
Copied the iso as per the howto
Made the Gujin boot floppy

Would the floppy drive work - no. Checked bios settings, swapped drive and cables and eventually it sprang into life. However, no sign of a bootable partition. Seems Gujin could not find it buried in an extended partition, so this might be something to check and perhaps add into to the HOWTO - [COLOR="Red"]**"Create a spare _primary_ partition?"**[/COLOR]

So created a spare primary partition and copying iso again. This time success, a bootable partition found, my 8.04.01 Desktop iso was found (yes, look for the "El Torito") Install got about 64% of the way then borked. Ran a md5sum on the ISO, it didn't match. Darn. Got a fresh copy of the iso, triple checked the ISO and away we went again. This time complete success. At last. Now for updates and configuration.

Thanks John for the howto, works well when everything works :)

---

### Post by munkyeetr on 2008-08-12
> **Jose Catre-Vandis said:**
> Seems Gujin could not find it buried in an extended partition, so this might be something to check and perhaps add into to the HOWTO - [COLOR="Red"]**"Create a spare _primary_ partition?"**[/COLOR]

This isn't a hard/fast rule, but possibly environmental. The partition I use regularily for this procedure is an extended/logical partition. I have had no issues with Gujin finding it, though, I have had some issues with some OS's not booting properly from that partition (eg: Fedora)

One thing to look for is when you create the logical partition, do not format it with any filesystem. (Not sure if you did or not, just saying)

---

### Post by Jose Catre-Vandis on 2008-08-12
> **munkyeetr said:**
> One thing to look for is when you create the logical partition, do not format it with any filesystem. (Not sure if you did or not, just saying)

Didn't format, but good to know it _can_ work from an extended/logical partition. Do you blank it everytime you "load" a new distro or just let the cat command do it's stuff?

---

### Post by munkyeetr on 2008-08-12
> **Jose Catre-Vandis said:**
> Didn't format, but good to know it _can_ work from an extended/logical partition. Do you blank it everytime you "load" a new distro or just let the cat command do it's stuff?

I just use the cat command each time.

---

### Post by say2sky on 2008-09-07
My laptop no floppy drive is available, I install gujin to HD's MBR

```

sudo ./instboot  boot.bin /boot/gujin.ebios
cat cd.iso > /dev/sda3

```

I have tested ubuntu and kubuntu 8.04.1 version. it works very well. Thanks for this good howto!

I also met two issue:
when testing pclinuxos-2007.iso, only simple shell are showed. cannot boot to normal system. 
when I install gujin and linux.iso both into USB jump drive, it cannot be boot. I think perhaps the ubuntu livecd image donot support USB boot. But I am not sure. 
 

Now after I test, original grub bootloader need to be recovered to HD, I hope in future grub bootloader will be able to directly boot ISO filesystem just like this gujin.

---

### Post by kraymore on 2008-09-08
i could have sworn that i had read something at some point in time referencing the ability to boot an iso from a grub entry, or something similar along those lines, if i'm not mistaken, in a manner without having to use gujin.  i could be wrong, but i thought i'd take another stab. when i had originally read it, it was a write up of another distribution's and how to install it through a iso and grub, and had some mention of doing it.  there are times i think that perhaps memories were somehow tainted, but my hunch says this is not one of them.

---

### Post by john_spiral on 2008-09-08
> **kraymore said:**
> i could have sworn that i had read something at some point in time referencing the ability to boot an iso from a grub entry....

It would be great to hear more info on this method.

---

### Post by say2sky on 2008-09-08
I think now grub cannot completely replace gujin as bootloader to boot iso filesystem copy out from livecd. gujin can search and find then use initrd.img and vmlinuz in filesystem as from livecd. I have checked  position of initrd.img and vmlinuz in filesystem, it is different from one livecd to other. 

I have tested three more distros:
dsl-4.4.5.iso  and puppy-4.00-k2.6.21.7-seamonkey.iso are successful to boot.
FreeNAS-i386-LiveCD-0.69b2.3631.iso cannot be booted by gujin.

---

### Post by RavUn on 2008-10-13
I checked out the link for booting from mac iso but it doesn't have much useful information.  It just has a link back to here.  Any news about this?

---

### Post by john_spiral on 2008-10-14
> **RavUn said:**
> I checked out the link for booting from mac iso but it doesn't have much useful information.  It just has a link back to here.  Any news about this?

You right :-(

Looks like the last post had some success, your best bet is to try the Gujin forums on sourceforge. Quote all the info on the above post and give as much info as possible.

Try the "cat filename.iso > /dev/sdb" command again, he might have had some bad sectors on his drive.

Once you have used the above command use the fdisk -l command to check that the filesystem is recognized.

Come back to us.

---

### Post by behdad on 2009-08-06
Hi John,

I followed your howtos to install XUBUNTU on my laptop, but I was not able to do so.. 

I cannot install Gujin on my hard drive as I have to unmount it, my hard disk just got two partitions, one 38 gig and the other one just 1 gig which used to be my Debian swap drive.

I did cat the ISO in my swap drive but as I had to unmount my /root to copy the Gujin, my Debian didn't let me to do that.. so I booted the laptop with initrd and vmlinuz which you have pointed recently to boot the laptop with them and copy the Gujin on my first partition.. but Gujin didn't copy successfully and now I have lost my GRUB too :(
Probably it was because of libc6 libraries.

I don't have CDROM, neither USB on my laptop..
Should I throw it away ?

---

### Post by john_spiral on 2009-08-06
> **behdad said:**
> Hi John,

I followed your howtos to install XUBUNTU on my laptop, but I was not able to do so.. 

I cannot install Gujin on my hard drive as I have to unmount it, my hard disk just got two partitions, one 38 gig and the other one just 1 gig which used to be my Debian swap drive.

I did cat the ISO in my swap drive but as I had to unmount my /root to copy the Gujin, my Debian didn't let me to do that.. so I booted the laptop with initrd and vmlinuz which you have pointed recently to boot the laptop with them and copy the Gujin on my first partition.. but Gujin didn't copy successfully and now I have lost my GRUB too :(
Probably it was because of libc6 libraries.

I don't have CDROM, neither USB on my laptop..
Should I throw it away ?

Hi behdad,

Firstly never throw a machine away that's working, all that toxic waste will eventually come back to bite us!

Few questions:

(1) Does your machine have the ability to boot off a network, check BIOS
(2) Is it booting, if not what is the error message?
(3) More specs on the machine (hardware). 

thanks

John

---

### Post by behdad on 2009-08-07
> **john_spiral said:**
> Hi behdad,

Firstly never throw a machine away that's working, all that toxic waste will eventually come back to bite us!

Few questions:

(1) Does your machine have the ability to boot off a network, check BIOS
(2) Is it booting, if not what is the error message?
(3) More specs on the machine (hardware). 

thanks

John

Oh ok.. I'm not going to do that.. just for you ;)

Let me please update my status, I just bought a converter to attach my laptop's hard drive to my PC. 
I made three partitions, 
1. 100 MB, 
2. 37 GIG 
3. 1 Gig

I tried to install Gujin on #1 with this command :
./instboot boot.bin /dev/sda1 --full
and I did cat the ISO on #3 and then I set #1 bootable with Gparted.

But when I boot the laptop with the hard drive it gives me an error about Gujin check sum error, it keeps blinking.

To answer your questions:

1. Yes, it does support PXE but I was considering it the last solution as I have to disable the DHCP server of the router.
2. As I mentioned above it keeps blinking and gives an error about check sum
3. HP Pavilion 4000, Intel Centrino 1.6, 512 RAM, 40 HDD, Phoenix BIOS

Thanks a lot John for your time and help;
Peace.

---

### Post by behdad on 2009-08-08
Oh I finally managed to install it.

The problem was a corrupted Gujin on my MBR and it seems every time that I was installing Gujin on my drive, it was not removing the old MBR, so no matter of my new installation I was keep getting that check sum error.

What I did: I did cat the ISO to /dev/sda, that apparently overwrite the MBR, then I partitioned the drive again

#1 100 MB
#2 37 G
#3 1 G

Then I installed Gujin on #1 :
./instboot boot.bin /dev/sda1 --full

and then I copied the XUBUNTU ISO to #3 :
cat xubuntu.iso > /dev/sda5

I attached the the drive to my laptop and Gujin successfully detected the ISO.
The only problem during installation was about the CDROM, it was complaining that there is no CD in CDROM so I did mount the /dev/sda5 on /cdrom : mount /dev/sda5 /cdrom and I redo the last step again.

So everything went fine and now I have XUBUNTU installed on my laptop.

Thanks again.

---

### Post by john_spiral on 2009-08-08
Excellent! :d

---

### Post by kagashe on 2009-10-31
With Grub2 able to boot ISO I think there is no need to use Gujin.
ISO on sda4/my-ISO and entry in grub.cfg
> ### BEGIN /etc/grub.d/40_custom ###
# This file is an example on how to add custom entries
menuentry "Karmic Live CD (sda4)" {
loopback loop (hd0,4)/my-ISO/ubuntu-9.10-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/my-ISO/ubuntu-9.10-desktop-i386.iso
initrd (loop)/casper/initrd.lz
}The menu entry was put in /etc/grub.d/40_custom and run 'sudo update-grub'

kagashe

---

### Post by john_spiral on 2009-10-31
thanks for the heads up kagashe!

---

### Post by VXxed on 2009-11-05
Well, in Grub 1 I was able to boot the Gujin floppy no problems...but when I tried to boot my Windows XP cd iso it said NTLDR not found...

Please, don't ask why I'm trying to install XP.  It's a long story, but I need it and have no cd drive.  Or USB boot.

---

### Post by etienne_lorrain@yahoo.fr on 2009-11-06
Hi there,

Just want to add some comments on how to use Gujin, for other seeing this thread to go in the right direction...

The command:
./instboot boot.bin /dev/sda1 --full
do not touch the MBR, as described in the docs.
It is only working if your MBR is a standard MBR and will load the "active" primary partition (see your partitionning tool about making that partition active).

If you have a single hard disk, no floppy drive, no USB thumb drive and no CDROM drive, you can install by typing:
./instboot boot.bin /dev/sda1 --mbr --full
or more simply (downloading the latest Gujin version at gujin.org / sourceforge):
./gujin /dev/sda1 --mbr
but it will erase all data on /dev/sda1 and recreate a FAT filesystem in there, so it is a last resort method.
Then Gujin will be able to start the PC and boot an ISO image (like Ubuntu install CD/DVD) which has been copied to another (big enough) partition like:
cat xubuntu.iso > /dev/sda5
sync ; sync         <- to wait that copy is finished before rebooting
After rebooting, you should be able to install Ubuntu without problem.

But in general, to install Gujin if you have Ubuntu installed on your PC, you either install the .deb package (see gujin.org / sourceforge) or (assuming you have a single hard disk and you are root / use sudo), just download the gujin executable (or gujin64 on a 64 bits system) and type:
gujin /boot/gujin.ebios
The Gujin installer will take care of everything, like the MBR.

Etienne.

---

### Post by john_spiral on 2009-11-07
> **VXxed said:**
> Well, in Grub 1 I was able to boot the Gujin floppy no problems...but when I tried to boot my Windows XP cd iso it said NTLDR not found...

Please, don't ask why I'm trying to install XP.  It's a long story, but I need it and have no cd drive.  Or USB boot.

Hi, did you write the XP iso to a partition?

---

### Post by john_spiral on 2009-11-07
> **etienne_lorrain@yahoo.fr said:**
> Hi there,

Just want to add some comments on how to use Gujin, for other seeing this thread to go in the right direction...

The command:
./instboot boot.bin /dev/sda1 --full
do not touch the MBR, as described in the docs.
It is only working if your MBR is a standard MBR and will load the "active" primary partition (see your partitionning tool about making that partition active).

If you have a single hard disk, no floppy drive, no USB thumb drive and no CDROM drive, you can install by typing:
./instboot boot.bin /dev/sda1 --mbr --full
or more simply (downloading the latest Gujin version at gujin.org / sourceforge):
./gujin /dev/sda1 --mbr
but it will erase all data on /dev/sda1 and recreate a FAT filesystem in there, so it is a last resort method.
Then Gujin will be able to start the PC and boot an ISO image (like Ubuntu install CD/DVD) which has been copied to another (big enough) partition like:
cat xubuntu.iso > /dev/sda5
sync ; sync         <- to wait that copy is finished before rebooting
After rebooting, you should be able to install Ubuntu without problem.

But in general, to install Gujin if you have Ubuntu installed on your PC, you either install the .deb package (see gujin.org / sourceforge) or (assuming you have a single hard disk and you are root / use sudo), just download the gujin executable (or gujin64 on a 64 bits system) and type:
gujin /boot/gujin.ebios
The Gujin installer will take care of everything, like the MBR.

Etienne.

Hi Etienne, you must be the very 'Etienne Lorrain' who wrote the Gujin  PC boot loader?

If yes, great to have you posting on this thread :-)

---

