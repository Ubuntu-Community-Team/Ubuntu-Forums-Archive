---
title: "New start with Ubuntu and can't even get an iso disk"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by robert_burns2 on 2015-06-15
Hi Guys

I am a new starter, please be kind.

 I do hope I can get my head around this Ubuntu. I tried it about five years back but, life was simpler then.
Scenario is, I run an all in one desktop (Medion) with Win 7. It has been good for four years, running dual boot 64 bit and 32 bit.
More recently, I bought a new all in one with Win 8.1 installed. This is definitely hair tear out gear and is presently inactive
due to a corrupted BCD boot. (I am the culprit as I was trying to dual boot it with the Win 7). It came without support disks.
Investigations into the upcoming Win 10 revealed my old system cannot handle it so, I thought, why not swap to Ubuntu? It should suit both systems!
Initially I first put a purchased copy of Win 8.1 on a spare hard drive and dual booted it with my Win 7 HDD, with due deference to the MBR/GUID system.
Once running, I switched off the Win 8.1 and cleared a partition on the win 7 HDD to take Ubuntu.The attack on Win 8.1 comes later.

I first read Gary Newells on line advice on Win 7 /Ubuntu Linux Dual Boot guide, then downloaded the 14.04.2 iso image. At least, that is what I thought.
Try as a might, I cannot get an ISO copy onto Disk or flashdrive. The folder appears to be compressed but I am not sure if I should unzip it before copying to 
the boot device. Perhaps the files are only unzipped when the disk or drive boots up? I have tried it both ways. One way says metadata missing thus no ISO.
The other way just does not boot. They leave a lot of garbage around which has to be cleaned out before another try. 
I have tried unzipping into a folder then just copying the folder contents to the drive but that is no better.
I suppose there could be some data corruption in the transfer, or perhaps the triple boot selector in the bios might be a problem?

Bit stuck now, although in signing on here I see there is a check recommended after downloading. I might try that.

Any comments and/or advice would be welcome.

Bob

---

### Post by coffeecat on 2015-06-15
Welcome to the forum.

You appear to be going about burning the ISO to a DVD the wrong way. Do not try to extract anything from or unzip the ISO file.  Here is a link for burning an ISO to DVD using Windows:

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

Another one for creating a bootable Ubuntu flash drive in Windows:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

My guess is that your problem is down to using the wrong method for transferring the ISO to the bootable medium. However, it is a good idea to confirm the integrity of the downloaded ISO file by checking the md5sum. A useful howto for this - scroll down for the method for Windows:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Good luck!

---

