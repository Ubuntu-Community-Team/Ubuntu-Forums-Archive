---
title: "Mounting Fail :( Can not mount external drive"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by ajwiddershins on 2012-03-04
g'Morning everyone! 

As a beginner -- some very limited terminal experience -- I need help mounting my external drive. When connected (via USB chord) it whirs and lights up all ready to go, but then the light just blinks coyly at me while it hides, unmounted. Poop.

FYI, I installed Ubunta via the Ubuntu Desktop Edition CD.

Heads up: this may've been the result of a tumble (I use a clunky old laptop and probably got up quickly while the harddrive toppled from its place and disconnected from the chord), which has happened once or twice before, but hadn't resulted in not being able to mount. When I first began using the device, i had a hard time convincing it cooperate. It hasn't been problematic for several long months, but perhaps the abuse made it change its mind. (I suppose a lot of us beginners take to obnoxiously personifying our machines....)

After searching, I came up with [this thread]("http://ubuntuforums.org/showthread.php?t=1930319&highlight=device+recognized"). Some of it got me in the right direction... Here's what I've toyed with and attempted: 

1) First I tried a command that, by the looks of that thread, displays what devices are available: ```
sudo fdisk -l
```
My external hard drive was on the list! Sweet. ...i think?

2)] After that, I realized that thread was significantly different than the help I needed for several different reasons, but kept it in mind while considering [this Ubuntu Documentation page MountUSB]("https://help.ubuntu.com/community/Mount/USB")
Here I read and confirmed that...> By default, storage devices that are plugged into the system mount automatically in the /media directory, open a file browser window for each volume and place an icon on your desktop. If you plug in a usb hard disk with many partitions, all of the partitions will automatically mount. This behaviour may not be what you want so you can configure it as shown below.

If the volumes have labels the icons will be named accordingly, otherwise they will be named "disk" and as more volumes are added, you can get "disk-1" and so on.
Being that I didn't want to alter any automounting, I read about configuring automounting, followed the steps and confirmed that both **/apps/nautilus/preferences/media_automount_open** and **/apps/nautilus/preferences/media_automount** were "checked".

3) Then I skipped down to section about [manually automounting]("https://help.ubuntu.com/community/Mount/USB#Manually_Mounting") and followed those steps:
```
apple@apple-MM061:~$ sudo fdisk -l
[sudo] password for apple: 

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8191

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9164    73606144   83  Linux
/dev/sda2            9164        9546     3069953    5  Extended
/dev/sda5            9164        9546     3069952   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)
  

```
I also used the following to discern the "vendor id", which i sensed could come in handy
```
apple@apple-MM061:~$ lsusb
Bus 005 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I followed the instructions as they'd been, and went on to " create a mount point for the device, let's say we want to call it "external". You can call it whatever you want, just please don't use spaces in the name or it gets a little more complicated - use an underscore to separate words (like "my_external")." To be specific, using the vendor ID, I used "external_passport", like this:
```
apple@apple-MM061:~$ sudo mkdir /media/external_passport
```
But because I'm new and going at this alone, I also made one with just "media/external", not knowing that if "nothing happens" when I press enter, it doesn't actually mean "nothing happened". So I guess I created two directories?

4) Continuing in an uncertain effort to "mount the drive", as per the page's instructions, I went ahead with this:
```
sudo mount -t vfat /dev/sdb1 /media/external_passport -o uid=1000,gid=1000,utf8,dmask=027,fmask=137

```
Yay! Passport made a noise at me. Cute.   ...But didn't mount :( 
And terminal told me this:
```
mount: /dev/sdb1: can't read superblock

