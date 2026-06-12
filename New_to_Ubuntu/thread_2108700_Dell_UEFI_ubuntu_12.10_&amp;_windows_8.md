---
title: "Dell UEFI ubuntu 12.10 &amp; windows 8"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by ShaunShaun on 2013-01-25
Hi - I got the same problem. I've spent the last 3 days trying to get Ubuntu to work without success. I have a Vostro Dell machine which is UEFI and uses GPT (I believe since I have 5+ primary partitions).
I have run Ubuntu from a live USB and it looks good. I have used EasyBCD to add the Ubuntu to the Graphical Windows OS choice on startup, however when I boot up Ubuntu I get /NST/AuoNeGrub0.mbr  missing or contains errors. I'm not sure this is the right approach anyway since I think the machine is GPT anyway. Installed Boot-Repair but says EFI detected, check options. Sure enough it wants to install the boot onto the "wrong" ext4 partition, so following instructions, I have not run Boot-Repair without getting advice. Can anyone help? Boot-Info at [http://paste.ubuntu.com/1568931](http://paste.ubuntu.com/1568931).  Windows 8 boots up fine.

There is a lot of poor advice out there on the web. Please help.

---

### Post by oldfred on 2013-01-25
Moved to your own thread as issues are different.

Your Windows is UEFI and you hve gpt.

But you installed Ubuntu in BIOS mode which will work with gpt in BIOS mode and adds a bios_grub partition. But you cannot dual boot easily. You may be able to boot Ubuntu if you had installed grub2's boot loader to the gpt protective MBR. But you would have to go into UEFI/BIOS and totally change from UEFI to BIOS to boot Ubuntu or change back to UEFI to boot Windows.

If you install Ubuntu in UEFI mode, you then can set UEFI default to ubuntu/grub and from grub menu boot Ubuntu or Windows. You then do not need bios-grub sda10 partition.

How you boot install media liveDVD or Flash is how it installs. But Boot-Repair can also convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi, but you also need to boot that with UEFI on, secure boot off, and fast boot off in the UEFI configuration.

Dell's do work (eventually) :)
       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by ShaunShaun on 2013-01-25
Hi

I reinstalled Ubuntu while BIOS was set to UEFI and now Ubuntu boots fine. Grub OS chooser shows Ubuntu but not W8. F12 shows UEFI:ubuntu but nothing else.

Ran Boot-repair twice but no change in behaviour.

new reference: paste.ubuntu.com/1570229

What to I need to do to get W8 back?

Shaun

---

### Post by oldfred on 2013-01-25
You should see several Linux in the UEFI menu.

Grub as a bug and finds BIOS entries still, not UEFI entries. Boot-Repair will add new efi entires to your grub menu in 25_custom to chain back to the Windows efi entry.  But any from os-prober will not work. Not sure if it will had efi chain entries to your other installs or not, but you can always manually add them. Style is similar for boot stanza. Bug report has Windows example.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ShaunShaun on 2013-01-31
Sorry for the delay getting back to you. I thought that I blown Windows away as I could see the GRUB menu but Windows wouldn't boot. I had to wait for the Dell Windows disk - anyway started all over again and got the same behaviour. This time the script auto-detected Windows 8 so I did not have to manually add them to the GRUB menu. I also ran boot-repair in the hope that this might solve the problem but it did not.

