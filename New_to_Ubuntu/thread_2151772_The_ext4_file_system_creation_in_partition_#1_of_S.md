---
title: "The ext4 file system creation in partition #1 of SCSI 1 0,0,0 sda failed"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by FMFCorpsman on 2013-06-05
I loaded 12.04, but have the misfortune of the Logitech bug. I then upgraded to 12.10, same result. When I tried upgrading to 13.04 through the upgrade software within Ubuntu, it froze. I tried to revert back, to no avail. I tried reinstalling 12.04 64 bit from USB again, but this time it gave an error of "the ext4 file system creation in partition #1 of SCSI 1 (0,0,0) (sda) failed. My mouse works intermittently and I don't know enough of Linux to try and fix from the terminal. Any help is appreciated. Also to let you know I included all this info and it still wanted that assinine prefix.

---

### Post by Cvxcvgg on 2013-06-05
I would suggest running GParted and creating a new partition table. Make sure to back up your important files, of course. This is what worked for me with a similar issue, and it's the best I've got, but I emphasize that it may not work for you. Hope this helps.

---

### Post by varunendra on 2013-06-05
Welcome to the forums FMFCorpsman :)

> **Cvxcvgg said:**
> I would suggest running GParted and creating a new partition table. Make sure to back up your important files, of course..

This ^^ should work, but shouldn't be needed. Just to be clearer, creating a new partition table will delete all currently existing partitions on the hard disk and you will have to create fresh partitions on it (or the installer will automatically do it for you). All the data on existing partitions, as Cvxcvgg stated, will obviously be lost.

A simple and in most cases the better variation of the fix is to just choose "Something else" option at the partitioning stage during installation. In the next window, you will be presented with a list of existing partitions. Just choose the one on which 13.04 is currently installed > change > choose to use it as EXT4 filesystem, Mountpoint for /, Format > Save/Ok (or whatever button there is to save and close it) > make sure GRUB (bootloader) is set to be installed on the hard disk (and not the usb drive itself) > proceed.

Let us know if you have any problems in following above, or if it doesn't work.

**PS:**
I saw your other [thread]("http://ubuntuforums.org/showthread.php?t=2151730") about prefix issue. So I know you may have problems posting back command outputs from your iPhone.
Can you use your 12.04 live USB in "Try without installing" mode to connect to internet and post back outputs if required? I sure hope we won't need that though, and you will have your problem solved with above suggestions.

---

### Post by FMFCorpsman on 2013-06-06
I had tried to upgrade to 13.04 through the software upgrade app in 12.10, but it froze. So I attempted to reinstall 12.04. I cleared all partitions, created one for primary, home, and swap. When I initiated install of partitions it gave me error as I described above.

---

### Post by FMFCorpsman on 2013-06-06
Verunendra, unfortunately I have been hit with a double whammy, I also suffer from that Logitech mouse bug, so my control only lasts so long.

---

### Post by Cvxcvgg on 2013-06-06
If you can't recreate the partition table, your drive may be burnt. Do you get an error about "Input/Output Error" by any chance? If so, I think your drive is failing or dead. In that case, there's not much to be done, except to get a new one. If you don't get an I/O error, then I'm sure Verunendra will be more able to counsel you than I am.

---

### Post by FMFCorpsman on 2013-06-06
Is there a way I can post a .jpg of the partition I setup and the error message I get when I inititiate the partition?

---

### Post by Cvxcvgg on 2013-06-06
There is an image button in the "Post Reply" window, it's right next to the hyperlinks (middle row, right side).

---

### Post by FMFCorpsman on 2013-06-06
I am not getting an I/O error, just the one I described above

---

### Post by Cvxcvgg on 2013-06-06
Ok, well I'm not too sure how to help then...Sorry. I'm sure someone will be along soon who does. All I know is what I've experienced, sadly. Good luck!

---

### Post by varunendra on 2013-06-06
> **FMFCorpsman said:**
> I cleared all partitions, created one for primary, home, and swap.
So how many partitions do you currently have?
Did you delete > recreate them or just formatted the previous ones?
Did you try creating a fresh partition table?

> **FMFCorpsman said:**
> Verunendra, unfortunately I have been hit with a double whammy, I also suffer from that Logitech mouse bug, so my control only lasts so long.
Does the mouse not work after a while? Is the rest of the system (keyboard and other OS functions) works after that? We can do without mouse, but it would have been much better if you had a working mouse.

> **FMFCorpsman said:**
> Is there a way I can post a .jpg of the partition I setup and the error message I get when I inititiate the partition?
You can press "PrintScreen" key to take a screenshot, "Enter" to save it in your "Pictures" directory. Then attach it here in your post. Alternatively, you can show us the output of -
```
sudo fdisk -l
```
To limit the above output to only interesting parts, you can filter the above command to -
```
sudo fdisk -l | awk 'NR>8 {print $1,"\t"$6}'
```
Then note down the output and post it here.

---

### Post by FMFCorpsman on 2013-06-06
> **varunendra said:**
> So how many partitions do you currently have?
Did you delete > recreate them or just formatted the previous ones?
Did you try creating a fresh partition table?


Does the mouse not work after a while? Is the rest of the system (keyboard and other OS functions) works after that? We can do without mouse, but it would have been much better if you had a working mouse.


You can press "PrintScreen" key to take a screenshot, "Enter" to save it in your "Pictures" directory. Then attach it here in your post. Alternatively, you can show us the output of -
```
sudo fdisk -l
```
To limit the above output to only interesting parts, you can filter the above command to -
```
sudo fdisk -l | awk 'NR>8 {print $1,"\t"$6}'
```
Then note down the output and post it here.

