---
title: "External USB Hard Drive setup Prior to Install"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by Starserpher on 2012-01-15
I am completely new to linux, no experience what so ever but have been researching about it for a couple of months. I am generally inexperienced with any aspect of modifying most of my computer and disks.
 
So, I have a laptop with Windows 7 64 bit. I have an external USB desktop hard drive, 1TB. I want to keep the laptop hard drive as is, be able to boot Ubuntu from the external, but still have space to store on the external for Windows. 
 
Please advise the best method to implement this. Should I format the partitions with window prior to Ubuntu install?
 
For the install of Ubuntu there is disconnecting the internal drive or another method utilizing &#8220;grub&#8221;. I am unsure as to the best method. I am inexperienced with BIOS, so once Ubuntu is installed is it as simple as hitting the right key on startup to boot BIOS, then select the drive to boot?
 
 
Thanks for your input and your tolerance of a complete noob.

---

### Post by Double.J on 2012-01-15
Hi there! Welcome to the forums!

I think you're pretty much there really, yes to leave the hard drive as is, the best way is to install ubuntu and it's bootloader (grub) on the external drive and choose between then at a BIOS prompt - you may have one time boot options with a key such as F12?

Tere's no need to edit the external from in windows - ubuntu comes with a partition editor called Gparted that's much better equipped. The main thing to do is back up your external drive if you have any data currently on it? Just bare in mind that if you  messed up the install you may write over it?

I'd agree that removing your laptop's internal hard drive is probably the safest way to go to guarantee you don't do anything at all to it. 

When you run the Ubuntu installer, click on try, then gparted from the desktop. Your external drive probably comes with one ntfs partition - if so right click and shrink from the left to the right so that you leave around 30GB at the start - this is more than enough to install ubuntu, packages and still move large files such as DVD iso's on and off it. Leave this as free space.

Run the installer and choose use free space - the installer will then do all the leg work for you. You may have read about the benefits of setting up a separate home, but in this instance I don't think it's necessary, it'd be more logical to access your personal data from the NTFS partition on the rest of the drive.

Once the installer finishes choosing to boot from the usb device should bring up the bootloader and then boot ubuntu. 

You may want to Update the grub bootloader, so that if you choose to boot to ubuntu, but wanted to go to windows, you can go back? Open a terminal (ctrl+alt+t) and paste in:
```

sudo update-grub

``` 

Hope it helps! Enjoy ubuntu!

---

### Post by Cheesemill on 2012-01-15
If you want to set up an NTFS partition for use with Winows then make sure it is the first partition..

Windows will only recognise the first partition on a USB device.

---

### Post by Starserpher on 2012-01-16
Thanks for your input. I have run into a bit of hurdle. I have tried 32 and 64 bit 11.10 iso put onto a DVD-R. I have tried BIOS SATA set to PCI and the other option. And booted by changing boot order to dvd drive first, and removed internal(Windows) hard drive.
 
When I restart and it boots, passes the purplish/pinkish screen with the rectangle and man in the circle. It will then go to black screen with a bunch of what i assume is a set of start up lines. all start with "[ 8.xxxx......." the numbers don't matter much, but they are sequential. The last line includes "*something *terminated at 9 (killed)" I tried many combinations from above and all ended the same way, sometimes made it to 10.xxxx lines.
 
Any advice on this situation?
Also, is 64 bit hardware compatible with 32 bit OS? I would prefer 32 bit as I am assuming that it has more developed drivers.
 
Thanks.
 
[EDIT]: I did discover if I pressed [enter] on the pinkish screen with the rectangle and man in a circle screen, it would go to language selection and then UBUNTU with several options: try, install, ..., other. But when selecting try Ubuntu, it would fail out as above.

---

### Post by Mark Phelps on 2012-01-16
Don't know HOW you but Ubuntu 11.10 onto a DVD-R, as it's actually a CD-sized image, but I would recommend that you put it onto a CD instead.  I suspect what you're experiencing may be a problem with the SW on the DVD.

