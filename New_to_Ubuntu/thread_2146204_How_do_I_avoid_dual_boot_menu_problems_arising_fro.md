---
title: "How do I avoid dual boot menu problems arising from Ubuntu/Windows updates?"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by shaunthesheep on 2013-05-17
I have just installed 12.04 LTS via Wubi duel booting with Windows 7 64 bit. Everyting is working well (knock on wood). But I have been here before. Some years ago, I set up a duel boot with an earlier version of Ubuntu with Windows XP. It also worked well for quite a time. Then a Windows update changed the appearance of the duel  boot menu but everything continued to work OK. Subsequently, an Ubuntu update screwed up the duel boot menu so I couldn't get into either OS. Panic, panic! It took me a day or so to get back into Windows (cannot recall  exactly what I did) but I never did get back into Ubuntu. I recall trying to use Supergrub to repair things without success.

I am far from being a geek, in the sense of being a technology expert, and when things go haywire like this I am very definitely technologically challenged.

What can I do to be better prepared for such an eventuality in the future? 

I am Beta testing Lightworks for Linux--that is why I installed Ubuntu. I will transfer completely to Ubuntu when a stable release of Lightworks for Linux is released. I am also Beta testing Lightworks for Windows and don't want to desert the testing programme just yet. 

I am tempted to temporarily turn off all updates for Windows and Ubuntu but I know that unpatched OSs become vulnerable. 

What is the best tool to have ready to resolve duel boot problems?

Another possibility would be to disconnect my video editing desktop PC from the Internet completely and use another PC for access to the Web. That is what many professional video editors do--they never let their editing machine anywhere near the Internet. They may become unpatched but if they are not connected to the Internet their vulnerabilities cannot be exploited. I may do this when my budget allows but at the moment i am stuck with one machine.

Any advice appreciated.

---

### Post by oldfred on 2013-05-17
Wubi does not work with the new UEFI systems with gpt partitioning. It has been discontinued with the newest versions of Ubuntu. Although some others are maintaining some use.
 Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

      
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Wubi is not a full install of Ubuntu. It is intended as a longer term test for those who are not sure they want Ubuntu and do not want to re-partition. It is just a file inside Windows and uses the Windows boot loader.

 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

As with all systems good backups are important. You can backup root.disk as that is your entire Ubuntu install as a file in Windows. And wubi adds entries to the BCD so you can review those entries or make backups of those to be able to reset the BCD.
With full installs and I assume wubi, you really only need to back up /home as that is your data and user settings. If editing system settings then something in /etc may need to be backed up also. The rest is system. If you install a lot of apps you can make a list to make it easier to reinstall.

---

### Post by William D. on 2013-05-17
This is what I did to overcome that same problem.    THREE Seperate Hard Drives.  No partitions.  No Boot Loader.
Connected the first hard drive and booted off of the CD and installed Windows 8. Disconnected that Hard Drive and connected the Second HD. Installed Windows 7. Disconnected that HD and connected 
a Third HD and Installed Ubutnu.  
Then went back and connected all three Hard Drives.  Now when I turn on the Computer I press the F12 Key and from the menu select which HD to Boot off of.  IF I don't press anything Windows 8 Boots up.
The Primary HD can be set in the BIOS.

---

### Post by shaunthesheep on 2013-05-17
Many thanks for prompt replies. 

My 3 year old Dell Inspiron 560 MT uses BIOS not UEFI--which I, of course, want to avoid like the plague. Is there any thing I should be aware of in terms of accidentally "upgrading" to UEFI? At the moment, Lightworks for Linux public Beta is officially supported on 12.04 LTS but not on subsequent versions--although people are testing it on later versions. So no immediate worries about upgrades. And Lightworks for Linux works brilliantly by the way. The speed of the launch is almost instantaneous. Still lots of limitations and known issues but it is getting there. Need more testers. Total users just passed 500,000!

I am coming round to the idea that I need to ditch Windows. It is a privacy/surveillance nightmare (backdoors)--that is actually my main concern. What would be the best way to transfer to a permanent installation of Ubuntu when the time is right? Nuke my C drive with Eraser and then install the DVD version of Ubuntu?

---

### Post by oldfred on 2013-05-17
If your system is BIOS, it wiil not update to UEFI. But if you have just installed with BIOS mode and your system is only a year or two old it may be UEFI.
Apple switched to UEFI when it changed to Intel chips. Most motherboard with newer i-series Intel chips have UEFI with a BIOS mode. Most Vendors still installed Windows in BIOS mode. Users did not notice as Windows 7 DVD install was always BIOS, you had to convert it to flash to use UEFI. 
But now Ubuntu will install either way.

I still recommend dual booting, but you have to partition. And William D. way is the best if you have another hard drive. We find many users who like Ubuntu and overwrite Windows. But then they find one game or application they cannot live without that is Windows only. 

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by shaunthesheep on 2013-05-18
I used Wubi to install on a second partition--on my E drive. The Windows drive is the C partition. Both partitions are on the same internal physical HDD. I will get a second internal HDD and reinstall Ubuntu on it using William D's suggestions. 