i can no longer boot Ubuntu from my USB. When I made my partition I made 15 GB for primary and 10 GB for home and 4 GB for swap. When I pressed continue I got the above error message.

---

### Post by FMFCorpsman on 2013-06-06
The only saving grace is that what little money I have, I ordered a Dell Inspiron 3521, with what little money I get from military disability. I retired last from the reserves as a combat medic for 24 years. Here's to government stipends!

---

### Post by FMFCorpsman on 2013-06-06
I'm sorry, in answer to your question I wiped the partition table on each attempt

---

### Post by FMFCorpsman on 2013-06-06
Is there no hope? No sugar coating please lol! Do I have any alternatives?

---

### Post by Cvxcvgg on 2013-06-06
Well, new memory is pretty cheap these days, so there's always that option, given that you are not averse to popping open your computer. Not much else I can think of, but it should work. If you don't want to do that, I'm afraid I'm out of ideas.

---

### Post by FMFCorpsman on 2013-06-06
You don't think it could be the drive itself? I can't even restore the old windows vista restore disk without getting giant red letters that say error.

---

### Post by Cvxcvgg on 2013-06-06
That's what I meant. There's a pretty good chance it is dead, with what you've reported. As I said, it's pretty cheap to get memory these days. Good luck with your computer, I know how irritating memory issues can be. Remember, if possible, back up your important data. :)

---

### Post by varunendra on 2013-06-06
> **FMFCorpsman said:**
> i can no longer boot Ubuntu from my USB.
Is the USB no more bootable or is it that the computer just refuses to boot now?

> **FMFCorpsman said:**
> Is there no hope? No sugar coating please lol! Do I have any alternatives?
Without sugar coating, you may try to physically disconnect the hard drive since that is what we are suspecting the most, then try booting into live mode if the USB is still fine itself. If you can boot normally in this case, at least it means the rest of your system is working. Then there are a few options to 'keep it working', some good, some... umm... 'compromising', to say the least.


**PS:**
I may not get online today (we have a power failure in our area, and laptop battery is almost drained), so please don't mind if I couldn't reply soon. I'm in a rural village, where power failure can mean anything from half a day to a couple of weeks! :(

---

### Post by FMFCorpsman on 2013-06-06
> **varunendra said:**
> Is the USB no more bootable or is it that the computer just refuses to boot now?


Without sugar coating, you may try to physically disconnect the hard drive since that is what we are suspecting the most, then try booting into live mode if the USB is still fine itself. If you can boot normally in this case, at least it means the rest of your system is working. Then there are a few options to 'keep it working', some good, some... umm... 'compromising', to say the least.


**PS:**
I may not get online today (we have a power failure in our area, and laptop battery is almost drained), so please don't mind if I couldn't reply soon. I'm in a rural village, where power failure can mean anything from half a day to a couple of weeks! :(
Verun, this is a new install on a 5 year old Asus laptop. No data has been lost. I removed hdd, to no avail. Install had worked before, but I had to repeat install several times to get the partitions the way I wanted then. I was hampered by the Logitech mouse bug. It is my belief that the files on the USB are corrupt and there is nothing I can do about it. I have no other computer and the windows restore disks fail to load now too.

tashi delek

---

### Post by FMFCorpsman on 2013-06-07
Well I do know after 24 years as a combat medic there are still lessons to be learned. Could you guys/gals give me some advice as to what tools I should have backed up on thumb drives so I have a fighting chance of recovering this fatal meltdown? Ie maybe a bootable thumb drive that has format commands, or the ability to do low level formatting. Until a new laptop comes I have nothing but a ton of useless thumb drives. Thank you for all your helpful responses.

---

### Post by FMFCorpsman on 2013-06-07
Trying to give you a pic of my partition is is tedious at best on my iPhone. Though I am no longer able to get this far into the new install.

---

### Post by FMFCorpsman on 2013-06-07
Sorry guys but your attachment feature on the iPhone is worthless

---

### Post by FMFCorpsman on 2013-06-07
So guys, does that mean i am screwed?  i dont know enough to fix this myself. i have made repeated attempts at attaching the pic, but to no avail.

---

### Post by oldfred on 2013-06-07
Are you using Installer to create partitions or gparted from the live installer. If not using gparted, I would try it. It may still give an error on your partition but may give further clues to issue. gparted has red or yellow icons on errors that you can click (right click?) for more info.

If partition exists but is giving errors then you may be able to run fsck to clear errors.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by FMFCorpsman on 2013-06-08
I tried loading live without hdd, it just hangs on Ubuntu title page. I put hdd back in and ran again. I bought a cheap corded USB mouse Onn optical mouse stock number : ONA11HO091, but the left click didn't work. I load with the USB I originally created with disk creator from the 64 bit 12.04 ISo. I got as far as the screen where it checks the available drive space, Internet connection,. I checked download packages on install and checked to download third party software. When I cursored over to continue, I got a box with the error "Ubi-part man failed with exit code 10. Further information may be found in var/log/syslog. Do you want to try running this step again before continuing? If you do not install may fail entirely or may be broken.

---

### Post by varunendra on 2013-06-08
System freezing on the loading page is no good sign. Was it (the USB) booting fine earlier? If it is corrupt itself, we do need a working system to create a fresh one.

---

### Post by FMFCorpsman on 2013-06-08
Varun, I spent money I don't have and bought a dell Inspiron 3521. It has 8 GB ram, celeron processor, and 320 GB hdd. It also has windows 8. I should be able to pick up at the post office tomorrow morning. I will try recreating a USB with disk creator using a different USB. I would appreciate detailed instructions because everything has been vague until now. If that does not work, then I will put Ubuntu on my new laptop with windows 8 and will need all the help I can get from my new friends!Namaste!Jeff

