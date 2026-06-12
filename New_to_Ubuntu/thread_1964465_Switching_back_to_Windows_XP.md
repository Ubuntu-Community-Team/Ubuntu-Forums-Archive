---
title: "Switching back to Windows XP"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by starrillos on 2012-04-24
I recently switched my laptop over to ubuntu OS for a "clean slate." However i have just found my Windows XP disk and would like to make the switch back. I start by putting in the disk, F12 for boot menu, boot from CD-ROM, after that it pulls up a linux repair menu and not an OS install guide...

My question: What do i need to do to completely remove ubuntu 11.10 from my laptop and reinstall XP.

---

### Post by scheuri on 2012-04-24
Hi there

Not much there is to do.
You have to make sure that the CD ROM drive is being used as boot drive before the hard disk and then insert a bootable CD (such as a Windows XP CD).

If that works then you should receive a message shortly after rebooting if you want to start windows that is on the cd (by pressing enter or so). If you do not do that, it will start linux again.

once you started windows you need to delete all the partitions first and recreate them (using preferably NTFS). Then you install Windows XP.

ATTENTION:
You will lose all your data...BACKUP YOUR DATA beforehand!!!!!

cheers
scheuri

---

### Post by 3rdalbum on 2012-04-24
Windows XP is really really old, so there may be an extra step involved. XP's installer cannot recognise SATA hard disks and may BSoD if you don't have any IDE hard disks. If this happens, you need to go into your BIOS and set the SATA mode to "legacy" or "compatibility". The SATA drives will pretend to be IDE drives. Once you've installed the SATA driver, you can switch off this special mode to get faster speeds.

---

### Post by zdeuyo on 2012-04-24
> **starrillos said:**
> I recently switched my laptop over to ubuntu OS for a "clean slate." However i have just found my Windows XP disk and would like to make the switch back. I start by putting in the disk, F12 for boot menu, boot from CD-ROM, after that it pulls up a linux repair menu and not an OS install guide...

My question: What do i need to do to completely remove ubuntu 11.10 from my laptop and reinstall XP.

Hello,

You can also use DBAN

Link: [http://www.dban.org/]("http://www.dban.org/")

This will 'nuke' aka erase everything off the Harddrive, HDD.

Once this is done if this does not solve the issue you can use gparted off the Ubuntu Live CD or Gparted bootable to create the new partition that will run Windows XP.

Please let us know how this goes.

---

### Post by ruols on 2012-04-25
I think it also have to be a clean version of XP - not a recovery disk, because you'll then get an error after the install

---

### Post by catlover2 on 2012-04-25
Make sure that you unplug any USB storage from your computer before booting from the XP install disk; the installer has caused me a lot of frustration because of USB drives.

---

### Post by anewguy on 2012-04-25
If it's your recovery disk for your PC and when you installed Ubuntu and partitioned the hard disk you didn't wipe out a recovery partition (if there was one), a recovery disk should be ok.

Right now I think you need to get rid of the Ubuntu partitions in order for XP to install.  XP is going to want the first partition on the disk.  So, I would:

- boot using the ubuntu LiveCD
- select Try Ubuntu and wait for it to boot
- open a terminal window and type:

sudo swapoff

- close the terminal window
- start the disk utility
- remove any ubuntu partitions on the disk. If there is a small partition labeled as Recovery, System, or something similar don't delete it - only the ubuntu partitions.
- shutdown the livecd
- when prompted, remove the livecd, put your Windows XP disk in the drive and close it
- press enter -> the system will reboot and should bring up your Windows XP install instructions

Dave ;)

---

### Post by NikTh on 2012-04-25
I have nothing to add on your suggestions - solutions . I just want to say that 
You are all **admirable**. Freedom here , with all meaning. 

You guide a person to switch back to a fully restricted O.S , for many people 'enemy' of Ubuntu and Open Source ... i didn't expect that. Sorry i am new to this Forum. 
Bravo  =D>

---

### Post by Bartender on 2012-04-25
The XP install CD won't recognize the ext3 or ext4 formatted HDD, so it gives up.

You've gotta do as some of the previous posts mentioned and wipe the Linux partitions off, but the next step would be formatting the entire drive as one primary ntfs partition.

If it were me I'd use a [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php").