Would I need to reinstall Windows 7 or could I leave it as it is? 

How do you NOT install the boot loader?

---

### Post by oldfred on 2013-05-18
You can and should leave Windows alone. After you get new install working and have copied any data you want you can delete wubi from Windows. Leave the extra NTFS partition to use as  a shared data partition.
You want the Windows boot loader on the Windows drive and grub2's boot loader on the Ubuntu drive.

Some suggest disconnecting Windows drive to install and that would of course prevent any issues.
And any of the auto install options automatically install grub to sda which you do not want. 
So use Something Else or manual install. 
On the partitioning screen at the bottom is a combo box that will default to the hard drive that is sda, change it to sdb but not any partition.

 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by shaunthesheep on 2013-05-20
My Dell Inspiron PC 560 MT  is actually almost 3 years old (I've  corrected the OP) so I don't think that UEFI is a problem. I will  install Ubuntu on a new internal HDD shortly. Thanks again for excellent advice and please test Lightworks. It could be a game changer for Linux which has lacked a professional NLE thus far (absolutely no disrespect to the excellent existing video applications intended). 

I hope that EditShare helps launch some kind of non-profit Linux video foundation in cooperation with existing Linux video (and audio) developers when the Lightworks code is open sourced so that cooperation and collaboration is established.

EditShare is a private, non-listed, company founded by media professionals who are not lumbered with shareholders who have no interest or knowledge in the media industry. See their roadmap:

[http://www.lwks.com/index.php?option=com_content&view=article&id=51&Itemid=177](http://www.lwks.com/index.php?option=com_content&view=article&id=51&Itemid=177)

And the latest Windows Beta version of Lightworks (11.1.k), just released on Friday, has a HUGE improvement in long GOP performance (e.g. H.264 in MOV and MP4 containers).  This  means that the enormous community of HDSLR, and many other users who capture to this format, can now edit 1080p AVC footage natively in Lightworks for the first time. No need to transcode. Check it out:

[http://www.lwks.com/index.php?option=com_content&view=article&id=51&Itemid=177](http://www.lwks.com/index.php?option=com_content&view=article&id=51&Itemid=177)

It will appear in the Linux version soon.

---

### Post by shaunthesheep on 2013-06-07
Just wanted to report that I have installed a new 2TB internal HDD (a first for me), installed Ubuntu Studio from the DVD (with the Windows drive disconnected) and all seems to be working very well. I have Windows 7 on one physical HDD and Ubuntu Studio on a second and I choose which one to boot to with F12. Thanks for the excellent advice (and OS).

---

### Post by shaunthesheep on 2013-06-11
I am having some problems with the computer clock appearing an hour slower than local time in Windows. It appears to be correct in Ubuntu. A few days ago, I noticed this problem in Windows and wondered if it was the CMOS battery that was in need of replacement. I replaced it with a new one but the problem remains. I noted down all the BIOS settings before replacing it and restored them afterwards.

One thing I am trying to clarify is should I use UTC time or local time (British Summer Time) in the BIOS? I gather from research on the Web that in a Linux-only set up, UTC is the correct BIOS time to use while in a Windows-only computer local time should used in the BIOS. 

I currently have Windows on one HDD and Ubuntu Studio 12.04 on a separate internal HDD. I am not using a duel-boot loader menu but booting by using the F12 key.  So should I use UTC or local time in the BIOS?

I have the time synched to the Internet in Windows but I can't see how to do this in Ubuntu.

EDIT

Further searching on the Web turned up this [post]("http://forums.opensuse.org/blogs/jdmcdaniel3/what-utc-gmt-time-opensuse-12-3-12-2-116/") from an OpenSuSe site. It recommends the following:

1) For a UTC Setting Do this (recommended for users that don't dual boot with Windows):

     Code:
     ```

su -   echo -e "0.0 0 0.0\n0\nUTC" > /etc/adjtime 
2) For a LOCAL Setting Do this (recommended for users that DO dual boot with Windows):

```
     Code:
     ```

su -   echo -e "0.0 0 0.0\n0\nLOCAL" > /etc/adjtime 
You most likely need to restart openSUSE for a manual edit of this  file to work properly.  It is OK to use Local time no matter your  reason if you wish to.  Since this seems to be an issue with the DVD  installation disk, it will likely remain that way for the entire life of  openSUSE 12.2.  

```
Should I do this in Ubuntu Studio 12.04  too ?

Thank You for using openSUSE!

---

### Post by shaunthesheep on 2013-06-11
After further searching the web on the clock issue, I came across a way of making Windows 7 use UTC BIOS. See [this page]("http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx").

Create a text file and copy the following into it
```

Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation]
"RealTimeIsUniversal"=dword:00000001
```

Save the text file and rename it as utc.reg on your Desktop.

Double click on the reg file and it will make the Windows registry use UTC BIOS time.

EDIT

I had to apply the registry hack twice before it had any effect.

---

### Post by shaunthesheep on 2013-06-11
Here is some [more info]("https://help.ubuntu.com/community/UbuntuTime") about resolving multiple boot time conflicts.

---