I would really appreciate more specific advice rather than links to a long discussion - I  just want to install Ubuntu, not learn everything there is to know about boot sequences and the like. I have already spent near a week trying to do this. The boot-info is at [http://paste.ubuntu.com/1592668](http://paste.ubuntu.com/1592668)

---

### Post by ShaunShaun on 2013-01-31
I've noticed that after installing Ubuntu, /dev/sda1 has mount point /boot/efi.

It didn't look like that when Windows 8 was installed on its own. 

It seems almost as if the Ubuntu installer just clobbers Windows 8. Is there any way to find out if this is the case?

---

### Post by ShaunShaun on 2013-01-31
OK - to test whether or not W8 was still there I reinstalled W8. This time the W8 installation talked about accessing Windows.old etc, and left disk partitions alone. Last time I reinstalled it destroyed the existing disk partitions.
Unfortunately I can no longer boot from the USB stick I has the 64-bit Ubuntu on (I updated the BIOS settings). Strange and worrying development. Just can't get into Ubuntu. Help would be appreciated.

---

### Post by oldfred on 2013-01-31
Did you turn fast boot off?

Some computers can only get into UEFI/BIOS with Windows if fast boot is on.

Windows normally has two more partitions in UEFI and one they say is required. The first is usually the Windows Recovery or just the repair console. And in UEFI just before the main Windows install has to be Microsoft Reserved partition. Where are those?

In Ubuntu did you choose erase entire disk option when installing? Not the side by side. 
Actually best to shrink Windows with Windows disk managment and then install Ubuntu into the unallocated space.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by ShaunShaun on 2013-01-31
Fast boot might be the cause of the non-boot from USB stick. Will try that now. (EDIT: Yes - I had forgotten to switch fast-boot off, but switching it off makes no difference)
 
I choose "Other option" when installing, which is usually the recommendation on most of the webpages I have seen. The problem is that I have not made any real progress in the last week. 
 
**I really need to get some specific help**. I have spent ages going through links. For example, should the first partition /dev/sda1 have mount point /boot/efi? Is this a sign of an problem? If you don't know, please say so.
 
I shrank the partition via Windows, created separate partition for swap (10GB), root (10Gb, ext4), /home (the rest > 200GB, ext4). That's seems to be the recommendation. I installed Ubuntu and installed it into the 10Gb ext4 partition. (I have tried other variation).
 
Ubuntu then works fine, every time.
 
The last couple of times, boot-repair has detected the windows install, added the menu item, but nothing happens if it is selected.
 
I have created an (additional) 25_windows.uefi file in /etc/grub.d as per the links. The added windows menu then appears, but again nothing happens when selected.
 
I have used boot-repair as well in various configuration with no success. 
 
I shall review the suggested links yet again....

---

### Post by ShaunShaun on 2013-01-31
Thanks for the links, but they seem very techie. I'm at a loss re what to do with them. The Windows partitions are as per Windows installation. I have not attempted to change them except to shrink them to make room for Ubuntu.
 
I don't think the problem is the Windows partition (I could be wrong) since W8 has always booted OK when installed first. It seems to be down at the GRUB2 level and I am totally lost with respect to what I should be doing there.  I have gone through most of the permutations I can think of and got nowhere.

---

### Post by oldfred on 2013-01-31
If you go into the UEFI menu and choose Windows does it boot? That is totally separate from the grub entry, but the grub entry in 25_custom is really just chain loading back to the same efi Windows entry that a direct boot from UEFI is.

I still do not think Windows is installed correctly. Is your recovery from Dell a full system recovery or just Windows? You also are missing the vendor recovery partition in addition to Microsoft recovery/repair and Microsoft reserved. 

If you go back to your original pastebin, you will see your original partition structure. efi was first sda1, then vendor Diags,  Windows recovery, sda3 - reserved  is not shown in this list as it is not formated, and Windows main partition. Then you added the Linux partitions. 

This is numerical sort order so sda10 is not near beginning of drive.
```
/dev/sda1        94DF-0E75                              vfat       ESP
/dev/sda10       510b0954-2b52-4541-9aa4-c313e96ca6a1   ext4       Bios Boot
/dev/sda2        5E35-8653                              vfat       DIAGS
/dev/sda4        624E36E34E36AFA1                       ntfs       WINRETOOLS
/dev/sda5        12163A92163A76B7                       ntfs       OS
 
```

---

### Post by ShaunShaun on 2013-02-01
Found the cause of the problem re not booting from USB. I had allowed Windows to "reset" my machine and it had formated the partitions I had setup for Ubuntu as NTFS. I cannot see why, but I returned them to unallocated and was able to boot from USB. Don't understand.

---

### Post by sudodus on 2013-02-01
Do you have a USB 3 port? Would it be an acceptable work-around to boot Ubuntu from a USB 3 pendrive, HDD or SSD? (It should be rather fast, and that way it need not interfere with Windows). I guess you would prefer an installed system, not only a [persistent] live system, and this is possible (to install Ubuntu into a USB drive and run it like a normal installed system).

---

### Post by oldfred on 2013-02-01
This users just documented his Dell install.

       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

---

### Post by ShaunShaun on 2013-02-05
Hi
Thanks for the post but I've already tried what worked for the other Dell user. It did not work for me. Just to  be sure I followed his steps AGAIN and it failed. 

I'm stuck with a boot-up menu with Ubuntu and Windows 8 entries. Ubuntu works, Windows 8 does not and displays the error message "error: no server is specified". 

<RANT>
It is possible that I made a mistake along the way. But I have to say that I am dismayed at the amount of trouble I'm having installing Ubuntu. I loathe Windows 8 with a passion and I know lots of people who do too. What a brilliant marketing opportunity for Linux and Ubuntu. But no, Ubuntu, the most popular Linux distro refuses to dual boot easily on Dells (the most popular PC vendors?). There is not even a definite installation guide.
I have told a number of friends and acquaintances that I was going to try Ubuntu. What am I going to say? To suggest it is a replacement for W8 is laughable, if you can't get it to even install.  If there is anyone out there from Canonical, get your act together. 
</RANT>

In the absent of specific help, I've given up on installing Ubuntu directly onto my PC and will try installing onto a USB stick. Are there any issues. E.g. installation of software (I would like to install a C++ and Java development environment). I presume these will not be installed under /home so what in the best way to do this? Also, are there any permissions problems re mounted partitions? Would it be better to boot from a CD?

---

### Post by squakie on 2013-02-05
If you want to be able to add software and have it remembered from one boot to the next, then you'll need USB and persistence.  Using a tool like unetbootln you can build the usb stick and set the amount to be used for persistence.  I would suggest using a USb stick larger than 10gb to start out.  You may need to actually use a larger one later, but considering your experience and experience level, start simple.  Try things out.  Don't get in a hurry to load all kinds of things until you know what is going on.

And another suggestion:  I don't have Win 8 yet, so I can't say if it's there for Win 8 or not, but I would run Windows 8 and install something like VirtualBox.  Using VirtualBox you can define 1 or more virtual machines - I would put ubuntu in one of those.  Do take the time to read up on virtual box and it's usage prior to just jumping off the deep end.  You'll need to be aware of the VirtualBox extras, when to install them, how networking works (setting the virtual machine network to NAT let's the virtual machine use the host's adapter), how USB works, etc..  If you don't do some of the reading, or don't  read it with the mindset of "I can take my time and try to understand this",  then perhaps you are not ready for Ubuntu yet.  It's not difficult unless you make it so.  It can work, but you have to do your home work just like school if you want to succeed.

---

### Post by sudodus on 2013-02-05
> **ShaunShaun said:**
> ...

In the absent of specific help, I've given up on installing Ubuntu directly onto my PC and will try installing onto a USB stick. Are there any issues. E.g. installation of software (I would like to install a C++ and Java development environment). I presume these will not be installed under /home so what in the best way to do this? Also, are there any permissions problems re mounted partitions? Would it be better to boot from a CD?

With USB 3 or eSATA you get fast and nice booting from an external drive. The most convenient is maybe a USB 3 pendrive. But it works well with standard USB 2 as well, but slower.

Since you want to install a lot, and maybe also upgrade the kernel, I suggest that you make a standard installation (but to the external drive instead of the internal drive). This way you will get a complete Ubuntu system :-)