``` 
Crap. I don't even know what I superblock is :(

Confused and troubled -- and worried that I was effing it all up -- I opted to stop and try something else. Because I was uncertain if the thing was mounted in anyway, I tried to "unmount" it with the code, and it was confirmed it was never mounted to begin with.

I should probably here note that above, where you see "/dev/sd**b**1" in the codes from *my terminal*, I'm pretty certain the first time i tried this, it was "/dev/sd**c**1" or something similar and certainly different from "/dev/sdb1". I don't know what's changed that, but it could have to do with any of the following:

Returning to the thread I found in my search, I thought I'd give the first suggestions a go:

> You could try installing **usbmount** .. works for my USB devices

So I went to the Synaptic Package Manager and searched for usbmount and applied the change to install it. Then I reconnected the drive, but still no mountage. 

Reading the rest of the thread, I'm unable to decipher what is applicable to my situation and what would be useless to try, being that I'm not trying to recover data specifically, as that user had been. 

I did try to take my external drive to another computer to see if it would mount there -- it was my housemate's laptop, a Windows of some kind (I don't know Windows very well). The laptop made an intriguing "pop" alert noise, and I saw that an icon had shown up, indicating to me it was *probably* mounted. However, the battery on this laptop was dying and it went into hibernate before I could open the External Harddrive to confirm. This, I will have to try again later.

Good news is nothing exploded ... yet.

In the meantime -- Got any advice??

As I said, I'm pretty dern new and jargon intimidates and frustrates me, but i can see where it's necessary sometimes. Hopefully I've been adequately informative!

I asked because all my resumes and music are on the hard drive  -- pretty much everything important in my life right now :cry: (i'm sure you understand). I'd loathe to give up.

---

### Post by TeoBigusGeekus on 2012-03-04
> **ajwiddershins said:**
> 
```
mount: /dev/sdb1: can't read superblock

