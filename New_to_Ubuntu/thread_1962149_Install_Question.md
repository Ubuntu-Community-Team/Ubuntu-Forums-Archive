---
title: "Install Question"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by languy99 on 2012-04-20
Hello all first time user of Ubuntu and I want to do this right. This is what I have in my system. I have 3 hard drives. One 650GB that is totally for windows 7 64 bit. Another 60GB SSD that is used as a caching drive for windows because I have the intel z68 chipset so I can use the intel rapid storage program in windows to speed it up. Lastly I have a 1.3 TB hard drive that has like 900GB partitioned as windows and 200GB not partitioned to anything. What I want to do is to install Ubuntu in the unpartioned 200GB and have a prompt when I boot up to choose to run windows or ubuntu. I found a tutorial [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs") case 3 that will be like I want to do this but I want to check with people who know better then me to make sure I get this working right.

---

### Post by Rex Bouwense on 2012-04-20
You are on the right track.  Do you have a problem or question?

---

### Post by languy99 on 2012-04-20
Just want to make sure everything will go ok.

This is my plan; 

burn ubuntu to CD.

Disconnect the ssd and windows hard drive

boot from cd and isntall onto free partition on other hard drive. 

What I am stuck at is what to do next. Do I just follow what that link tell me to do or should I do something else?

---

### Post by Nick_Kats on 2012-04-20
Well I believe that If you follow the steps in that link everything will go just fine :)
In case a problem occurs, you can always post it here ;)

---

### Post by oldfred on 2012-04-20
Some parts of link are old as they refer to grub legacy. Ubuntu has used grub2 as the standard since 9.10 or Oct 2009.

Some other links to multiple drives. If not disconnected you have to use manual install or Something Else to get the option on which drive's MBR to install grub2's boot loader to. If disconnecting you should not have to worry as the drive will be seen as sda and grub just defaults to sda.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by audiomick on 2012-04-20
I agree with Oldfred: doing the partitioning before the install has it's advantages, and having a separate /home partition does too.

I don't bother unplugging drives to be on the safe side. I reckon it is better to stare at it all long enough to know where you are at. If your do your partitioning ahead of the install, then it should not be that hard.

During the install, choose the "something else" option, and then all you need to take care of is that you really look at what you are seeing on the screen. It is not that hard to understand if you take your time about it. The good thing is, it doesn't do anything permanent until you tell it to. There is a point at which you have to confirm a "do you really want to...". Up to this point, you can bail out and start again from scratch if you are not sure.

---

### Post by languy99 on 2012-04-21
well I got it installed. Everything is ok now. I can boot into both windows and ubuntu. It was actually simpler then I would have thought. Just getting used to everything.  

One thing, what would you recommend I use for programs that don't run in linux and have to emulate, wine or something else?

---

### Post by Rex Bouwense on 2012-04-21
Most Widows programs do have a Linux alternative.  If perchance you are using one that does not have a Linux equivalent, it probably will work in Wine.  There are a few exceptions.  Which ones are you talking about?
Since you are dual booting with Windows, it is probably a moot point anyway.

---

### Post by audiomick on 2012-04-21
> **languy99 said:**
>  don't run in linux and have to emulate, wine or something else?
Glad you got things sorted.

The question "wine or virtual machine or native" is not that simple. I would like to be able to never leave my machines in control of windows, but I have to use several program which I, for very solid technical reason, neither in Wine nor in a Virtual Machine am willing to try. The reasons have to do with latency and with connections via firewire and network. It is all just a bit too complicated.

For your purposes, it is really a matter of deciding case by case. As has already been mentioned, if you are going to maintain a dual boot, it is a moot point. If you are wanting to work towards a "Linux is always in charge" situation, then it is a matter of trying out the programs that are an issue in Wine and then in a Virtual Machine to find the best solution.

---

### Post by d4m1r on 2012-04-21
Just for other people looking to install Ubuntu along similar lines:

1) OP has the general idea correct but
2) You don't have to physically disconnect any drives
3) Make sure the space is totally unpartitioned (unallocated) in Windows
4) Just specify that space for Ubuntu to use it it first format it into EXT4 format and then install itself

You then can choose which OS you would like to boot to every time you turn on the PC ;)

---

### Post by languy99 on 2012-04-21
for anyone interested this is what I did. 

I have three drives

Drive1 = 64GB SSD used as a caching drive for windows

Drive2 = 640GB Windows 7 64bit totally partitioned for windows. 

Drive3 = 1.3TB storage drive totally partitioned for windows.

First inside windows I took D3 and shrunk the partition by 200GB. 

Then I burned Ubuntu 12.04 to a cd. Shut down the PC.

Opened the PC and disconnected the SSD and D2. Booted from the CD.

When I went for the install Ubuntu asked me if I wanted to install alongside windows, I suspect it did this because there was a NTFS partition already on the drive. 

Went along with the install. Once done I rebooted and made sure I could boot into Ubuntu. 

Once I knew I should could do that, I shut down and reconnected all of the drives. 

Booted into BIOS and set D3 as the first boot. That way GRUB was the first to boot. 

When you boot GRB comes up, Linux is first in the list and at the bottom there are two Windows listed, as drive sdb1 and sbc1. I just boot from drive sdb1 and can get into windows 7 just fine.

---

### Post by 3rdalbum on 2012-04-22
It's better not to disconnect the other drives (for anyone else who may be looking at this later). When you disconnect the other drives, that makes the one remaining drive listed as the FIRST one, and the GRUB installer won't be able to see the other drives that you want to boot from (like your Windows one) so won't add them to the bootloader.

When you reconnect the other drives, there's the possibility that one of the other drives will become the FIRST one, and GRUB won't be able to find the instance of itself on the first drive.

Sometimes it all works out okay, sometimes not. There's no reason to disconnect the drives anyway if you've got your head screwed on and make sure you don't select the wrong drive to install to :-)

---

### Post by languy99 on 2012-04-22
I think why it worked on mine is because the drive that I installed on already had a ntfs partition on it and it looked just like a windows partition. I also had a Windows 7 virtual machine stored on that drive. Who knows which ones worked but something let ubuntu know that there was windows 7 installed.

---

### Post by oldfred on 2012-04-22
If you do disconnect drives, you need to make sure you reinstall the Windows one to the same location - SATA port number (vital for XP & better for newer versions of Windows).

Since Ubuntu changed to using UUIDs, drive order is not critical to Ubuntu, but you may have to use BIOS or one time boot key to change boot order to use drive's MBR you installed grub2's boot loader into. I always suggest with multiple drives, installing a system's boot loader to the same drive as your system so if one drive fails the other should boot. Both Windows & Linux.

If you disconnect, your install of Ubuntu will not find the other systems. You can easily refresh that with this.
```

sudo update-grub
```

---