---

### Post by oldfred on 2013-06-08
Suggest using gparted to see what it says about drive. It may be corrupted partition, left over bits of RAID if drive ever was RAID or left over bits of Windows if you ever converted Windows to dynamic partitions from basic. Or could be a variety of partition issues. Or a failing drive.

Post this.
sudo fdisk -lu

If you decide to add Ubuntu to new computer, it is a bit more difficult. It uses the new UEFI with secure boot turned on per Microsoft specs. Some will boot Windows with secure boot off and then it is not quite so difficult. 
Start a new thread if you start on new computer as those issues are totally different. Also see my signature as the change from BIOS to UEFI is large.

---

### Post by FMFCorpsman on 2013-06-08
Old Fred thanks for the response. Though I am not holding my breath, Dell tells me they will send the actual windows 8 CDs after the fact and just not the restore CDs. Could I just take that Inspiron and take the plunge and partition it put saving a NRA partition for a later windows 8 partition?

---

### Post by oldfred on 2013-06-08
Depending on what install disk they send you may be able to convert install back to well known but 30 year old BIOS/MBR install. But there are some advantages to UEFI and gpt partitioning as it is new and will be the future.

With UEFI there are several required partitions for Windows. One advantage of gpt partitioning is that there is only one type of partition, no primary, extended nor logical partition like MBR(msdos).

         Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by FMFCorpsman on 2013-06-08
Old Fred, I will read those links, but are you suggesting taking that Dell Inspiron 3521 that I should be getting Monday and wiping it for 100% Ubuntu? The other question I have is for $349.99 shipped I am getting a Intel Celeron processor, on board graphics, 4GB RAM, 320 GB HDD, with Windows 8. Do you have any recommendations for upgrades to facilitate some of the development work I will be getting myself involved in? Is it true that I can't upgrade to an i3 or 5 processor,the only thing I can do is increase RAM? Should I leave a partition with windows 8 or commandeer the whole drive for Ubuntu ?Funniest thing happened, I thought my old laptop drive was des, because I had tried everything to get it to boot or format. Just for shots and grins I put in this old cd of XP I had  and low and behold if the thing didn't start booting up asking for partition spaces. Wow ! So any advice you guys can give on another go on getting Ubuntu going would be appreciated.Thank you everyone for your advice! I'm sure it won't be the last lol!

---

### Post by oldfred on 2013-06-08
I would not delete Windows 8. But just understand UEFI with secure boot is a lot different.

Laptops usually have just about everything soldered in. You may be able to add some RAM or change to an SSD if you want speed.

If XP starts to load, then Ubuntu should on old system. But if you have certain drive settings or video issues then it may have touble. Both usually can be worked around. Were you trying to use a 64 bit version on an old 32 bit system or even if really old does it have not have cpu PAE extensions and you used the newer version of Ubuntu that now need PAE. If Pentimum M or older it may not have PAE.  Lubuntu 12.04 32 bit may then work.

---

### Post by FMFCorpsman on 2013-06-09
> **oldfred said:**
> I would not delete Windows 8. But just understand UEFI with secure boot is a lot different.

Laptops usually have just about everything soldered in. You may be able to add some RAM or change to an SSD if you want speed.

If XP starts to load, then Ubuntu should on old system. But if you have certain drive settings or video issues then it may have touble. Both usually can be worked around. Were you trying to use a 64 bit version on an old 32 bit system or even if really old does it have not have cpu PAE extensions and you used the newer version of Ubuntu that now need PAE. If Pentimum M or older it may not have PAE.  Lubuntu 12.04 32 bit may then work.

My Asus has a Centrino 2, and the system settings say its a 64 bit system. My problems didn't start until I decided I wanted another partition when I was upgrading to 13.04. I had already installed 12.04 64 bit, and successfully installed all upgrades and then 12.10 I wonder if the files in my thumb drive got corrupted when 13.04 got hung up and froze during install. I won't be able to fix that until I get the new laptop Monday so I can restart all over again. Though I think I will need help loading Ubuntu on these new fan dangled way they are doing things now according to Old Fred. Fred I can be certain that the Dell Inspiron 3521 is 64 bit if windows 8 is the OS, right? Will I still be able to make primary, home, and swap partitions?

---

### Post by oldfred on 2013-06-09
If you have a new Windows 8 pre-installed it will be 64 bit. Just about every Intel chip in last 6 years or so is 64 bit. Some Atoms are lightweight and may not be. 
Only if you bought a Windows RT system then you cannot install anything else as it is secure boot without any way to turn it off.
With UEFI, you have gpt partitioning. There is only one type of partition in gpt, no extended nor logical. But you are limited to 128 partitions which all in effect are primary.

---

### Post by FMFCorpsman on 2013-06-09
So Fred what your basically saying is that new laptop coming would give more disadvantages if I tried loading Ubuntu. I would be better off fixing this jacked laptop I have for a Linux only system, or put together an old desktop that's in pieces. It has a high end Asus motherboard, two 512MB DDR2 RAM, a Pentium IV 3.2 GHZ CPU and a 350 GB HDD. All I need is a case and power supply. Do you think this desktop could run Ubuntu Server well enough, and leave the others as windows OS's?

---

### Post by oldfred on 2013-06-09
Quite a few have posted installing Ubuntu on new Windows 8 systems. Some are easier than others. The high end UltraBooks have additional issues that are separate but add to the complications. Some brands boot Windows with secure boot off an d those install relatively easily. Those that only boot with secure boot on and/or only boot the Windows efi file need several work arounds to make them work.