``` 


Go to your friend's win laptop, connect the drive and, once it shows up under My Computer, right click it and select "Scan for and Fix Errors" or something like that.
Don't worry about creating 2 folders under /media; you can delete them later.

---

### Post by ajwiddershins on 2012-03-04
Thanks! Just gave this a try. There was a "Troubleshoot" or "Fix Problems" type option upon right-clicking. The attempt to recovery took about five minutes, but it said it could no resolve any errors. :( I tried to access something about discovering other methods of resolving the problem, but the program became unresponsive. Upon trying again, the drive made Windows Explorer unresponsive, too. 

Am I doomed?? :?

---

### Post by fleamour on 2012-03-04
Did you invoke CHKDSK from right click context menu?

[http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors](http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors)

---

### Post by ajwiddershins on 2012-03-06
Probably not -- that doesn't sound familiar. 

The PC/windows I'm using is really not liking this or cooperating though. As soon as my external drive is plugged in, it slows up and becomes somewhat unresponsive (maybe it's like this all the time though, I don't know).

From the link provided previously:
> Click the Tools tab, and then, under Error-checking, click Check Now.   If you are prompted for an administrator password or confirmation, type the password or provide confirmation.

There is no Tools tab :( 

I did search around a little bit:
Right click > Properties the two tabs available are General and Hardware. Under Hardware, There are two devices listed, both are USB devices. Under the Type column, one is "Universal Serial Bus..." and the other "Disk Drive". I assumed this second one is mine. I click on it and go down to a second Properties button. A new window shows four tabs, General, Volumes, Driver and Details. In the General tab, under Device status, is says "This device is working properly." Underneath here there's a button: Change Settings. This adds a fifth tab for Policies, which seems to pertain only to method of removal of the device.

Trying to open or "browse files" just seems to give me the swirling, blue, circular vortex of no return. :confused:

The owner of the PC mentioned she thought this could just be that my external drive is too big. I don't really know if that's a potential problem or not. 

> Depending upon the size of your hard disk, this may take several minutes. For best results, don't use your computer for any other tasks while it's checking for errors.

I also have no way to know if there are oodles of weird, sneaky background programs running, which could be interfering, perhaps? I don't want to troubleshoot a whole separate OS if I can avoid it... If not, c'est la vie.

FYI, my access to this PC is pretty darn limited/inconsistent. If it's the best/only route so far, I'll keep trying to use it. If there are some creative methods to explore using my own OS, I'm open to that, too. 

Thanks lots for the ideas thus far.

---

### Post by ajwiddershins on 2012-03-06
Oh, in the department of creative strategies, I could see if a friend with a MacBook could let me try farting around with it there. In my experience, the Mac OS's are a lot less obnoxious than Windows PC. If I get this opportunity, I'll report back. 8)

---

### Post by Mark Phelps on 2012-03-07
If dropping the WD drive resulted in sector faults (which are very likely if it is still running), then what is most probably happening is that opening the filesystem is hanging on those faults -- which can slow it to crawl. I've had damaged drives sit for over 30 minutes before the filesystem scanning finished to allow me to open it.

You don't say which version of Windows you're using (or I missed it) but in Vista and Win7, you click the COMPUTER entry in the Start Menu, then right-click the "drive" in question, and then select Properties.  Once you do that, you should see a Tools tab for that "drive" (what MS calls partitions).

---

### Post by ajwiddershins on 2012-03-07
Well, that's a bit hopeful! Good, good, I like where that could be going. I definitely haven't patiently let it sit for long on any OS, incl. my Ubuntu.

Just confirmed it's Windows 7 ("Starter"? ...Whatever that means.) "Properties" was available from a drop-down menu upon right-clicking. No "Tools" tab -- as a matter of fact, the new screen that came up looked nothing like it did in this link at all: 
[http://www.sevenforums.com/tutorials/433-disk-check.html](http://www.sevenforums.com/tutorials/433-disk-check.html)

There were several options listed in a column on the left hand side. One of which was something to the effect of "Advance preferences and Tools". I tried that, did not see anything that looked like CHKDSK. *eye twitch*

When I went to try again -- to make sure I was doing it right -- Windows explorer become unresponsive. At this point, I can't get past it continually becoming unresponsive.

Is it worthwhile to keep going on this OS if it becomes so unresponsive that I am waiting for up to 20 minutes just to close unresponsive programs??? I understand patience is a rare and valuable tool, and I can embrace it if needed. The rate of functionality this particular PC seems to be exhibiting makes me think perhaps it would be best if we assumed that no PC was available to me at all? 

Currently, I'm trying again. The "shiny" green bar loading the Hard Disk Drives is at like 95%, but hasn't loaded all the way. It's been lagging there for the past 5 minutes. I'll keep waiting to see if it does load before the PC owner wakes up/wants her PC back.

---

### Post by ajwiddershins on 2012-03-07
Donnerwetter! Nothing :( I've learnt that right-clicking the hard drive (from the Computer directory) will make Windows Explorer unresponsive -- that seems to be regardless of what I do. 

From the Devices and Printers directory (still on Windows 7), I've been trying to browse files, just to see what happens. The status bar is again at about 95% and I'll keep waiting to see what happens --if anything -- for as long as I can.

In the meantime.... other suggestions?? [-o<

**Edit** About a half-hour into the process of attempting to browse files, a pop-up is now telling me: D:\ is not accessible. The request could not be performed because of an I/O device error. I click OK. Windows then becomes unresponsive again.

---

### Post by ajwiddershins on 2012-03-16
Is it be inappropriate for me to bump this thread? Truly, if anyone has read this and believes this case to be completely impossible, I'd like to know that at the very least.

---

### Post by Nightstrike2009 on 2012-03-16
Dont know if this will help but during partioning (Gparted) in the installer i usually set the mount point to "/" and set the boot loader to the first hard disk. This works fine for me don't know whether this helps but just a suggestion :-)

PS: I dual boot Windows 7 and Ubuntu 11.10 this way.

---

### Post by duke.tim on 2012-03-16
If the drive is damaged i'd see if you can backup the data and get a new drive.

You might need to use something that works a bit differently than check disk, to 'repair' the drive. It might be worth looking into something like spinrite

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

It costs money, but is a great tool. 

There are some open source tools that do similar repairs, Though they are more difficult to use.

ddrescue, dd_rhelp,

---

### Post by ajwiddershins on 2012-03-20
: ) Thanks for responding...

> Dont know if this will help but during partioning (Gparted) in the installer i usually set the mount point to "/" and set the boot loader to the first hard disk. This works fine for me don't know whether this helps but just a suggestion :)

... not really sure what this means tough. Specifically, what is "partioning", "Gparted" and "the installer"? Is that something I should integrate into the codes I'd originally tried?? Also, I'm not sure what a boot loader is either. **Nightstrike2009**, Can you elaborate?

**duke.tim** > There are some open source tools that do similar repairs, Though they are more difficult to use. 

It seems as though that's the general pattern I'm seeing ... 
I'll look into pricing something that could help with restoring the data.

---

### Post by flurospar on 2012-03-20
> **ajwiddershins said:**
> ... not really sure what this means tough. Specifically, what is  "partioning", "Gparted" and "the installer"? Is that something I should  integrate into the codes I'd originally tried?? Also, I'm not sure what a  boot loader is either. **[...]** Can you elaborate?

In layman's terms, "partitioning" means diving the space of a single storage device into different drives.

**Primary Partition** is a partition that is needed to  store and boot an operating system, though applications and user data  can reside there as well, and what&#8217;s more, you can have a primary  partition without any operating system on it. There can be up to a  maximum of four primary partitions on a single hard disk, with only one  of them set as active (see &#8220;Active partition&#8221;).
 **Active (boot) partition **is a primary partition that  has an operating system installed on it. It is used for booting your  machine. If you have a single primary partition, it is regarded as  active. If you have more than one primary partition, only one of them is  marked active (in a given PC session).
 **Extended partition** can be sub-divided into logical  drives and is viewed as a container for logical drives, where data  proper is located. An extended partition is not formatted or assigned a  drive letter. The extended partition is used only for creating a desired  number of logical partitions.
 **Logical drive** is created within an extended  partition. A logical partition is a way to extend the initial limitation  of four partitions. An extended partition can contain up to 24 logical  partitions (you&#8217;re limited by the number of drive letters and the amount  of hard drive space available for creating drives; of course, it&#8217;s  senseless to use 24 partitions on a system in most cases, because it  will be a data organization nightmare). Logical partitions are used for  storing data mainly, they can be formatted and assigned drive letters;  their details are listed in the extended partition&#8217;s table - EMBR  (Extended Master Boot Record).




"Gparted" is a partition editor (helps you create, delete and resize partitions.)

The installer he refers to is the Ubuntu installer, the one which you see when you boot Ubuntu from the CD. It's also known as Ubiquity

> **ajwiddershins said:**
> I'll look into pricing something that could help with restoring the data.

You could try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") , which is free and open-source, to recover your files.

For a GUI, Windows-only program for recovering files, have a look at [Recuva]("http://www.piriform.com/recuva/").

And as for checking your hard disk for errors (on Windows), could you try this:

Press Winkey+ R and type "%comspec%". In the command prompt window, type:

```

