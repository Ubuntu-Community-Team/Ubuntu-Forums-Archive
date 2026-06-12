---
title: "HOWTO - Discovering and using existing sata raid (eg sil3112)"
date: 2004-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by dave_blob on 2004-10-29
DISCLAIMER: this is my first HOWTO, so ill probably get a lot of the style wrong. I just had huge trouble finding information on this problem, and i thought i should pass it on now ive solved it.
[B]
What this is for[/B]: People who have a SATA(serial ATA) raid controller, such as the sil3112 controller that comes on the Abit NF-7 S motherboard, and want to use this raid though the controller.
This is *NOT* for people with new, blank hdds. For you it is much easier IMHO to set them up using linux software raid, i believe that there is a howto on this forum already for that. 
This *is* for people who need to access raid arrays they have already created, in my case i am dual booting with winxp and i have a large amount of data i need to access in linux. 
It is supposed to support these raid controllers:
Highpoint HPT37X
Highpoint HPT45X
Intel Software RAID
Promise FastTrack
Silicon Image Medley


Right, lets get started. These instructions are adapted and fleshed out from the original dmraid(the program used to discover the raid devices) README.

1) download and install your kernel source, you can follow the instructions up to and including 'unpacking your kernel' in the kernel howto wiki
[http://wiki.ubuntulinux.org/KernelHowto](http://wiki.ubuntulinux.org/KernelHowto)

2) Lucky for Ubuntu users, the 2.6.8 kernel that ships with warty final already has the device mapper base code!  :)  That means for raid-0 people there is nothing to do for step 2, goto 3! 
If you want to use raid-0,5 or append, you will need to apply some kernel patches and build a new kernel. 
For the 2.6.8.1 kernel they are here:
[ftp://sources.redhat.com/pub/dm/patches/2.6-unstable/2.6.8.1/](ftp://sources.redhat.com/pub/dm/patches/2.6-unstable/2.6.8.1/)

Apply these patches to your kernel source using something like:
cd /usr/src/linux
sudo cat <directory containing patches>/*.patch > patch -p1

Then build your kernel following the instructions in the wiki link above.

3) Install the device mapper userspace. This is located at [ftp://sources.redhat.com/pub/dm/](ftp://sources.redhat.com/pub/dm/)
You might as well get the latest version, which at time of writing is device-mapper.1.00.19.tgz. 
Untar this somewhere and go into the directory tar creates.
then run 
./configure
sudo make install

4) download the dmraid software
[http://people.redhat.com/~heinzm/sw/dmraid/src/dmraid-current.tar.bz2](http://people.redhat.com/~heinzm/sw/dmraid/src/dmraid-current.tar.bz2)

Untar it, and again go into the directory it creates. 
./configure
sudo make install

Almost done!

5) now everything is installed. You just need to make dmraid  load on startup and set up the drive mounting. 
I didnt make mine load on startup, as i do not need to access my raid drives all that often. So i made a little script to mount them when i need them in my home directory.
Heres how:

You need to find your device name. 
ls /dev/mapper/

There will be a few entries that look long and confusing. They are actually just the partitions of your raid drives, prefixed with a complex name. mine looks like
sil_0309402025011
sil_0309402025011_p1
sil_0309402025011_p5

you need to note these down.

make a new file called activateraid in your home directory.
Put this code in it :

dmraid -ay -v
mount -t <fs type> -o users,owner,ro,umask=000  dev/mapper/<your partiton name> /<your mount dir>

and add another line for every partition you have.
Save the file.
chmod 700 activateraid

6) Now test it! run
./activateraid
and all your drives should mount! 

:D!
Hope it works for you. I was so stoked when i finally found this solution. Worth noting is that Ubuntu is the only distro of 3 or 4 ive tried that had the devicemapper code included in a form that was useful for this to work. Yay Ubuntu! :)

---

### Post by regi on 2004-12-29
THX, for this HowTo!

It works perfectly for me.

I have two 80gb HD at RAID-0.

Can i install ubuntu on this array?

sorry for my bad english.

---

### Post by kral on 2005-01-02
[QUOTE=regi]THX, for this HowTo!

It works perfectly for me.

I have two 80gb HD at RAID-0.

Can i install ubuntu on this array?

sorry for my bad english.[/QUOTE]

at first, thx for that nice Howto.
but, I think its most for consultation purpose, and not for instalation. as mentionned above, it should be an existing howto about installing unbuntu on sata raid. i will edit and put that url as soon as I find it.

---

### Post by movement3 on 2005-01-05
Thank you for the how-to, able to read my two hds in a raid0!

---

### Post by Zillion on 2005-02-15
Tx for the info.

[QUOTE=kral]at first, thx for that nice Howto.
but, I think its most for consultation purpose, and not for instalation. as mentionned above, it should be an existing howto about installing unbuntu on sata raid. i will edit and put that url as soon as I find it.[/QUOTE]

I also want to know how u can install Ubuntu on an existing sata raid 0, like when using an onboard Silicon Image raid controller. Any info in n00b terms would be more than welcome.

---

### Post by Zillion on 2005-02-19
[QUOTE=dave_blob]
This *is* for people who need to access raid arrays they have already created, in my case i am dual booting with winxp and i have a large amount of data i need to access in linux. [/QUOTE]

Do u have Windows XP installed on the raid stripe, or only data? If so then u prob have a 3rd hdd for linux? tx

---

### Post by Grey on 2005-03-07
Okay, I'm just a little confused here...  Does this only work with SATA?  I've got 2 IDE drives in RAID-0 on a Fasttrak 378 SATA/IDE RAID controller.  I haven't installed the kernel patches, as I am still somewhat of a newbie, and I don't have internet access without my madwifi module, and the kernel I built with the custom patches doesn't have that module included.  And I just kind of assumed that given your comment in step 2...  I didn't have to do that anyways.

But I've followed all the other steps, and all that's in dev/mapper/ is a device called "control".

Am I just plain screwed?

---

### Post by mlidman on 2005-03-17
you need to activate your raid. That is what the 'dmraid -ay -v' is for. Once you do that you will see your partitions in /dev/mapper

----

Edit Mar 24 2005:
Problem fixed. I emailed the developer and he fixed the bug that was cuasing my problem. He was vary responsive and helpful. 

----

I'm having trouble of my own. The compile for device mapper and dmraid appear to go just fine. But when I do a 'dmraid -ay' I get the message

ERROR: sil: invalid metadata checksum on /dev/sdb
ERROR: sil: invalid metadata checksum on /dev/sdb
ERROR: sil: invalid metadata checksum on /dev/sdb
ERROR: sil: invalid metadata checksum on /dev/sdb

In /dev/mapper I have

control  sil_afadbgdebbdeb  sil_afadbgdebbdeb1

There are supposed to be two ntfs partitions on the raid on /dev/sda and /dev/sdb

When I mount the drive sil_afadbgdebbdeb1

sudo mount -t ntfs -o users,owner,ro,umask=00 /dev/mapper/sil_afadbgdebbdeb1 /windows/h

and do an ls I get

ls: reading directory /windows/h: Input/output error

edit: i forgot to mention i'm running horey 5.04 with the 2.6.10-5-k7 kernel. I'm running an asus A7N8X Deluxe with the Sil 3112A Controller with two WD 160 7200 sata drives on them. They are raided together and partitioned into a 260 and 60 gig ntfs partitions made by windows xp sp2. I have 2 maxtor 200 7200 ata drives where I have winxp duel booting with ubuntu.

---

### Post by Grey on 2005-03-21
dmraid -ay -v told me that there were no software RAID disks.  :(  Which I would assume means that this whole thing doesn't apply to me?

---

### Post by Tichondrius on 2005-03-22
[QUOTE=Grey]dmraid -ay -v told me that there were no software RAID disks.  :(  Which I would assume means that this whole thing doesn't apply to me?[/QUOTE]
 me too. I think it's because the raid controller is not supported. Mine is VIA 8237 southbridge raid controller.

---

### Post by Grey on 2005-03-27
For whatever reason, when I upgraded to Hoary and kernel 2.6.10, I decided to test this one more time.  And you know what?  I freaking LOVE YOU GUYS!

```
[img]http://people.uleth.ca/~dave.brady/raid.png[/img]
```

I can confirm that this works with a Promise Fasttrak 378, and IDE hard drives.  My Linux partition has just become incredibly more useful, thanks to everyone in this thread.   \\:D/   I am going to have a huge smile on my face for the rest of the night.  I don't need Windows anymore.

---

### Post by justme on 2005-03-31
the mapper finds and activates my raid partitions,
I can see them in GParted, but the filesystem on them remains unknown. 
I know it's ntfs, but even forced mounting doesn't work.

they are :
via_bhbacfbfae  via_bhbacfbfae1

any idear ?

---

### Post by MiddleBrooker on 2005-04-14
Hy Guys,

First: MANY THANKS for this howto because it works perfectly  ;-) 

Second: Now I would like to install directly Ubuntu Hoary into my two SATA Hard Disk in RAID 0 configuration by the Nvidia Raid Chip, builtin in my Shuttle XPC with Nforce3 based mainboard.

In my previous test I've saw that Hoary can recognize correctly my SATA Hard Disk in RAID 0 mode but at the partion step I don't see only one disk with the total capacity of my TWO phisical disk....I see always two disk like a setup without RAID 0 configuration; the reason should be that my RAID 0 configuration is for Linux a software raid.

After that I've tried to make two equal partitions on both disks with Linux RAID filesystem, so I can setup the MD software raid...all seems to be ok but not for the Grub installation, because seems that Grub cannot be installed on Software RAID partition.

My next test is to make the same things but install Grub on a normal floppy disk using this procedure by Fuche :

```
In the installation menu, I opened a shell and navigated to /target/boot/grub
There I edited the devices.map file (nano devices.map) and add a new line at the end -- (fd0) /dev/fd0
Save and exit, and in the line for grub installation path I enter /dev/fd0 and thst's it, it worked.

``` 

I hope that this is not a problem for boot up my root partition after a reboot, buy I've a lot of dubious.

I would like to have some suggestion about this type of installation, because I like the RAID 0 speed and for me this is a big issue, I'll be very happy to install both Windows and Ubuntu into my RAID 0 setup.

Another question is: Should be a good idea to make my partiton before Ubuntu installation through a Partition Magic bootdisk that is able to see my RAID 0 setup like only one disk with the total capacity of my phisical two disk?


Thanks for all the replyes.
MiddleBrooker

---

### Post by jr_G-man on 2005-04-14
This howto worked great for me...and things are working fine according to the original instructions.

However, does anybody have any idea how to set this up automatically during bootup?

---

### Post by shakey on 2005-05-02
Sorry for dragging this thread up, but it seemed appropriate

I followed the how-to given at the start of this thread, and all went well. almost.
I can see my raid array in GParted fine and correct, but when i try to run the "activateraid" scrip i get this:

> INFO: Activating stripe RAID set "sil_afaddgceajabb"
INFO: Activating partition RAID set "sil_afaddgceajabb1"
INFO: Activating partition RAID set "sil_afaddgceajabb5"
mount: special device dev/mapper/sil_afaddgceajabb1 does not exist
 

But it does exist! I've seen it!

Help? Please?

---

### Post by gorilla on 2005-05-09
thanks for the guide, works like a charme :)
just allow me a few stupid questions:

is there a way I can prevent getting icons of the mounted partitions on the desktop? It's not really important, but I prefer a icon-less desktop.

The drives are pretty slow, but hdparm doesn't work properly on it. Is there something I can do to improve performance?

anyone using it with read/write access? how safe would it be? the dmraid readme states that since it's a rc version, write access could destroy data. I just wonder how likely this "could" is.. it's just that since my linux drive is pretty small, i'm in a need for alternative hdspace..

---

### Post by vfactor on 2005-05-28
Hi

Thank you for the tutorial

I am a comple newbie to Linux and have a hard time understanding it but with these how to, my life gets much easier 

I follow this guide to make my Ubuntu sees the RAID 0 build on my on board SATA RAID controller (Sil3112 , NFS-S)

Everything goes smooth ( I didn't do step 2 ) til I do **ls /dev/mapper/**  which only return me one item  **control**

well as you can guess I am stuck :)

By the way I have a HighPoint Rocket 133SB on board too.

On /dev/ folder I saw my hard disk on the Highpoint controller and the satas on the SATA RAID but can't mount them, is that normal ?


My kernel is the latest one 2.6.10 with Ubuntu patches.


Any help is appreciate.

Thank you

---

### Post by derelict_frog on 2005-07-19
This looks like exactly what i need to get my raid0 partition to show up, i have the silicon 3112 controller onboard.

But when u say these bits:
"3) Install the device mapper userspace. This is located at [ftp://sources.redhat.com/pub/dm/](ftp://sources.redhat.com/pub/dm/)
You might as well get the latest version, which at time of writing is device-mapper.1.00.19.tgz.
Untar this somewhere and go into the directory tar creates.
then run
./configure
sudo make install

4) download the dmraid software
[http://people.redhat.com/~heinzm/sw...current.tar.bz2](http://people.redhat.com/~heinzm/sw...current.tar.bz2)

Untar it, and again go into the directory it creates.
./configure
sudo make install"

Does dragging the configure files into root terminal then running them fromt here work? and where do i have to type in sudo make install?

And after doing 3 & 4 after im sure they didnt work i create the file and run it from root terminal and get this:

root@ubuntu:/home/ubuntu # /home/ubuntu/activateraid
/home/ubuntu/activateraid: line 1: dmraid: command not found
mount: special device dev/mapper/casper-cow does not exist


The things in my ls /dev/mapper/ are:
casper-cow  casper-snapshot  control


Any help would be awesome!!!!!!!!!!!

---

### Post by Alessio on 2005-07-22
[QUOTE=vfactor]Hi


Everything goes smooth ( I didn't do step 2 ) til I do **ls /dev/mapper/**  which only return me one item  **control**
[/QUOTE]
Same problem, with promise fasttrack. I must divide the array in two device with stripe mode? Now the controller view 2 mirrored device..

```

randa:~# dmraid -r
/dev/hde: pdc, "pdc_eaedhfdh", mirror, ok, 80293185 sectors, data@ 0
/dev/hdf: pdc, "pdc_eaedhfdh", mirror, ok, 80293185 sectors, data@ 0

```

then..
```

randa:~# dmraid -ay   
pdc_eaedhfdh already active
ERROR: dos: reading /dev/mapper/pdc_eaedhfdh[Invalid argument]

```

---

### Post by Marcs316 on 2005-07-24
Sorry for bumping such an old thread, but I've been lost for a while trying to get this to work. Here's what I have so far:

I've got everything install and the RAID is recognized as "via_bdibeiahhj". Everything seems ok but when I try and mount it from "/dev/mapper/via_bdibeiahhj" it tells me it's already mounted.

My only choices are "control" "via_bdibeiahhj" and "via_bdibeiahhj1". 

The command I've been using to try and mount the device is:

```
mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/via_bdibeiahhj /mnt/windows
```

Any help would be great. Sorry if I haven't posted in any correct format, I hope you can make sense of all that. And sorry for bumping this, I'm just stuck.

---

### Post by [_Silence_] on 2005-08-09
[QUOTE=shakey]Sorry for dragging this thread up, but it seemed appropriate

I followed the how-to given at the start of this thread, and all went well. almost.
I can see my raid array in GParted fine and correct, but when i try to run the "activateraid" scrip i get this:

>  INFO: Activating stripe RAID set "sil_afaddgceajabb"
INFO: Activating partition RAID set "sil_afaddgceajabb1"
INFO: Activating partition RAID set "sil_afaddgceajabb5"
mount: special device dev/mapper/sil_afaddgceajabb1 does not exist

 

But it does exist! I've seen it!

Help? Please?[/QUOTE]

 I have the exactly same problem, running 2x 160Gb SATA in Raid0, NForce4 controller.
 Anyone know why it says that?

---

### Post by [_Silence_] on 2005-08-09
[QUOTE=shakey]Sorry for dragging this thread up, but it seemed appropriate

I followed the how-to given at the start of this thread, and all went well. almost.
I can see my raid array in GParted fine and correct, but when i try to run the "activateraid" scrip i get this:

>  INFO: Activating stripe RAID set "sil_afaddgceajabb"
INFO: Activating partition RAID set "sil_afaddgceajabb1"
INFO: Activating partition RAID set "sil_afaddgceajabb5"
mount: special device dev/mapper/sil_afaddgceajabb1 does not exist 

But it does exist! I've seen it!

Help? Please?[/QUOTE]

 I have the exactly same problem, running 2x 160Gb SATA in Raid0, NForce4 controller, but using Ubuntu 5.0.4.
 Anyone know why it says that?

---

### Post by meycauayan on 2005-08-10
Can anyone help... I have 2 sata hdd set as raid "0" and it 's working fine. I wanted to add an extra drive , an ide ata 133 because i wanted to retrieve some datas in it. I have tried with no avail. I do not even know if it 's possible to do so. My M/B is  asus p4c800 e deluxe..2x120 maxtor sata as raid "0".

---

### Post by mickc1303 on 2005-08-17
Just had to register to say thankyou for this great guide..

After trying various linux distros over the last year I never managed to get to access my sata raid 0.

Now after an hour, mostly down to typo's on my behalf I can access my NTFS SATA partition!!!!

 :grin:

---

### Post by TomalakBORG on 2005-08-19
I too signed up just to say 'thank you'

THANK YOU

All I had to do was run dmraid -ay and life is good! Thanx a bunch!

I have two 160gb sata drives in a raid 0 with ntfs on them. I have it set up to mou tnat boot time. Thank you for such a good guide. I run slackware, so it was a good thing this guide is distro independant. Any 2.6 variety of kernel has device-mapper support in it. 

Thanks again, -Bill

---

### Post by heltreko on 2005-08-22
Thanks for the howto.

Managed to get my striped set (RAID0) working following this howto.

2 x Seagate SATA disks on an VIA VT6420 controller (ASUS A8V Deluxe motherboard).

---

### Post by jose.home on 2005-09-07
Hello,

Could you please provide more details?

I'm using WinXP now, with 2 160Gb HDD in RAID0. I left 40Gb Partition Free to install Ubuntu, but as some of you, ubuntu installer recognize 2 160Gb HDD instead 1 RAID set. My Mobo is ASUS A7N8X-E Deluxe with Sil3112 Controller.

Even last ubuntu beta has same behavior on installer.

About the description to install kernel, it seems how to install from Linux, but, could you provide more details about how it is done since boot?

How did you boot the system to install new kernel? By LiveCD? Floppy Disk?

I cannot find any good description over the internet.
Several people says that is better install Linux Raid instead Sil3112 Raids, but I already has installed, and worried to lost my WinXp data.

Any help will be welcom.

---

### Post by saschxd on 2005-09-08
still no go for ATA RAID ? 

i have HPT372 on a DFI Lanparty mobo, 
with 2x 120 GB attached, i even managed to get windows installed on it  ;-) , 
but i can't figure it out on ubuntu 5.04 (didn't try another distribution for that purpose, yet) ...  :? 

all i get after following the steps is also an empty  
/dev/mapper/control 

maybe some mind get us some help with the opensource driver they provide ?
[http://www.highpoint-tech.com/BIOS%20+%20Driver/rr133/Linux/hpt3xx-opensource-v2.0.tgz](http://www.highpoint-tech.com/BIOS%20+%20Driver/rr133/Linux/hpt3xx-opensource-v2.0.tgz)

i'm used to osx, and a very little to debian, but this is all completely new to me, 
and, besides, giving me a headache  ](*,) 


any help greatly appreciated, 
thanks in advance 
saschxd

---

### Post by communico on 2005-09-12
when I type dmraid -ay -v, I get these errors:

ERROR: sil: zero sectors on /dev/sdc
ERROR: sil: setting up RAID device /dev/sdc
ERROR: sil: zero sectors on /dev/sdd
ERROR: sil: setting up RAID device /dev/sdd
ERROR: sil: zero sectors on /dev/sde
ERROR: sil: setting up RAID device /dev/sde
ERROR: sil: zero sectors on /dev/sdf
ERROR: sil: setting up RAID device /dev/sdf

any ideas how I can resolve this?

---

### Post by jose.home on 2005-09-16
Regarding the subject...

I installed Mandriva 2006 Beta in existing RAID0 as described before,
without any problem!!

Just insert CD and that's all!

Ubuntu guys should investigate about this procedure....

FYI

---

### Post by Stoned on 2005-09-20
[QUOTE=shakey]Sorry for dragging this thread up, but it seemed appropriate

I followed the how-to given at the start of this thread, and all went well. almost.
I can see my raid array in GParted fine and correct, but when i try to run the "activateraid" scrip i get this:

 

But it does exist! I've seen it!

Help? Please?[/QUOTE]

Don't copy exactly the line in the first post
```
mount -t <fs type> -o users,owner,ro,umask=000 **dev/mapper/**<your partiton name> /<your mount dir>
``` 
because there is a little error...
Try
```
mount -t <fs type> -o users,owner,ro,umask=000 **/dev/mapper/**<your partiton name> /<your mount dir>
``` 
with the "/" before dev...

---

### Post by cypher35 on 2005-09-29
Thanks dude!

The only problem i had was the current dmraid package requiring some sortof "selinux" library.  I simply downloaded an earlier release and it worked like a charm.

-cheers

---

### Post by progame on 2005-10-11
[QUOTE=cypher35]Thanks dude!

The only problem i had was the current dmraid package requiring some sortof "selinux" library.  I simply downloaded an earlier release and it worked like a charm.

-cheers[/QUOTE]
i found it.
its name is libselinux1-dev

---

### Post by groovywombat on 2005-10-18
hey
everything seems to work OK but when i run dmraid -ay -v I get 
"gavin@Apollo:~$ sudo dmraid -ay -v
ERROR: hpt37x: wrong # of devices in RAID set "hpt37x_eccadiicdi" [1/2] on /dev/hde
ERROR: removing inconsistent RAID set "hpt37x_eccadiicdi"
No Software RAID sets"

So i run 
"gavin@Apollo:~$ sudo dmraid -r
/dev/hde: hpt37x, "hpt37x_eccadiicdi", stripe, ok, 156355520 sectors, data@ 0"

So I guess it's just not seeing /dev/hdf, which is there but in fdisk- l 
"Disk /dev/hde: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       19465   156352581    7  HPFS/NTFS

Disk /dev/hdf: 80.0 GB, 80054059008 bytes
16 heads, 63 sectors/track, 155114 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdf doesn't contain a valid partition table"

however I wasn't aware hdf needed a valid partition table, It works in windows xp
is this a product of it being NTFS formatted?

any ideas? thanks

---

### Post by vfactor on 2005-10-22
Hi guys,

This is my second attemp to mount my RAID-0 2 SATAS disks on Sil3112 (NF7).  On Hoary version I gave up after a while...

Now I just installed Breezy and managed to get much further but instead of using device mapper from Redhat I used the one from Debian found on this [link]("http://packages.debian.org/unstable/admin/dmraid")

Now in my /dev/mapper/  I see my partition listed....

Now the problem is when I try the command *mount -t <fs type> -o users,owner,ro,umask=000 /dev/mapper/<your partiton name> /<your mount dir>* I get the message already mount or busy....

I don't know where else could be mount...I search around but don't see it no where...

Anyone has an idea ?

Thank you


Edit:  Got it work....I have to mount the 2 others sil_ and not the first one.....Thanx for the tutorial

---

### Post by VR6Pete on 2005-10-30
Cracking guide! helped me no end!

---

### Post by Grafster on 2005-11-12
[QUOTE=dave_blob]
This is *NOT* for people with new, blank hdds. For you it is much easier IMHO to set them up using linux software raid, i believe that there is a howto on this forum already for that. 
[/QUOTE]
Where is this how-to?

searching for "linux software raid" doesn't produce anything that shows a newbie how to plug their ata drive into the raid plug on their motherboard and  get the system to show the hdisk as /dev/sdx or whatever.

(having a superadvanced how-to is nice too of course)

Thanks!

---

### Post by aberry on 2006-03-08
Hi,

First of all many thanks for a great thread, it's been on great use to me.

Secondly I am sorry to bump it again but I am still having some issues and hoping someone out there can help me.

I have an ASUS motherboard which has an onboard SiI 3512, I have 2 SATA drives which I have striped.  I'm running Windows XP  with 2 NTFS partitions, which show in Windows as a C and D Drive.  I also have some free space in which I want to install Linux.

From lspci I get

0000:01:0d.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

After following the instructions in the post when I ls /dev/mapper I see

casper-cow       control           sil_afaedfbjcfcc2
casper-snapshot  sil_afaedfbjcfcc  sil_afaedfbjcfcc5

So far so good...

When I try and mount sil_afaedfbjcfcc2 it mounts no problem and I see the contents of the C Drive.

When mounting sil_afaedfbjcfcc5 I would expect to see the D Drive.  I don't, I see the contents of the C drive.  Even when mounting them one at a time.

fdisk -l gives...

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2611    20964825    f  W95 Ext'd (LBA)
/dev/sda2   *        2612       13054    83883397+   7  HPFS/NTFS
/dev/sda5   ?      121635      248474  1018833296   54  OnTrackDM6

Is anyone able to assist me in mounting the contents of my D drive?

Thanks,

Andrew

---

### Post by cprophecy on 2007-02-06
> **dave_blob said:**
> 
5) now everything is installed. You just need to make dmraid  load on startup and set up the drive mounting. 
I didnt make mine load on startup, as i do not need to access my raid drives all that often. So i made a little script to mount them when i need them in my home directory.
Heres how:

You need to find your device name. 
ls /dev/mapper/

There will be a few entries that look long and confusing. They are actually just the partitions of your raid drives, prefixed with a complex name. mine looks like
sil_0309402025011
sil_0309402025011_p1
sil_0309402025011_p5

you need to note these down.


Hi I realize this thread is several years old by now but I just installed ubuntu and am trying to configure my ntfs raid-0 partition and mount it. As the post states it is for a sil3112a controller, which I have as part of my Abit NF7-S motherboard. I have installed the kernel source, downloaded device-mapper.1.02.17 and dmraid1.0.0.rc13 and installed them both, what i think is successfully. As the guide said I skipped step 2 since I am on Ubuntu Edgy 6.10. Until the step i have quoted above it has seemed to all go fine. But when I do 

**ls /dev/mapper**

 it gives me
 **ls: /dev/mapper: No such file or directory**

Could my drive be in some other location?

This is a copy of my fdisk -l
These are the 2 partitions that is my NTFS Raid-0 partition

```
Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       39858   320159353+   7  HPFS/NTFS
```

any help would be greatly appreciated, I think I am very close. Thanks

---

### Post by DJMatty on 2007-03-22
Hi

Have you run '[FONT="Courier New"]dmraid -ay[/FONT]'?

This starts the raid discovery and after this the files have appeared in /dev/mapper for me.

Matt

---

### Post by config on 2007-03-25
Hi everybody!
I have a little problem... May be anybody of you have ever encountered it?
When I type dmraid -ay no nods are created in /dev/mapper/. Verbous mode shows that devices are found:
> 
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sda: nvidia discovering
NOTICE: /dev/sda: nvidia metadata discovered
NOTICE: /dev/sdb: nvidia discovering
NOTICE: /dev/sdb: nvidia metadata discovered
NOTICE: added /dev/sda to RAID set "nvidia_bddgdabd"
NOTICE: added /dev/sdb to RAID set "nvidia_bddgdabd"
WARN: unlocking /var/lock/dmraid/.lock

and something is done with them but nothing really happens.
I've moved from Mandriva to Ubuntu Edgy 6.10 lately. There were no problems in Mandriva and here I simply don't know what's wrong. Searched all over the internet but nobody has any solution for this situation...

---

### Post by config on 2007-04-01
Ok. The latest version of dmraid (rc 13), installed from source, that is not yet available in repositories, fixes all this stuff :).

---

### Post by kilgore731 on 2007-06-08
The worst part for me is that I did this once and now I can't figure out the problem.  

I've got a sata raid I'm trying to mount in feisty.  dmraid is installed and I have the two drives, pdc_ghfaeeaj and pdc_ghfaeeaj1, showing up in /dev/mapper.  What I can't remember is how to mount them. 

these are the disks...
```
Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       77826   625137313+  42  SFS

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdf doesn't contain a valid partition table

```

Any pointers would be appreciated.

---

### Post by JPMATRIX on 2007-11-24
So I tried 

sudo dmraid -ay

Gave me this:

RAID set "nvidia_ecaaibca" already active
RAID set "nvidia_ecaaibca1" already active
RAID set "nvidia_ecaaibca5" already active
RAID set "nvidia_ecaaibca6" already active
RAID set "nvidia_ecaaibca7" already active

I have a raid 0 with 2 250Gb hard drives in nvidia_ecaaibca and nvidia_ecaaibca1 (presumably this is port 0 and 1) 

So the code in activateraid file shuld be like this:

```
dmraid -ay -v
mount -t ntfs -o users,owner,ro,umask=000/dev/mapper/nvidia_ecaaibca /mnt/windows
mount -t ntfs -o users,owner,ro,umask=000/dev/mapper/nvidia_ecaaibca1 /mnt/windows
```

Is this right?

---