With 1GB of RAM you can even run the 64 bit version if your Pentium IV is 64 bit.
       32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

---

### Post by FMFCorpsman on 2013-06-10
> **oldfred said:**
> Quite a few have posted installing Ubuntu on new Windows 8 systems. Some are easier than others. The high end UltraBooks have additional issues that are separate but add to the complications. Some brands boot Windows with secure boot off an d those install relatively easily. Those that only boot with secure boot on and/or only boot the Windows efi file need several work arounds to make them work.

With 1GB of RAM you can even run the 64 bit version if your Pentium IV is 64 bit.
       32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

I got my new laptop today and I have to say Windows 8 has got to be the biggest cluster ever distributed. Whoever came up with this was tweaked on crack laced with LSD! I can barely get my head around it. I want to try to load Ubuntu 12.04 again, but I wonder if I should try the 32 bit version? I should be able to create a primary, home, and swap partition without affecting the existing OS, correct? I have some more reading to do now!

---

### Post by oldfred on 2013-06-10
With UEFI you have to use the 64 bit version as only that has UEFI support.

See link below in my signature. It is not particularly difficult but involved. Backups, repair disks and following the process help make it work for those that have dual booted.

Important to use Windows disk tools to shrink the NTFS partition and reboot to let it run chkdsk. Then you can create partitions easily with gparted or as part of the install. You have to use Something else and with UEFI grub is installed into the existing efi partition.

---

### Post by FMFCorpsman on 2013-06-10
> **oldfred said:**
> With UEFI you have to use the 64 bit version as only that has UEFI support.

See link below in my signature. It is not particularly difficult but involved. Backups, repair disks and following the process help make it work for those that have dual booted.

Important to use Windows disk tools to shrink the NTFS partition and reboot to let it run chkdsk. Then you can create partitions easily with gparted or as part of the install. You have to use Something else and with UEFI grub is installed into the existing efi partition.

Fred, is it a given that I have UEFI because Windows 8 is the OS? How can I confirm that?

---

### Post by oldfred on 2013-06-10
All pre-installed Windows 8 systems use UEFI with secure boot on. You may have to turn secure boot off and must turn the fast boot off or the always hibernated setting. Fast boot is just a way for Windows to say they boot faster but is really just hibernation.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by FMFCorpsman on 2013-06-10
I have been reading, but i want to get this sequence right and get a clarification. Do I need to turn off secure boot, fast boot, and always hibernating setting in my BIOS before I run Boot Repair? Now as far a boot repair is concerned, how can I get that on a Live USB, and is that what I should be doing?

---

### Post by FMFCorpsman on 2013-06-10
Also, on my last attempt at an Ubuntu install i created a live USB with UnetBootin, and I wasn't impressed. Are there better ones out there or should I try that one again?

---

### Post by FMFCorpsman on 2013-06-10
oh I also forgot to mention that I was initially going to use that LiliUSB, but found for some reason that the persistence was offline and couldn't be set. I can't remember the reason they gave.

---

### Post by FMFCorpsman on 2013-06-10
I was able to find and disable the secure boot function, but I could not find anything that remotely looked like fast boot. There was an option called a boot list option and you could change that from UEFI to Legacy, but I left it alone until I heard from you. Thank you for all you advice and responses, the are really appreciated.

Well whudda thunk! I deselected fast start up under personalize in power options! I thought all this was through the BIOS. Now guess I make a live USB for the Boot Repair

---

### Post by FMFCorpsman on 2013-06-11
I have included a print screen of my computer management. Volumes E and F are my 1TB external drive I used for my other laptops backup, hence why I don't need to download another Ubuntu 12.04. I can shrink the primary partition, but where to back it up to? Another idea, I have no recovery CD's for this computer though Dell says they are sending a Windows 8 cd, what about just wiping this clean and giving it 100% to Ubuntu? Will the UEFI still truly be in the way?

---

### Post by varunendra on 2013-06-11
> **FMFCorpsman said:**
> Now as far a boot repair is concerned, how can I get that on a Live USB, and is that what I should be doing?
You can use unetbootin to create a live USB with Boot-Repair iso, or you can install it on an existing Live USB of Ubuntu as per this guide :
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

> **FMFCorpsman said:**
> Also, on my last attempt at an Ubuntu install i created a live USB with UnetBootin, and I wasn't impressed. Are there better ones out there or should I try that one again?
Which one you weren't impressed with? Unetbootin or Ubuntu itself. There are many alternatives to both.

> **FMFCorpsman said:**
> Another idea, I have no recovery CD's for this computer though Dell says they are sending a Windows 8 cd, what about just wiping this clean and giving it 100% to Ubuntu? Will the UEFI still truly be in the way?
Just make sure (looks like you already have) that Secure Boot is turned off, then you should be good to go.
But I wouldn't recommend it until you get the Win8 installation DVD in your hands. Or at least create a "Full-Disk" backup image of your laptop's hard-disk with some imaging software that is compatible with win8 installations. Clonezilla is most popular for that here on the forums, but I don't know if it is reliable for a Win8/UEFI setup.

In any case, I'd suggest to wait for input from oldfred before making any drastic changes to the new laptop.

Oh, and I didn't get an opportunity to reply earlier - "Namaste"! :D

---

### Post by oldfred on 2013-06-11
Some have made suggestions on Windows software that will work for backups. That is included in the entire UEFI overview I posted. See signature for link.

---

### Post by GregA on 2013-06-11
Is it still possible to return, and get credited for the "Win8" laptop from Dell?  IF so, there is a super easy way to level the playing field (with Microsoft or Apple) - buy a laptop with Linux "Pre-Loaded" . . . . 

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