Then try again with the XP disc.  It should go once it sees a primary ntfs partition.

---

### Post by anewguy on 2012-04-25
Bartender: I *think* it will go without the formatting - it's like buying a new disk drive and installing it - you just install the OS.  I'd be curious to see how that goes.  I didn't recommend any other disks at this time as the OP says the computer doesn't boot to anything right now - but it didn't dawn on me that if they are making posts here they must have access to something that works ;)

OP: Let us know how that goes and if you have any more questions.


NikTh:  I think you'll find the ranks of vocal Ubuntu "bigots" has quieted down some.  People know that anyone should use whatever works best for them - doesn't matter if it's Linux, Windows, Mac OS "x", or a new OS brought in by the visitors from Jupiter last night ;)  Some of us like Linux, and in particular Ubuntu, for what it is, others for what it represents (free OS, great support on these forums, open source software, and yes those who want to free themselves for whatever reason from another OS).  But it's not for everyone, and many of us don't preach that it is.  I'm glad to try to get someone back to the OS of their choice if it means they can use their PC again in a way that works best for them.

Dave ;)

---

### Post by corrytonapple on 2012-04-25
So what you should do is this:
Boot up from an Ubuntu Live USB/CD just like you did when you installed, and when it asks what you want to do, you want to try it out.
Then, go ahead and open up gparted.  **ALL OF YOUR DATA MUST BE BACKED UP, AFTER THIS OPERATION, ITS GONE!**.  Nobody wants to try the risk of getting it back, so make sure it is backed up.  Backing up to two different areas is better.
Anyway, select your Ubuntu partition, then delete it.  Then right click the swap partition, then click "swapoff".  Then delete it.  You may have a recovery partition, but I don't think XP does that.  Make your harddisk nothing but unallocated space.  Now go ahead and make a new partition the size of the whole drive.  Format it as NTFS.
AGAIN, MAKE SURE YOUR DATA IS BACKED UP.
Now, click the checkmark.  When it is done, and it can take a while, you can shutdown.  But before you do, put in the first XP install disk.  Go into your BIOS, and change your SATA controllers to go into legacy or classic mode.  Then have your computer boot off of the CD drive.  Install XP as the installer shows

---

### Post by S2UIRR3L on 2012-04-26
I had a similar problem... The computer started as XP. I got my hands on it and used DBAN to make sure the hard drive was clean. I checked it for bad sectors and it returned as passed 100% with no bad sectors. I installed 8.10 and everything went smooth.

When it came time to sell the computer (because I bought a better one), I didn't think I needed to wipe the hard drive clean because I had nothing personal on it (was using an external for all that stuff). Tried to re-install XP and it didn't want to start. I didn't try using gparted because I was such a newbie.

I just went back to DBAN, nuked everything and tried the XP disc again and it worked. How ever, the only thing that 'may' be different in my situation is that my hard drive was an older IDE drive, not a SATA. So if the OP wants to make sure that everything is totally wiped from the disk, I'd try DBAN as mentioned a few posts ago.

I'm sure DBAN works for SATA drives (my laptop is SATA). The only time I've seen DBAN fail was when trying to erase Vista or 7, regardless if it's a 32-bit or 64-bit system. In the case of erasing Vista or 7 from a drive, there's another program that I use (it's not exactly open source, so I won't mention names) but I'm sure there's a few open source programs out there.

Best of luck!

---

### Post by anewguy on 2012-04-26
Hence my how-to post. Please read the thread before posting - all the info the OP needs is already here.

---

### Post by corrytonapple on 2012-04-26
Hence his post in this thread.
I believe he was giving a personal experience.

---

### Post by Bartender on 2012-04-26
> **anewguy said:**
> I *think* it will go without the formatting - it's like buying a new disk drive and installing it - you just install the OS.

Yeah, I kinda jumped over some of the posts.  I was thinking about trying to install XP to a Linux HDD.  I know that doesn't work.  But a drive that's unallocated is different.  I think. :)

Anyway, pre-formatted to primary ntfs is your best bet, but probly not necessary.

---

### Post by kio_http on 2012-04-26
Instead of doing that, I would suggest trying variants like Kubuntu 12.04 and then perhaps setting up a dual boot with xp. You know that you can have both side by side right?

---