You could also try putting the installer onto a USB stick.  Would recommend going to PendriveLinux.com and using their latest Universal USB Installer to do that.

Haven't used GParted in a while, so don't remember if it will let you shrink a partition from the LEFT.  If it does, then that will work OK. If it doesn't, you can download the free Partition Wizard, install that to Win7 -- and use that to shrink the NTFS partition on your external drive from the left.

And, I agree that disconnecting the internal drive is the safest way to ensure that GRUB isn't accidentally written to your Win7 drive.

---

### Post by Cheesemill on 2012-01-16
> **Mark Phelps said:**
> Don't know HOW you but Ubuntu 11.10 onto a DVD-R, as it's actually a CD-sized image, but I would recommend that you put it onto a CD instead.  I suspect what you're experiencing may be a problem with the SW on the DVD.

I don't think this is a problem. I often use DVD's when I have run out of CD's and I've never had a problem with any distro or ISO image that I've done this with.

---

### Post by oldfred on 2012-01-16
Sometimes you need an extra boot parameter or two, especially for video.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some examples of installing to a second drive. The important part is to use manual install/partitioning, so you get the combo box on which drive's MBR to install grub2's boot loader to:

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Starserpher on 2012-01-17
Currenly at work so I won't be able to make any progress untill later, but thanks for the responses and I will see what progress I can make.
 
I did have one question.  Does the SATA setup in BIOS matter for install?  I thought I read that it had to be IDE, but this weekend, I had forgotten to switch it back when I reconnected my internall after a Ubuntu install attempt.  Before I knew what had happened, windows failed to boot and asked if I wanted to repair.  I did,  I thought I had lost everything, and it failed to repair.  After a several paniced minutes and numerous restarts, I remembered that I had changed the SATA option in BIOS.  Windows booted, but was not where it was the last time I saw it, and there were no restore points so I was still in panic mode.  I had to restart and reorder boot order to boot from my repair disk.  Sucessful repair, and my restore points were back, and finally my internal hard drive was back minus my recent install of Minecraft.  Lost my recent world stat, but small loss concidering what could have been. 
 
Is the SATA required to be IDE for Install?
Is the SATA required to be IDE after install, or will I have to change it to boot Ubuntu, and remember to change it back so my wife doesn't mess up the internal hard drive again?
 
Thanks everyone.

---

### Post by oldfred on 2012-01-17
If you have AHCI, it is better to use that, but Windows 7 needs a fix first and with XP it is a major change (best to do as part of an install as I understand it). I just converted from standard SATA LBA to AHCI for a new SSD. My XP stopped working, but no real loss. On the very rare occassion I may boot it, I will just change back.

Quotes from others:

It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

HOWTO: enable AHCI mode after installing Windows 
However, in the real world the performance difference isn't huge.
[http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)

---

### Post by Fernhill Linux Project on 2012-01-17
I have written a couple of simple articles for new users on bios and installing ubuntu to USB drives. Have a look on our site for details, you may find it useful : [http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html](http://fernhilllinuxproject.com/guidesandhowtos/installubuntutousbdrive.html)

The two most important things are:

Ensure that you are installing to the correct drive.
Ensure that the boot loader is installed to the correct drive.

If you have only one internal drive, and unplug any other external devices, then install from CD/DVD you will only have 2 drives, and sdb will be the usb drive.

Note to MODERATORS - Is it okay to post links to my guides? 
I considered copying and pasting the info, but it seemed easier to link. Please let me know if this is not okay.

---

### Post by oldfred on 2012-01-18
As long as link is relevant to issue, I do not see any reason why you cannot link (se #10 in policy). I have seen some users complain about links (or links to links) versus comments, so I usually try to answer some or most of question and provide links to several sites with further info.

But if link is to a site selling Uggs boots (which we seem to get daily) or other unrelated product, it is spam and we erase post and ban user.
please see the forum policy: 
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Just a comment on your instructions. Many users get confused with install to USB flash drive. You can do installer version with or without persistence, and those can be in small flash drives. A full install now needs over 4GB so you will need a 8GB flash to do a full install.

A few systems promote an external device to sda, users then get very confused on which drive is which and usually install to the wrong device. Best to check first.

---

### Post by Starserpher on 2012-01-18
Thanks everyone, but I'm still failing.
 
set up: 1 week old laptop, internal drive with windows 7 64 bit. new empty 1TB external usb 3.0/2.0 hard drive partitioned using windows 750/250 GB. intend to put Ubuntu on the 250 partition.
 
My current experience. Ubuntu 11.10 32bit
 
remove internal drive
boot to CD.
see screen with rectangle and man in circle at the bottom
 
a) If I let it run it goes to black with white text and eventually freezes for at least 5 minutes so I reboot and retry.
 
b) If I hit [enter] I can select a language and then I see Ubuntu 11.10 with 4 options: try Ubuntu, install, check disk, something else and several F-key options like help, mode, other options, ect.
 