### Post by mastablasta on 2015-06-15
after download first check the image for any errors (if you download with torrent this is done during download): [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

you can then burn the image to DVD: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

or you can put it on USB flash drive: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

there are also other programs for creating bootable usb for example my two favourite ones in windows:
Linux LiveUSB Creator: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
Unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You an also easily create multiboot USB disk (for example if you want to try more Linux images - let's say you want to try to run Kubuntu, Xubuntu etc.) with Yumi multiboot: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

enjoy and make sure you try some other flavours of Linux in case they work better on your PC. easy ones for Windows users are KDE based (Kubuntu) but also Mint has nice desktop interface (Cinnamon or Mate). For older PC's you have Xubuntu and Lubuntu. For really old PC's the there is ToriOS or Bodhi Linux. All these are based on Ubuntu. and then you can go after others, such as OpenSUSE for example.

depends what you need and what kind of interface you want.

---

### Post by nerdtron on 2015-06-15
> I first read Gary Newells on line advice on Win 7 /Ubuntu Linux Dual  Boot guide, then downloaded the 14.04.2 iso image. At least, that is  what I thought.
Try as a might, I cannot get an ISO copy onto Disk or flashdrive. The  folder appears to be compressed but I am not sure if I should unzip it  before copying to 
the boot device. Perhaps the files are only unzipped when the disk or  drive boots up? I have tried it both ways. One way says metadata missing  thus no ISO.
The other way just does not boot. They leave a lot of garbage around which has to be cleaned out before another try. 
I have tried unzipping into a folder then just copying the folder contents to the drive but that is no better.
I suppose there could be some data corruption in the transfer, or  perhaps the triple boot selector in the bios might be a problem?

A youtube video can help you with this: [https://www.youtube.com/watch?v=SoTQEfwjP2o](https://www.youtube.com/watch?v=SoTQEfwjP2o)

---

### Post by robert_burns2 on 2015-06-15
Thank you Guys

Your inputs made something click. I have, over four years with this Win 7, never made an ISO disk.

I suddenly thought when looking at your pics, I don't have a 'burn to disc' in my dropdown when I right click,

only a Copy to. Problem was, I had never made Windows Burn to disc the Default! Files and music fine, but ISO no!

I sometimes can get it top of page but rarely. Feel a bit sheepish now.

All fixed now . I will let you know how I go. Thank you!

Bob

---

### Post by robert_burns2 on 2015-06-15
Further input.

The 'Burn to Disc' did appear in my drop down but, in terms of putting an ISO program onto my blank DVD BD-RE, it just took an hour
to repeat what the download was! Still, she no boot!

So, I swapped back to the USB drive, downloaded the universal USB installer and I was in business! I think the DVD option needs a bit more looking at.
I have been in and had a look but not yet installed. Need to be sure about my internet connection and how it might effect my local network.
I can see all my files on my Win 7 system but not sure yet about all the applications. The touch screen might be a problem.
If I put my Missus off line with her iPad, she will not be best pleased.

I feel like I am at the start of a rather long learning curve!

Progress reports and calls for help to follow.


Bob

---

### Post by nerdtron on 2015-06-15
There sure is a learning curve as Linux will do things differently from windows. Just post your questions on the forums and people will voluntarily help in a way they can.

Goodluck and enjoy!

---

### Post by RobGoss on 2015-06-15
There's no better place to start using Ubuntu then here they have some of the best Ubuntu's user's right here on these forums. Ask and you shall receive this might help [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by robert_burns2 on 2015-06-15
Well, today I hit a couple of snags when I tried a true install.
The installer spotted the 20GB partition which holds the Win 8.1 boot, (EFI), although the actual drive, a 1 TB  is powered off.
It then appeared to be setting up to instal alongside this? The nomeclature used for the partitions bears no resemblance to
what I know them as and that, is very confusing. I have 224GB of unallocated space on the Win 7 1TB which already carries
four partitions. Also 232GB unallocated on the win 8.1 1TB which also has four partitions. 
I understand I cannot have more than four partitions per drive. I am getting warned that if I put in a new primary partition,
that will be the only one I can boot from???
I suppose I could do away with the backup partition of the win 8.1, which is extra to the recovery and, if all goes well, I will need none of it.
Identifying each is the hard bit.

Please understand, This particular Win 8.1 is on a 1 TB HDD in an external dock and is entirely experimental, 
I am already aware it is incompatible with my Medion touch screen and DVBT systems of the Win 7 configuration.

The new All in one (ASUS) also has a 1TB with Win 8.1 currently not bootable and ready to return to supplier for a fix.

Once fixed, I hope to convert that to Ubuntu. The drivers may be a problem as many are MS specials.
Let the experiment continue!

Bob

---

### Post by mastablasta on 2015-06-16
the 4 primary partitions limit applies only to MBR partitions (sued in XP, Vista and quite often in windows 7. I am not sure what you are trying to do as you write a lot of unnecessary things in your post. but if you want to add to windows 7 disk, then use mini tool partition wizard  ([http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)) to change one of windows 7 partition into secondary (I.e. extended) then you should be able to install into allocated free space.

 if for some reason it is still not working (which was the case in my install since allocated space was in between the windows partitions), then go for manual partitions.

create root (/) partitions. Mount as / , format as ext4 (this is like C:\ in windows)
create /swap partition (the size of your ram). mount as /swap, format as /swap  (this is kind of like pagefile.sys in windows)

and you should be good to do. you can recognise partitions by size and I think if you have volume named in windows you should also see that name.

some people setup separate /home partition - this is kind of like mydocuments or maybe user in windows. but is not necessary and default.

 /dev/sda = device sata disk a
 /dev/sda1 = ddevice sata disk a, first partition
 /dev/sda2 = ddevice sata disk a, second partition
 /dev/sdb1 = ddevice sata disk b, first partition

 ...

if you don't wan't to mess with win8 disk then unplug it.

---

### Post by robert_burns2 on 2015-06-16
Thanks for the advice Mastablasta. I think you misunderstand my intention but those links to the manual could be handy.

I can confirm that the Windows names of drives bear no relationship to the Ubuntu names. The sizes are close but not identical.

Anyway, I took a punt and loaded Ubuntu, I think on the Win 8.1 drive but as yet have not proved it as I can't find it From the windows drive.

The intention is to replace Win 8.1 on a new ASUS which has been troublesome for weeks, with Ubuntu, mostly due to it asking for  an Other Log On which,

I had never set up and which does not respond to any password. Leaving the machine non operational. I am going cautiously with my existing old Win 7 plus a dock and a 1TB HDD,

 onto which I have loaded a new Win 8.1 in dual boot with my old Win 7, also on a 1 TB internal drive.

This Win 8.1 is not fully compatible with the earlier Win 7 hardware config.  Once I am confident it will

replace the Win 8.1 on the new machine. I will swap my efforts to that but, to achieve that confidence also means ,

I must first learn my way around Ubuntu.

Thus the protracted discussion.

Bob

---

### Post by mastablasta on 2015-06-16
right - you won't be able to see Ubuntu from windows. it will be unformatted disk space. if you want to see where you installed it boot into live OS (test it) and then open gparted to see how the disk is divided.

you can also run boot repair tool's bootinfoscript (bootinfo summary)  and post result here. then we can see how you set it up and tell you how it is setup at the moment. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

if you want to install to 8.1 disk then all you need to take care is that GRUB (the boot loader) is installed on that disk as well.

---

### Post by Mike_Walsh on 2015-06-17
> **robert_burns2 said:**
>  The sizes are close but not identical.

Hi, robert_burns2.

Simple reason for this is that Windows uses Me[COLOR=#ff0000]**ga**[/COLOR]bytes & Gi[COLOR=#ff0000]**ga**[/COLOR]bytes, whereas Ubuntu (and indeed most Linux distros that I've used) use the alternate of Me[COLOR=#0000ff]**bi**[/COLOR]bytes, and Gi[COLOR=#0000ff]**bi**[/COLOR]bytes. Binary, as opposed to decimal. Similar, but not quite the same.

See [here]("https://en.wikipedia.org/wiki/Mebibyte") for explanation. Another little piece of the puzzle for you! All part of that 'learning curve' you mentioned..... :)


Regards,

Mike.

---

### Post by cooleryawner on 2015-06-17
For burning to a disk: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) For burning to a USB: [http://pcsupport.about.com/od/file-folder/fl/burn-iso-usb.htm](http://pcsupport.about.com/od/file-folder/fl/burn-iso-usb.htm)

---

### Post by robert_burns2 on 2015-06-17
Thank you guys, all points taken. I had heard of Grub before and have, accidentally had it searching on this system.

The Binary difference is news to me and appreciated. Would you believe I was a mainframe hardware specialist in the late seventies!

Most industrial process control, 16 bit binary. You carried a 16 word bootstrap in your head back then. Magnetic core store memories were the go.

Haven't times changed! I have Ubuntu up and running but still a few steps before I have the confidence to do a complete swap.

Bob

---

### Post by Mike_Walsh on 2015-06-18
Hi, Bob.

Yes; times **have** changed. I've been messing about with these things ever since leaving school.....probably about the time you were playing around with your mainframes!

Strange to think, isn't it, that what took the same amount of space as the average house to perform complex calculations, can now be carried out by something you can hold in the palm of your hand.....and they're getting smaller by the day.

The info about Mebibytes & Gibibytes was news to me, as little as 6 months ago. Until then I, too, had never heard of them.


Regards,

Mike. ;)

---