chkdsk X:

```replacing X: with whatever your drive is named as.

---

### Post by ajwiddershins on 2012-08-01
Recently a friend and I discovered that replacing the enclosure could yield results. We found out that the hard disk responded in at least some way when we connected just the hard disk after removing it from the original WD Passport enclosure. 

I've connected again using this enclosure, and started again from the top. 

Entering this, however,
```
sudo mount -t vfat /dev/sdb1 /media/external_passport -o uid=1000,gid=1000,utf8,dmask=027,fmask=137

```

... has resulted in this:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

... which i don't recall happening previously.

---

### Post by ajwiddershins on 2012-08-06
Alright, back to the Windows method:

I was using the following PC:
[B]OS Name    Microsoft Windows 7 Home Premium
Version    6.1.7601 Service Pack 1 Build 7601[/B]

Merely attempting to right click on the drive icon resulted in Windows Explorer becoming unresponsive. Here are the details:
> 
Description:
  A problem caused this program to stop interacting with Windows.

Problem signature:
  Problem Event Name:    AppHangB1
  Application Name:    explorer.exe
  Application Version:    6.1.7601.17567
  Application Timestamp:    4d672ee4
  Hang Signature:    8e01
  Hang Type:    4
  OS Version:    6.1.7601.2.1.0.768.3
  Locale ID:    4105
  Additional Hang Signature 1:    8e01584c4564368b99422649011e747c
  Additional Hang Signature 2:    4094
  Additional Hang Signature 3:    4094871afc2f6c73b39d5019e703d1de
  Additional Hang Signature 4:    fe8d
  Additional Hang Signature 5:    fe8d3888d0fe19db9031b5977cb3a6b2
  Additional Hang Signature 6:    09e5
  Additional Hang Signature 7:    09e52d12a058221cf36d4ba2d3089a0b


Can anyone provide any insight based on that info.??

---

### Post by duke.tim on 2012-08-07
Since it can not read the Superblock, which records information about the filesystem try this (in linux) to identify where the primary and backup superblock is:

```
# dumpe2fs /dev/sdb1 | grep -i superblock
```

If a backup is available you can use that to restore the primary Superblock 


This is where I found the information, the web page will explain superblocks and may aid you in restoring the drive.

[http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html)

p.s. this is my limit of my superblock knowledge so google is in order if the redundant copies of the superblock are found.


If you are trying to decode windows errors good luck, try searching msdn and technet.

this might help you get started
[http://blogs.msdn.com/b/wer/archive/2009/03/19/let-there-be-hangs-part-4-better-bucketing-in-windows-vista.aspx](http://blogs.msdn.com/b/wer/archive/2009/03/19/let-there-be-hangs-part-4-better-bucketing-in-windows-vista.aspx)

---