1) when I select try and hit [enter], ends similar to (a) above
2) I have tried check disk, Finds no errors, gives option to press any key to reboot
3) I have tried install, ends similar as (a) above. 
 
 
Is the 3.0 HD the problem, I am only using a 2.0 port?
Do I need to install something else other than the disk created form
[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download?")
 
All I know is it is no where as smooth as the videos I look up and they never show the black screen with white text.
 
Thanks.

---

### Post by C.S.Cameron on 2012-01-19
Confirm the MD5SUM of your downloaded iso.

---

### Post by Starserpher on 2012-01-20
Ok I finally have some success.  I got a hold of an old high school bud that I know was into Linux back then.

Fist we tried one stick of RAM, then swapped for the other with the same results which he said rules that out.  Then I made a liveUSB(out of dvd/cds) and got the ISO for 10.04.  Finally I can see Ubuntu desktop.

He also suggested searching make-model+Ubuntu.  I have searched Acer Aspire Ubuntu before but all I got were issues with their Netbooks.  Last night I searched Acer Aspire 5742G Ubuntu, where some one said that 11.10 needed one of the other options(F6) in the boot menu, disable acpi.

I can now get 10.01 and 11.10 to the same point where I can start the install, but I have no wireless, and it doesn't seem to see that I have an external hooked up.

**Wireless**: Is it best to go with wired for install and then find a driver or should it already find it?

**External**: Back to my original post before attempting install.  Currently split 750/250 GB/GB partitions of NTFS.  I intend to put Ubuntu on the 250(someone mentioned earlier that Windows can only use the first), and I wanted the larger storage area for windows, and just wanted to play around with Ubuntu.  Do I need to format the partition first?  Everything seems to point that this is done in setup.

1TB USB3/2 Seagate GoFlex with its own power supply.

Thanks

---

### Post by oldfred on 2012-01-20
The liveCD includes almost every driver needed for wired connections to Internet, but there seem to be so many wireless versions than you often have to use the wired to download a wireless connection. Install works better with Internet connection.

You really do not need 250GB for Ubuntu. And with large drives it is better to keep a smaller / (root) partition. There used to be a bug in Grub that with very large / partitions, there were boot issues.

If you use the NTFS partition as your data partition you do not need much space.

I normally install to a 25GB / (root) and include /home in / as I do store all data in a NTFS /mnt/shared and a ext3 (I would use ext4 now) /mnt/data partitions. The advantage of a separate /home is if you want to reinstall your user settings and data can be reused without backup (backups still required). That makes a new clean install easier. But with new large drives another / partition of 25GB is easy to allocate and you can easily backup/copy the user settings to the new install.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Starserpher on 2012-01-22
Thank you everyone who helped out.  I have completed my install on my external hard drive.  The biggest issue I had at the end is Ubuntu detecting my hard drive.  I found that with the USB 3.0/2.0 cable, it is able to be inserted slightly farther into my laptop port than a normal 2.0 cable/flash drive.  By slightly pulling out the cable until I heard the hard drive spin up I was able to see my hard drive partitions.

Thanks again everyone, I shall now begin my journey into Linux.

---

