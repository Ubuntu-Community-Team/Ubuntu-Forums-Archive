---
title: "Help pls. New computer broken after ubuntu"
date: 2017-12-14
forum: New to Ubuntu
---

### Post by johnny5isalive on 2017-12-14
I just bought a new laptop yesterday for a multi purpose. 

The laptop came with windows 10 which i will be using for work and leisure.  

I also wanted a separate SSD with linux on it for more secure online trading.   I was leaning towards Debian, but all sources steered me to Ubuntu since I'm a linux beginner.  

I checked out some online guides on how to accomplish my goal and this is the route I took:
First I created a live usb stick for ubuntu using Rufus.   Then installed that copy onto my External SSD, but made it a full install with a "persistence" partition.  

The initial install off the SSD failed and I had to start over.    No clue why and I didn't do anything new the second time but it worked.  

Next, I tested it out.  Ubuntu "seems" to be working well (keep in mind that I'm new and this is the first time seeing it), check.   Then I restart to check out my windows....which brings me to a boot option window. I selected windows and booted up successfully, check.  Now, heres where it goes sideways. 

 I remove the SSD to test the computer and see if it boots to windows automatically when nothing is plugged up.  Once I remove the SSD I restart the computer, it takes me to some grub bash error.   I am then locked in this grub purgatory with no escape.  I am forced to hard shutdown.   I turn it back on and it goes straight to grub purgatory again...hard shutdown

So I plug back in the SSD and magically I'm back at the boot options, where both windows and ubuntu work fine.    I decide I need to change the boot order so that if no usb is plugged in, the computer will boot straight to windows.   Once I finally make it to the Bios and open the boot order page, I discover that there is no option for hardrive or windows.   Just 3 different versions of a usb boot and one network boot.  

After 17 hours of frustration I gave up and got some sleep.  Is there a simple fix for this grub issue?   Can I get windows back in the boot order? Remember I'm at the level of a 3 year old with this computer stuff, I only got as far as I did by following different guides from Google; so please keep any answers simplified.   I'd  prefer it booted to Ubuntu if the SSD is plugged in but it needs to boot to Windows if nothing is plugged in. 

Thanks for any help.

---

### Post by alanthelinuxguy on 2017-12-14
When you installed Linux, you probably didn't pay any attention to where the bootloader was to be installed and the default was probably the SSD.  If this is the case, and the SSD isn't always going to be present, the bootloader (which gives you the options to boot into either Linux or Windows) needs to be on the regular hard drive.  See: [https://askubuntu.com/questions/198939/system-doesnt-boot-when-ubuntu-is-installed-on-an-ssd](https://askubuntu.com/questions/198939/system-doesnt-boot-when-ubuntu-is-installed-on-an-ssd)

---

### Post by jaweewo on 2017-12-14
Your problem is this, windows boots up using MBR ( Master Boot Record) and linux uses Grub2 so, when you install linux your "Boot Menu" changes to Grub2 and you have something like:


GRUB OPTIONS
Ubuntu
Memory test
Windows loader in /dev/sdb

if you want to solve this you need to reinstall MBR in your windows installation. And when you do this don't plug the SSD. 

I think that will solve your problem. Hope it helps.

---

### Post by Impavidus on 2017-12-14
Instead of guessing what went wrong, let's first get some actual data. Boot Ubuntu and try boot-repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Don't run the repair yet, but create a BootInfo summary and post the link here.

---

### Post by johnny5isalive on 2017-12-14
Ok so I had to plug in the SSD to get past the grub and into the cmd prompt repair page.  I used this guide: [https://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records](https://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records)

I then unplugged the SSD used all the cmd repair commands in the guide.  

No dice. No fix.  Sadface.

---

### Post by johnny5isalive on 2017-12-14
Where do I get boot repair?    I logged on to ubuntu. I typed it in the the search bar of the "ubuntu software AppStore" or whatever that thos is...orange briefcase with "A" on it. 

It just searches indefinitely and doesn't find boot repair or anything else

---

### Post by coffeecat on 2017-12-14
> **johnny5isalive said:**
> Where do I get boot repair?   

Impavidus has already given you that information in post #4.

---

### Post by leunam12 on 2017-12-14
On the terminal you have to type:```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```press enter and then enter again when it asks you to confirm. Then```
sudo apt update
sudo apt install boot-repair
```

---

### Post by johnny5isalive on 2017-12-14
thanks  

here is the info... [http://paste.ubuntu.com/26183401/](http://paste.ubuntu.com/26183401/)

---

### Post by QIII on 2017-12-14
> **johnny5isalive said:**
> Ok so I had to plug in the SSD to get past the grub and into the cmd prompt repair page.  I used this guide: [https://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records](https://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records)

I then unplugged the SSD used all the cmd repair commands in the guide.  

No dice. No fix.  Sadface.

I hope you have not now put your machine in an indeterminate state.  It is usually not a good idea for beginners to go out to the web, find a random source and follow some random instructions.

Impavidus asked you to go to a specific place (note that it contains the word ubuntu -- the tool was written by a member of the Ubuntu Forums) and use a tool to get some information -- but not to use the repair tools yet.

If you buck the advice being offered to you here, it becomes less likely that we can help.  Please do as Impavidus asked rather than charging off into the darkness on your own.  We are here to help and we are pretty good at it.

---

### Post by johnny5isalive on 2017-12-14
I used leunams post to get the boot repair.  Have not run it yet. Just did the info paste bin that impavidus wanted.   I linked it in my previous post. Awaiting instructions.

---

### Post by Impavidus on 2017-12-14
Ubuntu is installed on sda2, which is on the external ssd, and Windows is installed on nvme0n1p3, which is on the internal drive. I'm not so familiar with nvme drives, but I don't think that really matters. Both systems have installed their boot loader on nvme0n1p1, which is the EFI partition on the internal drive. The Ubuntu boot loader, grub, can boot both Ubuntu and Windows, but needs data files stored on sda2, so it only works when the external drive is plugged in. The Windows boot loader should be able to boot Windows. You should be able to access the UEFI menu of your computer and change to the Windows boot loader. That should enable you to boot Windows when the external drive is not plugged in. Switch back to grub when you have the external ssd plugged in and you want to boot Ubuntu.

Your setup isn't ideal. If you have Ubuntu on an external drive, it's best to have its boot loader on that external drive too. That way, you can directly boot Windows whenever the external drive isn't plugged in. When the external drive is plugged in and has boot priority, you would get the grub menu, even when the internal drive is broken. And you would be able to simply plug the external drive in a different computer (provided proprietary drivers match/aren't used) to boot your Ubuntu system on that computer.

I've got no experience in changing your setup to match that, but I think there are forum users who know what to do.

---

### Post by johnny5isalive on 2017-12-14
Yes that's what I need.  And that way I can run that SSD on any computer too. 

 When I ran the installer from the live USB to install the full ubuntu OS on the SSD, it did not give me the option to set up or manipulate the boot loader that I can recall.  

Should I reinstall windows and wipe the SSD and reinstall ubuntu to get it all configured correctly?

---

### Post by oldfred on 2017-12-14
UEFI only boots from the ESP - efi system partition (FAT32) on the external drive and from /EFI/Boot/bootx64.efi.
Standard install of Ubuntu to any drive in UEFI mode only installs to internal drive seen as sda and in /EFI/ubuntu.
If you did not partition in advance you probably do not even have an ESP on the external drive.

If you have created an ESP on your external, boot live installer as standard Ubuntu fstab mounts the ESP hidden and copy /EFI/ubuntu twice to ESP on flash drive.
Second copy should be to /EFI/Boot folder and then rename shimx64.efi to bootx64.efi. The standard install version of grub that you are renaming expects more files in /EFI/ubuntu, so both copies or both folders are required on external drives with full installs.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 


 Manually copy efi files to efi partition on flash drive for booting. Toshiba Satellite S855-5378  by ubfan1
[http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515](http://ubuntuforums.org/showthread.php?t=2107873&p=12599515#post12599515)
On the Ubuntu filessystem, you should have the signed versions of the following: /usr/lib/shm/shim.efi.signed, /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed. 
Copy them all onto the USB stick .../EFI/ubuntu directory without the ".signed" extension. 
Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi. 
Also copy the grubx64.efi to the EFI/Boot/grubx64.efi. 
There should be the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg
[http://askubuntu.com/questions/738132/ubuntu-14-04-doesnt-boot-grub-prompt](http://askubuntu.com/questions/738132/ubuntu-14-04-doesnt-boot-grub-prompt) 




[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by johnny5isalive on 2017-12-14
Oldfred thnx for the info.   It's almost like I'm reading another language though.   Any chance you can msg me your number and walk me through it over the phone?   If everything works how I want it to I will vinmo you $40

---

### Post by Rocky_Bennett on 2017-12-14
It seems to me that the very easy fix would be to wipe the external SSD clean then shut off the computer. Then unplug the internal hard drive with Windows 10 and then re-install Ubuntu on the external SSD. Then shut off the computer and plug in the hard drive with Windows 10 on it.

This works every time.

---

### Post by johnny5isalive on 2017-12-14
I wouldn't know where to begin disassembling this tiny laptop to pull out the internal hard drive

---

### Post by oldfred on 2017-12-14
We can walk you thru it, but if you did not partition in advance, you first need to redo SSD with new partitions and have an ESP - efi system partition as first partition. It must be FAT32 with boot flag to make it the ESP.

Then use Something Else install option and choose the ext4 partition you created for / (root) as / and ext4. If separate /home you also choose it, but DO NOT check the format button, so your data is not erased. Always have good backups anyway.

Once we get correct partitions and full install, then we can move files around.
Links above go over details of partitioning in advance.

Do you also want a shared NTFS data partition on external drive for some Windows data? If so, you can create that in advance, but do not directly use it during install.

---

### Post by johnny5isalive on 2017-12-15
Oldfred last night i spoke with my stepdather whos a computer guy sort of and he said to start over.   So I reinstalled windows which is working great.   

But now i need to bring the ssd back to it's normal state.   The grub for the linux/ssd somehow got loaded on windows and it cannot load itself...doesn't even show up in bios or under my files of windows when I plug it in.  

So step one.. how do i wipe and format my ssd?

Step two will be installing a full unbutu on the SSD to where it has its own grub boot cabability. 

Just fyi this is the guide I used before to try and accomplish the mission which led to my computer errors. [https://youtu.be/glFCEauwGgw](https://youtu.be/glFCEauwGgw)

He did have me partition but I don't know if that was just for persistence or what. 

Thanks

---

### Post by leunam12 on 2017-12-15
The partitions on your ssd are ext4 filesystem and they cannot be seen by Windows, you have to boot from live USB stick and use gparted to format ssd and create partitions. You can also choose "Something else" at the installer and create your partitions there as suggested by oldfred on post #18. Your partition table has to be GPT.

---

### Post by johnny5isalive on 2017-12-15
I would like to use the something else option with an installer since I am a little familiar with it.   If I use this route am I able to accomplish my goal and do everything that old Fred was saying? Or do I have to modify the SSD before I use the installer? 

What would making NTFS data partition on external drive for some Windows data do for me?

 I don't want any grub or Linux stuff saved on my windows drive. I want to Linux to be isolated in fully self-supporting on the SSD

---

### Post by oldfred on 2017-12-15
Did you reinstall Windows in UEFI boot mode or the 35 year old BIOS boot mode?
How you boot install media, UEFI or BIOS is then how it installs.
Windows on boots with UEFI from gpt partitioned drives and only boots in BIOS mode from MBR(msdos) partitioned drives.

So this can show which way Windows is installed. gpt or dos on Windows drive.
sudo parted -l

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

The reason for a shared NTFS might be if you use both systems a lot. While I was converting from XP years ago, I put my Firefox &  Thunderbird profiles in the shared NTFS, so I had same bookmarks & links and same email.
Otherwise not required.

I have several larger flash drives. I also put a full install in somewhat smaller partitions and use rest for backup data from my systems.
```
Disk /dev/sdc: 61.9GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  211MB   210MB   fat32        ESP        boot, esp
 2      211MB   213MB   2097kB               bios_grub
 3      213MB   22.9GB  22.6GB  ext4         system
 4      22.9GB  61.9GB  39.1GB  ext4         data

```

After install but before rebooting, I copy the /EFI/ubuntu from my internal drive to my flash drive twice and rename shim to be bootx64.efi. And edit fstab with external drive's ESP's UUID.
First time I did an external drive install it overwrote my /EFI/ubuntu folder as all Ubuntu installs use same /EFI/ubuntu folder. Quickly learned to backup /EFI (ESP).

---

### Post by johnny5isalive on 2017-12-15
Old fred i think it was the UEFI mode where i did the reinstall.  It was a blue more modern looking screen than the bios.  It said HP RECOVERY MANAGER at the top and i used the SYSTEM RECOVERY option.  I would link a picture but im not sure how to do that in my phone (at work).  Also, I do not think i want the NTFS to be shared.   I don't want any links between the windows computer and linux ssd. 

I also took pics of how that guys guide had me partition the drive with the installer last time(which didnt work).  I cant load pics so i will describe. 

First partition was 
8000 MB
Logical
End of this space
Use as swap area

Second partition was
112037 MB (which is strange cause ssd is 500g, and this was supposed to be all the remaining space besides first partition)
Primary 
Beginning of this space
Use as Ext4 journaling file system

---

### Post by oldfred on 2017-12-15
If you have a logical partition, then you have the old BIOS/MBR configuration.
Post this:
sudo parted -l

New systems are UEFI, but for backwards compatibility have CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Windows requires vendors since Windows 8 was released 5 years ago to only use UEFI.
But users can install in UEFI or BIOS boot mode, depending on how install media is booted.

---

### Post by johnny5isalive on 2017-12-15
I don't think im able to access the SSD anymore since I reinstalled windows (which had the linux grub boot on it) in order to test that sudo-1 command. 

Thats why I was leaning towards the using a live boot usb and reinstalling Ubuntu on the SSD

---

### Post by oldfred on 2017-12-15
You can run this from live installer, just check which drive is which.
sudo parted -l

---

### Post by johnny5isalive on 2017-12-15
So i type sudo parted -1 in the terminal of my live usb stick?

---

### Post by oldfred on 2017-12-15
Yes, but its lower case L like -el, not -one or dash i.
You can just copy & paste from here:
```
sudo parted -l
```

---

### Post by johnny5isalive on 2017-12-16
It appears i am unable to boot to ubuntu.   Whatever loading grub Ubuntu needed that got loaded onto my windows drive was wiped out when I reinstalled windows.   I tried to get to it from bios but when i select ubuntu it says unable to boot from device

---

### Post by oldfred on 2017-12-16
You boot using UEFI menu and it should show USB live installer with two entries for a standard Ubuntu live flashdrive.  You should one UEFI:flash and the other flash where flash is name or label of flash drive.

Then in live mode not installer, you can go to terminal and run commands.

---