A lot of choices here, although most low end laptops are going to be in the $599 to $799 price range.   

The above info provided to give you some more options, but if you find that by updating the bios (disabling secure boot, and enabling legacy mode)  . . you can still boot into Windows, that's a good sign you can shrink the Win8 partition (using Windows tools only) - and then use a "Parted Magic" live CD to boot up and setup your partitions (ext3 or ext4 and 4gb swap).  From there, it's pretty easy to install Ubuntu (or my preferred distro, Kubuntu 13.04).

[http://distrowatch.com/](http://distrowatch.com/)

Greg
HM3USN
USS Sperry AS12
Jan 1971 - Aug 1972

---

### Post by FMFCorpsman on 2013-06-11
> **oldfred said:**
> Some have made suggestions on Windows software that will work for backups. That is included in the entire UEFI overview I posted. See signature for link.

Fred, I have seen those suggestions, I have read everything I can. The last thing I want to do is come on here and waste peoples times by asking questions that I can find the answer myself. My issue is that, those options aren't necessarily available to me and so I wanted opinions on a different approach.

---

### Post by FMFCorpsman on 2013-06-11
> **GregA said:**
> Is it still possible to return, and get credited for the "Win8" laptop from Dell?  IF so, there is a super easy way to level the playing field (with Microsoft or Apple) - buy a laptop with Linux "Pre-Loaded" . . . . 

[http://linuxpreloaded.com/](http://linuxpreloaded.com/)

A lot of choices here, although most low end laptops are going to be in the $599 to $799 price range.   

The above info provided to give you some more options, but if you find that by updating the bios (disabling secure boot, and enabling legacy mode)  . . you can still boot into Windows, that's a good sign you can shrink the Win8 partition (using Windows tools only) - and then use a "Parted Magic" live CD to boot up and setup your partitions (ext3 or ext4 and 4gb swap).  From there, it's pretty easy to install Ubuntu (or my preferred distro, Kubuntu 13.04).

[http://distrowatch.com/](http://distrowatch.com/)

Greg
HM3USN
USS Sperry AS12
Jan 1971 - Aug 1972

Greg, I did think about getting those Linux systems, but they were too far out of my price range right now. One thing I did just find out though is that my computer will not boot when put in Legacy mode in the boot list option. When I press F12 on restart it comes up with options and under legacy it starts with a boot priority of network, HDD, and CD. You can't change the order. I did see and am beginning to understand whats behind this UEFI, where the boot list for UEFI shows it looks for some sort of windows manager in order to boot from the HDD. When in Legacy, this manager of sorts is not present so it gives me an error stating insert bootable media. I am really leaning towards wiping this drive completely and just running Ubuntu because I am not happy with Windows 8 at all. I just don't know if by reformatting and partitioning the drive I will get rid of that need for a manger to be present to boot up or if Legacy will finally work?

Jeff
HMCS (FMF) (AC) (AW) USN ret.

---

### Post by FMFCorpsman on 2013-06-11
Okay, I have decided what I am going to do. I have an old ATA drive that's 140GB. I am currently taking my archived stuff on that and transferring it to my 1TB WD Passport. Once that's done I will reformat the ATA Drive and use it as the image drive for the Windows 8 on my laptop. Question I have is that this ATA drive is older, will there be unforeseen circumstances when trying to reformat it for the Windows 8 image, or should I be okay?

The other question I had, in another post I added an attachment that showed all the different volumes that were unused. some as small as 40 mb, others as large as 14GB. When I shrink the partition for volume C:, will those be shrunk as well and be a part of the whole volume or will those need to be managed individually? 

Again, thank you for your help and especially your patience! Especially you OldFred!

---

### Post by varunendra on 2013-06-11
> **FMFCorpsman said:**
> Question I have is that this ATA drive is older, will there be unforeseen circumstances when trying to reformat it for the Windows 8 image, or should I be okay?
I don't know Win8. So can't answer that question with confidence. Although the fundamental knowledge tells me that it shouldn't matter. But then again, they are up to changing the 'fundamentals' with win8 :(

> The other question I had, in another post I added an attachment that showed all the different volumes that were unused. some as small as 40 mb, others as large as 14GB. When I shrink the partition for volume C:, will those be shrunk as well and be a part of the whole volume or will those need to be managed individually? 
Each partition will be treated individually, by any partition manager, be it windows' or linux or any other. Just make sure to use the Windows' inbuilt tools to do the job, and you'd be safe.

---

### Post by oldfred on 2013-06-11
Windows installs only with UEFI with gpt partitioning. Or with gpt partitioning will only boot with UEFI. Ubuntu boots from gpt with either BIOS or UEFI but needs different support partitions, efi for UEFI or bios_grub if booting in BIOS mode from gpt partitioned drive.
Both Windows and Ubuntu will only boot in BIOS mode from MBR(msdos) partitioned drives.

Windows also does not correctly reformat a gpt drive to msdos as it leave backup gpt partition table. You have to use fixparts to removed the extra gpt info.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

One user posted that when he buys a new laptop, he buys a better system but only with a hard drive. He then separately buys a SSD, removes hard drive and puts it on shelf and installs Ubuntu to SSD. Then if he ever wants to sell system he reinstalls Windows drive.

---

### Post by GregA on 2013-06-11
FMFCorpsman,

Maybe another valid option is to install Ubuntu 13.04 via a Net install versus any type of boot-up media, as Microsoft has done a wonderful job on not only controlling the OS/Software, but now the hardware.  The average Joe Citizen has no idea this has happened, all they know is they're stuck with a system that is not optimized for a traditional PC user interface.

It may be possible to talk to Dell about this, and see if they can exchange the laptop for another Dell with Win 7 and traditional BIOS (perhaps a refurbished model??)

I'd wait for Old Fred's input before doing much else - - as you might just hose your system and not be able to install any OS (other than Win8).

---

### Post by FMFCorpsman on 2013-06-11
OldFred, I looked up your link for Mark Phelps instructions concerning backing up and shrinking partition. I am confused now, because he is advocating shrinking the partition then downloading Macrium reflect and backing everything up. I was under the impression you wanted to take a snapshot of everything before any changes are made by doing an image and then shrinking the partition. I am downloading Macrium now, but my gut tells me to ignore Phelps sequence and image first.

---

### Post by FMFCorpsman on 2013-06-11
Greg, I'm not familiar with what a net install is, but as of right now I'm waist deep in this direction and getting deeper lol!

---

### Post by oldfred on 2013-06-11
I think the advantage of Mark's suggestion is that the image is smaller. Not sure if I specifically suggest backing up before or after shrink, but you can never have too many backups. Some tools also shrink, but I have never used any of those & Mark has, so I might go with his suggestions.

---

### Post by FMFCorpsman on 2013-06-11
I realized his thought process. When I went to try cloning the primary partition, or C drive to my 140GB clone drive, Macrium told me it would have to shrink the partition to fit. I didn't realize that it wouldn't be just cloning 41GB of data, but the whole 320GB partition. Should I be paranoid, or just clone it and be done with it?

---

### Post by FMFCorpsman on 2013-06-11
here is a print screen of the report when the cloning completed.

---

### Post by GregA on 2013-06-11
In all these thread posts, I don't recall seeing a link to the official Ubuntu Documentation pages which describe the "suggested" method for installing Ubuntu in an UEFI/EFI environment.  

This is actually the documentation which provides a **_base upon which to build from_** (e.g., adding the content from Old Fred's links, etc.)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by FMFCorpsman on 2013-06-11
Something I came across while utilizing OldFred's links extensively. Has anyone heard of or used the Linux-Secure-Remix? It combines Ubuntu 13.04, Boot Repair, OS Uninstaller, and Clean Ubiquity...Whatever the hell that is? It seems to wrap up everything you need to do a dual boot install with Windows 8 in a neat little package. Any pros or cons to this? Link is [here]("http://sourceforge.net/projects/linux-secure/?source=navbar").

---

### Post by oldfred on 2013-06-11
I have seen a lot of the UEFI installs use that version, since it included Boot-Repair. And you will need boot repair whether you use that version or Ubuntu and then download Boot-Repair into it.

[https://launchpad.net/clean-ubiquity](https://launchpad.net/clean-ubiquity)

One of the complaints of the installer is that it does not back up the MBR, so you could restore it later if needed. So others have created tools to add features, but they have not yet been incorporated in the standard install by Ubuntu.

---

### Post by FMFCorpsman on 2013-06-12
Well baby steps! I shrank the partition and rebooted without issue. The partition shrank down to 144.42GB leaving 138.32GB unallocated. Next step is to go into my external drive and get the 12.04 ISO and an installer to put it on a USB again. I would like to make a primary partition, a home, and a swap. Any recommendations or does that suffice?

Also wanted to add I am now taking the 12.04 iso and moving it to a 4GB USB with UNetbootin. I am downloading the boot repair disk ISO as we speak. Do I need to unpack that to the same USB using UNetbootin before I begin the installation of Ubuntu?

---

### Post by varunendra on 2013-06-12
I think the partition plan is okay.

> **FMFCorpsman said:**
> Also wanted to add I am now taking the 12.04 iso and moving it to a 4GB USB with UNetbootin. I am downloading the boot repair disk ISO as we speak. Do I need to unpack that to the same USB using UNetbootin before I begin the installation of Ubuntu?
As far as I know, unetbootin will allow you to boot only one OS at a time.

You can use YUMI (for windows) to easily make the same pendrive multiboot with both (or even more) ISOs : [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

EDIT:
I think I should elaborate a bit. You will still be able to boot only one OS at a time, but you will get an OS menu at startup (with YUMI) to choose which ISO (OS) to boot into. Unetbootin doesn't provide that choice.

---

### Post by FMFCorpsman on 2013-06-12
> **varunendra said:**
> I think the partition plan is okay.


As far as I know, unetbootin will allow you to boot only one OS at a time.

You can use YUMI (for windows) to easily make the same pendrive multiboot with both (or even more) ISOs : [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

EDIT:
I think I should elaborate a bit. You will still be able to boot only one OS at a time, but you will get an OS menu at startup (with YUMI) to choose which ISO (OS) to boot into. Unetbootin doesn't provide that choice.

Now I'm confused Lol! I am only installing on OS Ubuntu 12.04 64 bit. The other item is the boot repair software and as far as I'm aware, it isn't an OS...is it?

---

### Post by varunendra on 2013-06-12
> **FMFCorpsman said:**
> Now I'm confused Lol! I am only installing on OS Ubuntu 12.04 64 bit. The other item is the boot repair software and as far as I'm aware, it isn't an OS...is it?

Nope, boot-repair itself is not. But the boot-repair ISO you are downloading is. It is not meant to be installed though, just to provide you a working platform (environment) on top of which you will be running boot-repair program. After all, any application needs a running OS to run upon :)

The YUMI program just allows you to boot multiple bootable ISOs with a single USB drive, that's it.

With unetbootin, you'll need to make it Ubuntu bootable to install Ubuntu. Then you'll be using it again to make it boot-repair ISO bootable, if it is required. That will overwrite the ubuntu boot configuration such that you won't get the option to boot into ubuntu again afterwards.

With YUMI (or many other multiboot tools like that) you can install both (or more, if there is enough space) on the same usb drive at the same time, and get the option to choose from them at boot time. Just try it, you'll see yourself :)

---

### Post by FMFCorpsman on 2013-06-12
Okay, I tried Ubuntu from live USB with no problems. Restarted and entered installation, got to partitioning portion and set a primary, home, temp, and swap. Last thing I have to do is select where to point the installation. Being that windows 8 is there, do I still select the main 320 GB sda drive, or one of my partitions? I'm stuck at this point. Searched for answers, no clear cut ones. The other thing I noticed is when I used yumi, it didn't have a way for me to set persistence when extracting Ubuntu ISO to USB. Will that be a problem?

---

### Post by varunendra on 2013-06-12
> **FMFCorpsman said:**
> ..got to partitioning portion and set a primary, home, temp, and swap. Last thing I have to do is select where to point the installation. Being that windows 8 is there, do I still select the main 320 GB sda drive, or one of my partitions?
Select the partition(s) as mount points for /, /tmp and /home, as you have planned. You must choose "Something else" option during partitioning stage of the installation to be able to do that.

For boot loader (can't be very sure about this, am just guessing by what oldfred told earlier), choose the root (/) partition. I *think* it will automatically write its boot configuration into the EFI partition which is common for both win8 and Ubuntu.

> The other thing I noticed is when I used yumi, it didn't have a way for me to set persistence when extracting Ubuntu ISO to USB. Will that be a problem?
The only problem with no persistence is that you won't be able to save changes (like a physical CD/DVD). There is a very easy workaround to make that work, but it will work for only any one of the OS/ISOs you are booting. Shouldn't be a problem for you since the only one you want persistence for is Ubuntu.

The workaround is to manually create a "casper-rw" partition or file and add "persistent" flag to syslinux boot line (permanently, or each time while booting). Let me know if it matters that much to you. Making this permanent may take a few attempts, as I don't remember exactly which file this flag needs to be added to. :)

---

### Post by FMFCorpsman on 2013-06-12
It's still installing since I went over my Internet daily usage it's still downloading packages. I selected the main drive ( couldn't wait) was in my free and fast downloading period! Ubuntu let me know that I had to create a partition at least 1 MB (I made it 10MB since I still had a ton of free space) it was called something with bios in it I think? It was a place for the grub to be. I am sure the root or / mount wouldn't work, because when I had tried to load the install there my old laptop, Ubuntu wouldn't boot up. No sleep for the wicked!

---

### Post by FMFCorpsman on 2013-06-12
I might just re install again because persistence is important for me since I'm doing this Linux thing to learn some programming. Need to be able to save my mistakes...mean successful attempts!

---

### Post by oldfred on 2013-06-12
If the installer had to create the bios_grub partition, you installed in BIOS mode not UEFI mode.

How you boot installer is how it installs. So if you boot in BIOS mode it installs in BIOS, if you boot installer with UEFI, it installs in UEFI boot mode.

Since Windows is UEFI, you can dual boot that way but it is not easy. You have to go into UEFI/BIOS and change boot mode to/from UEFI to boot system installed in that mode.
UEFI & BIOS write hardware system data for operating system differently so you cannot easily dual boot from grub menu.

Boot-Repair will convert a BIOS insitall to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).

Did you Shrink Windows with Windows disk tools? And reboot so it can run chkdsk? You have to go back into UEFI and turn off BIOS/CSM/Legacy and see if Windowss boots. Also does Windows boot with secure boot off or just with it on. Some work both ways, others only boot Windows with secure boot on and then you also need Ubuntu to have installed its secure boot or signed versions of grub (shim) and kernels.

---

### Post by FMFCorpsman on 2013-06-12
Old Fred, I was able to disable secure boot , I also shrunk the partition successfully through disk management in windows. I was able to reboot into Windows several times after that, even installed some windows updates on one of the reboots. My bios will not allow me to choose a boot priority under UEFI. It just says Windows Manager. The only way I could get the USB to boot was to go to the command prompt and type "shutdown / r /o", it then restarted and gave meany options including restoral, repairs and such. It also gave me the option to use the USB device, which I did. I am hoping I have done everything correctly so far. Please tell me if that's not the case. As far as creating that grub partition, boot-repair will fix that once the install is done, right? I have the boot-repair on another USB because yumi didn't allow for persistence so I made another live USB with only Ubuntu with undbooten, or whatever it's called.  On my iPhone while its installing.

---

### Post by oldfred on 2013-06-12
Some computers only seem to let you install in BIOS mode. It may be settings well hidden, but Boot-Repair should convert ok. It will not delete bios_grub partition but it is only 1MB so should not matter.

Issues now will be if you have to have secure boot verisons or not. First repair by Boot-Repair will just convert to UEFI. But if that does not work then Boot-Repair on a second repair should offer to update to secure boot versions. You have to boot with secure boot on and check secure boot box in Boot-Repair.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.

---

### Post by GregA on 2013-06-12
So, a couple questions for Old Fred about this type of install . . . . . . if I understand your main points throughout this thread . . . . . the recommended way to get the "install media" to boot-up on a system with UEFI & GPT is to disable "secure boot", but leave the UEFI enabled (in other words, not to enable legacy mode BIOS).    Then, when installing the proper 64 bit Linux like Ubuntu, OpenSuse, clicking/enabling uefi or efi checkboxes wherever they appear on the install screens.  Is this basically the "gist" of installing safely on a Windows 8 machine?  Also of course, using the Windows defrag and partitioning tools to shrink the Windows partition (it's kind of disconcerting in a way, that Windows won't release but about 50% of the HDD capacity . . . . even though it shouldn't need nearly all that space.   Is there a safe way to shrink the Windows partition to about 20-25% of the HDD capacity?  Is the presence of Windows REQUIRED on a UEFI machine (in other words, nuking Windows may not make things simpler re install).

For FMFCorpsman, you should clearly see and map (list out) your partition scheme using a tool like "Parted Magic" live CD.  It runs from RAM, and for a Live CD, is extremely fast.  That way, you can be sure of "where" on the HDD you're actually installing Linux to . . . . otherwise, you may inadvertently overwrite Windows.  For example, on my machines, Linux is typically installed to "sda5", my linux designated partition (you can also ID it by the file type - - ext4 versus NTFS).

Greg

---

### Post by FMFCorpsman on 2013-06-12
Well this is an interesting outcome! The install completed and I restarted, and low and behold ubuntu pops up in all its glory. What did I do wrong? I can still plainly see the 155GB NTFS OS partition there. I am downloading Gparted to get a better picture.

---

### Post by oldfred on 2013-06-12
If you are still in BIOS mode Ubuntu will boot without any issue from UEFI. It just may show Windows entries in grub menu but since that is UEFI those will error out.
You may get video issues or need other boot parameters if boot does not fully work.
But if you go into UEFI and turn it back on then you should be able to boot Windows. May also need secure boot on. But then Ubuntu will not work unless you turn BIOS back on and UEFI off.

@GregA
One or two have totally erased drive and installed Ubuntu. Some have said you may need Windows for some things, but that may vary by system. Some early versions could only get into UEFI from Windows and totally locked system, but now Ubuntu has a menu entry to get into Ubuntu which you should test to make sure it works before thining about removing Windows.

This was Vista but I think the same applies. Some of the third party Windows partition tools may also work.
       Windows Disk Cleanup tool to houseclean
defrag at least twice
#Partitioning generally better
Windows Vista - partition your hard drive using Disk Management, if XP use Gparted
25GB at an absolute minimum 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

    
       shrink the primary partition from the Windows MMC or Disk Management.
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
You can also try downloading and installing the FREE version of Partition Wizard in Win7. It may allow you to safely shrink the Win7 OS partition more than does MS.

---

### Post by GregA on 2013-06-12
I *think *the problem was/is installing Linux with UEFI disabled ? ? ? ?   

It seems it's REQUIRED to turn "Secure Boot" off - - _so the install media (CD or DVD or USB-Stick) will be allowed to load & boot_.   By keeping UEFI enabled . . . . the install is done in "UEFI mode" vs "BIOS mode".   

Then, use the 64bit version of any "Buntu" and click on the UEFI/EFI checkboxes (on the install screens).   

Then, after successful install and bootup into Linux, restart the system and go into setup again, _to re-enable secure boot_.   Of course, just like before the UEFI days, Linux still needs to be installed to the right partition - it may be listed slightly different, but it should be identifiable via the file-system type (ext2,3,4 or Reiser or XFS, etc. etc.).

I'm interested to see what running gparted on the Parted Magic CD shows . . . . .  .

---

### Post by FMFCorpsman on 2013-06-12
I haven't tried any of that yet, and I won't right now. Ubuntu is very happy and flourishing, I'm downloading updates now. I need to start learning what I need to add and how to begin my apprenticeship at different programming languages, so thats next on the list. A program I want to write, translates Tibetan Uchen Script into Wylie, and then a Romanized pronunciation. I want to translate Buddhist scripts from the their written language to their spoken language basically. I have an idea I will need a database program, so that is next on my research. I want something powerful, but very compatible with Ubuntu.

---

### Post by oldfred on 2013-06-12
Several choices for DBs.

 Databases:
[http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL](http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL)
[http://www.sqlite.org/](http://www.sqlite.org/)
MariaDB versus MySQL - Features - fork of MySQL
[https://kb.askmonty.org/en/mariadb-versus-mysql-features/](https://kb.askmonty.org/en/mariadb-versus-mysql-features/)
LibreOffice/OpenOffice database

---

### Post by GregA on 2013-06-13
While MariaDB, MySQL, etc. are excellent databases -- they're probably overkill for 9 of 10 people in personal use cases.   At an organization, public or private, such db's are essential to run slice & dice reports, batch jobs, spc analysis, etc.   However, I'm going to also offer a recommendation to look into the 5 to 10 open source "tree-structure" hierarchical databases.

Currently, I'm using a simple application for data storage, retrieval and conversion to pdf, html, etc.   That app is "CherryTree" - - see screen pic below:

[[IMG]http://imageshack.us/scaled/large/6/6xk.png[/IMG]](http://imageshack.us/photo/my-images/6/6xk.png/)

This program has some great features and it's easy to install and run.   DBMS programs like MySQL are almost like another OS, and unless you have prior training/experience, maybe CherryTree could cover your needs.  Another great Tree database is "TreeLine", however, it's currently under full re-development and not as fleshed-out as CherryTree.  Make sure whatever you use - that it's secure and can be "compressed and encrypted."  CherryTree is in the repos, however, you should add a PPA (Personal Package Archive - instructions are at this link:  (Vincent Cheng&#8217;s PPA:)   [https://launchpad.net/~vincent-c/+archive/cherrytree]("https://launchpad.net/~vincent-c/+archive/cherrytree")   Also, the homepage is:  [http://www.giuspen.com/cherrytree/]("http://www.giuspen.com/cherrytree/")

Greg

---