---

### Post by oldfred on 2013-02-05
I thought you totally overwrote your Windows install and the recovery partitions with a second install of Ubuntu using the choice overwrite entire drive? And you were gong to erase drive and do a new Windows install from Vendor's DVD?

You can use persistence but if a larger flash drive a full install is possible also.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
but with UEFI it will be a bit different to install. Not many have installed a UEFI bootable flash dirve but it should be like any install to a second drive. But you MUST use Something else to get to choose where to install grub. And with UEFI, you will want it on the efi partition on the flash drive.

       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by squakie on 2013-02-05
> **oldfred said:**
> I thought you totally overwrote your Windows install and the recovery partitions with a second install of Ubuntu using the choice overwrite entire drive? And you were gong to erase drive and do a new Windows install from Vendor's DVD?

You can use persistence but if a larger flash drive a full install is possible also.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
but with UEFI it will be a bit different to install. Not many have installed a UEFI bootable flash dirve but it should be like any install to a second drive. But you MUST use Something else to get to choose where to install grub. And with UEFI, you will want it on the efi partition on the flash drive.

       UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

I've got to remember that and keep following this thread.  I'm getting a new Dell laptop that should be in here in 2 to 3 weeks and of course it has Windows 8.  I want to give it a chance, but I also want to try running ubuntu on it as I hope to use it as my desktop replacement to cut down on space being used by computer "junk".  My desktop actually has more horsepower than I really require (a sad problem to be sure, but none the less.....).  Do you know if Virtual Box will run in Windows 8?  I'm hoping so and hoping that perhaps I can put my Ubuntu there until I decide to go dual boot on the laptop - at which time I'll be back myself asking questions!

---

### Post by ShaunShaun on 2013-02-09
I gave up trying to install Ubuntu on the main hard disk and bought a USB hard disk for £45, changed it to GPT and installed Ubuntu onto that. The 64 bit version seemed to worked first time but after that Ubuntu couldn't see the USB drive in GParted or anything else. Could see it in W8, so changed to it back to MBT and installed 32 bit Ubuntu onto the USB drive. That boots up fine but 
 
(1) need to change BIOS everytime I change OS (liveable)
(2) W8 needs repairing after running Ubuntu. Why? This makes no sense to me.
(3) I unplug the USB drive when using Ubuntu -although this doesn't seem to be a requirement.
 
I think this is as good as its going to get. At least I can save work in Ubuntu and get back into W8 for other things. But on the whole not a good advertisement for Ubuntu.

---

### Post by oldfred on 2013-02-09
It sounds like you boot Windows in UEFI mode and Ubuntu in BIOS mode, so you have to switch in BIOS. The 32 bit version does not even have a UEFI install option. With Ubuntu you can have gpt partitioning and still boot in BIOS mode. Windows only boots from gpt with UEFI.

Is the Windows hibernation part of the issue, or the changing from UEFI to BIOS causing an issue somehow?

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

