---
title: "Dual boot problem."
date: 2014-07-15
forum: New to Ubuntu
---

### Post by oXydead on 2014-07-15
Hi guys,  i am new in this forum (and new to linux). 
3 days ago,  i installed 14.04 x64, alongside my windows 8.
Ubuntu, boots just fine but... When i boot windows:
1) The login screen,  from Seattle's Space Needle photo, changed to a blue wallpaper(don't know if i have to mention this). 
2) When i enter my password on Windows 8, it takes about 10 minutes to loging to Windows and when it logs,  i just see a black screen. 
3) When in windows loging screen,  the shut down button is pressed and no dialog appears. 
4) On turning on laptop, the dual boot of linux appears instead of windows 8 OS selection. 
And 5) In ubuntu,  my main hdd is not mounted and thus i can't access my files. (tried sime sudo mkdir commands from some answers but it says, i don't have root privileges). 
I am using an HP Elitebook 8460p.
Thanks in advance, if any other info is needed tell me. 
Keep in mind, I'm a total newbie in Linux in general.

---

### Post by slooksterpsv on 2014-07-15
How did you install Ubuntu?

Generally, when I install, I do a custom install, setup my partitions and install Grub ONLY on the partition Grub is on.

As for regard to your laptop Windows being slow, how did you partition the drive for Ubuntu? If you resized your current disk, you may need to run a chkdsk on it.

```

sudo mount /dev/sda2 /mnt

```
sudo means act as root essentially, /dev/sda*#* # is either 2 3 or 4 is usually the drive which has your Windows data if dual-booting. If you go to the File Manager on your Ubuntu, you can normally see the drive in the left hand side and mount it. Now you WON'T be able to write to it if you just shut down Windows. Windows 8, by default, shutdown just Hibernates the computer. With Windows 8 you have to restart in order for it to not hibernate. (Odd I know) You can change this in the power settings for the hibernation under Windows.

You can try my program in my signature, efibootorder, to see if you can change the boot order between Windows and Ubuntu. Usually Ubuntu, and like distros, when modifying the EFI, puts itself at the top moving Windows to the next boot option. With efibootorder you can move those around. Sometimes when booting you can press F12 and select what you want to boot from off the HDD - Windows, Windows Recovery, Ubuntu, Other OSes, etc.

---

### Post by yancek on 2014-07-15
Are you using uefi to boot both Ubuntu and windows 8?  I believe that is necessary.

Your wallpaper situation on windows and the login time are unrelated to the Ubuntu install or dual-booting.

> ) When in windows loging screen,  the shut down button is pressed and no dialog appears. 

Don't know what that means?  Pressed by whom?  It shuts itself down?

> ) On turning on laptop, the dual boot of linux appears instead of windows 8 OS selection. 

Does that mean you see multiple entries for Ubuntu?  That's expected.  If you don't see a windows entry, that's not expected and may be because you installed Ubuntu in Legacy mode rather than uefi.

>  In ubuntu,  my main hdd is not mounted and thus i can't access my files.

You'll have to explain that.  Where is Ubuntu installed if not on your main hard drive?  Do you have multiple internal/external drives?

---

### Post by oXydead on 2014-07-15
When i click on shutdown, the dialog on the right corner of the screen, won't appear. I installed it via live usb and did it alongside on my main hdd. That's all i did.  Install alongside windows 8. No partitions, whatsoever. 
And yea, multiple entries for ubuntu but only one for Windows. Windows 8 loader.

---

### Post by sandyd on 2014-07-15
**Moved to absolute beginners section**

---

### Post by P_THE_AWESOME on 2014-07-15
The most important thing to do first is backup your data. In the Ubuntu file manager, you should see the Windows drive. Browse to where you keep your files (your home folder is [FONT=courier new]/Users/<username>/[/FONT]). Back them up to an online cloud service like Dropbox or a physical *completely separate and removable* hard drive or flash drive. **_Make sure that it is unplugged from your computer before continuing!_** Be sure to eject/unmounted it properly before removing it.

Please try installing and running [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). If you click the "Advanced Options" arrow and go to the "Other Options" tab, make sure "Repair Windows boot files" is checked. _Try rebooting after this and see if this step alone fixed it. You may not need to continue._

Next, you need to try repairing the Windows filesystem (NTFS partition).
[LIST=1]
[*]```
sudo apt-get install ntfsprogs
```
This will install the tool that will repair the NTFS filesystem. 
[*]```
sudo fdisk -l
```
This will help you find what name it is under in Ubuntu. It will be something like [FONT=courier new]/dev/sda1[/FONT]. _**If it's not obvious which one it is, post the output of [FONT=courier new]sudo fdisk -l[/FONT] and we'll tell you which one to use.**_ 
[*]```
sudo ntfsfix <insert name here>
```
This will run the repair. It may take some time depending on how large and full the partition is. 
[/LIST]

That should hopefully fix windows. If it doesn't, tell me and I'll post a link to the Windows OS repair instructions. With Windows 8, it is possible to keep your files and programs but reinstall all Windows System files. There are also other built-in repair tools.

Good luck!

---

### Post by yancek on 2014-07-15
My understanding is that with windows 8, you need uefi and Ubuntu would need to be installed as uefi also for both to work.  Maybe the boot repair script will output some useful information.  Did you do an md5checksum on the Ubuntu download prior to putting it on the flash drive or DVD you used to install?

---

### Post by P_THE_AWESOME on 2014-07-15
> **yancek said:**
> My understanding is that with windows 8, you need uefi and Ubuntu would need to be installed as uefi also for both to work.

I am running Windows 8 on an old Dell Latitude D620 (as I write this post) that *definitely *doesn't have UEFI on it. Also, Ubuntu simply wouldn't work if it needed UEFI and didn't get it, not Windows 8 (especially considering it worked previously).

---

### Post by oXydead on 2014-07-15
I can't backup my files,  since i installed Ubuntu alongside windows 8 and my main hdd that has my files, won't mount.

---

### Post by oldfred on 2014-07-15
Do not install ntfsprogs, it will probably uninstall the standard NTFS driver and install an old version of ntfsprogs.
They merged the two & NTFS is now installed by default with all the features of both.

       On April 12, 2011 it was announced that Ntfsprogs project was merged with NTFS-3G
[http://en.wikipedia.org/wiki/Ntfsprogs](http://en.wikipedia.org/wiki/Ntfsprogs)

Best to run the BootInfo report and post the link to it so we can see details. You can run it from Ubuntu if install is working or from a live installer, or download a full liveCD version to use.

---

### Post by P_THE_AWESOME on 2014-07-15
Yes, BootInfo would probably be a good idea. However, because you can't mount the NTFS partition, it might be damaged or partly corrupted. You will need to repair it sometime. This is probably why Windows is responding the way it is. Depending on whether if you bought this computer with Windows 8 already installed on it (not upgraded or manually installed) there might be a recovery partition that will eventually pop up when you try to boot into Windows. I wouldn't risk trying to boot into it and damaging more though. Your best bet will be to run the official Microsoft NTFS repair. I've had the best luck with it in the past. However, you will only be able to use icrosoft's tool if you have another Windows 8 computer that[ you can create a repair disk]("http://windows.microsoft.com/en-us/windows-8/create-usb-recovery-drive") from or have an upgrade or install CD you can boot into.

Again, first let's get more details: run BootInfo.

---

### Post by oXydead on 2014-07-15
[https://mega.co.nz/#!BxpHSZpT!_JHgXVdLMdEELLUNGgZPEZPiZtXXWo72HNylvpWkSKM](https://mega.co.nz/#!BxpHSZpT!_JHgXVdLMdEELLUNGgZPEZPiZtXXWo72HNylvpWkSKM)


Sorry 'bout the link but I'm using my phone and it wont let me attach a link.

---

### Post by at_first_light on 2014-07-15
> **P_THE_AWESOME said:**
> I am running Windows 8 on an old Dell Latitude D620 (as I write this post) that *definitely *doesn't have UEFI on it. Also, Ubuntu simply wouldn't work if it needed UEFI and didn't get it, not Windows 8 (especially considering it worked previously).

Unrelated to fixing your problem, but on a side-note Windows 8 supports both BIOS with MBR partition tables, and UEFI with GUID partition tables. The reason most people run Windows 8 with UEFI is that the big name manufacturers that ship computers with Windows 8 OEM editions pre-installed are required by Microsoft to enable secure boot (which means using UEFI).

---

### Post by yancek on 2014-07-15
> Unrelated to fixing your problem, but on a side-note Windows 8 supports  both BIOS with MBR partition tables, and UEFI with GUID partition  tables. The reason most people run Windows 8 with UEFI is that the big  name manufacturers that ship computers with Windows 8 OEM editions  pre-installed are required by Microsoft to enable secure boot (which  means using

The post you are quoting is in response to my earlier erroneous post.  Based on what I have read about uefi since I don't have a computer using it, it isn't possible to mix/match uefi with MBR meaning  that if mbr is used for windows 8, then mbr needs to be used for Ubuntu or another system and if uefi is used for windows 8 then it needs to be used for Ubuntu or another system.  Is that correct, or not?  Obviously, my earlier post didn't state this correctly.  I've not used windows 8 other than on virtual software so have no idea.

Thanks to you for clarify it and also to P_THE_AWESOME for pointing out the error.

---

### Post by P_THE_AWESOME on 2014-07-15
Yes, the partition table types will need to match. However, Ubuntu should handle this itself with no problem. Also, throughout the file uploaded, it talks about an MBR or msdos (same thing) partition table. No cause for alarm.

It seems that Boot Repair was run (line 389):
> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
This is why you can't mount the drive! Sneaky Windows 8 has locked it. What got my attention was this:
```
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
```
I'm not sure if this will work (or damage Windows 8), but you can try it if you want. **Boot Repair may not work if it can't access that partition.**

Here's line 670 through 678:
> =================== Final advice in case of recommended repair


The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda6 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot
I don't think it is a problem that your BIOS isn't detecting Ubuntu. You can try to fix this if you want though. Boot Repair might do this for you automatically.

It is suggesting to unhide the GRUB OS/boot selection menu at startup (I think this is what you want) and also to try to fix the windows boot. These two options are available from the "Advanced Options" arrow in Boot Repair. The GRUB boot menu is in the first tab in that and the Windows Repair in the last.

Unless anyone else finds another problem that I missed, I think Boot Repair is your best bet. **I'm still not sure about deleting that hibernation file though.**

---

### Post by oldfred on 2014-07-15
I have seen the remove hiberfile suggested and seen it not work in some cases.
       Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

I think it may be better to reinstall a Windows boot loader temporarily with Boot-Repair's advanced mode and directly boot Windows. Then correctly shut Windows down without hibernation.

      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

### Post by at_first_light on 2014-07-16
> **yancek said:**
>  it isn't possible to mix/match uefi with MBR meaning  that if mbr is used for windows 8, then mbr needs to be used for Ubuntu or another system and if uefi is used for windows 8 then it needs to be used for Ubuntu or another system.  Is that correct, or not?  


I would say yes, but there is one exception. When using a BIOS based computer Windows requires an MBR partition table be used, Ubuntu however can use either a GUID partition table or an MBR partition table. Due to this if 2 hard drives are used one could have Ubuntu running from a GUID partition table, and Windows running from an MBR partition table. However in the case of UEFI based computers both Windows and Ubuntu require a GUID partition table. 

Ubuntu's ability to support GUID partition tables on BIOS based computers is why you see so many questions on AskUbuntu.com where the OP has accidentally gotten Windows 8 booting in UEFI mode, and Ubuntu in CSM mode (Bios emulation for legacy compatibility), and now has to irritatingly switch back-and-forth when booting into the other operating system. :P

---

### Post by at_first_light on 2014-07-16
> 
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully


Have you disabled fast-startup in Windows 8? It's a feature in Windows 8 that prevents Windows from turning off when you click Shutdown. I just puts it into a very minimal hibernation, and you can even boot into other operating systems during this which can cause mount problems for them since the Windows kernel maintains control of the system to a certain degree.

1. Go to Control Panel/Hardware and Sound/Change what the power buttons do
2. Uncheck the box beside "turn on fast-startup", and save your changes.
3. Shut down (not restart).

---

### Post by oXydead on 2014-07-16
Used  boot repair, then restarted my laptop. 
While booting windows, a dialog appears that last time windows weren't correctly shut down last time. 
Pressed on troubleshoot, so i can boot into dafe mode but it won boot into safe mode either. 
Did the whole process fron the start and instead of troubleshooting, i shut down the laptop. 
Still nothing.

---

### Post by P_THE_AWESOME on 2014-07-16
Yes, I agree with olfred and at_first_light. You need to try to get into Windows how olfred has described and turn off "Fast Startup" a.k.a. "Hibernating without keeping you logged in when you click Shutdown."

After that, you should be able to fully run Boot Repair like it says to at the end of Bootinfo:
> =================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda6 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot
You will just run it with the GRUB boot menu and Windows Fix enabled. **Fix the Windows shutdown first.**

---

### Post by oXydead on 2014-07-16
I can't boot into windows no matter what.  That's my problem.
And now in booting options,  i have 2 windows 8 options. 
On sda1 and on sda2.

---

### Post by oldfred on 2014-07-16
Did you reinstall the Windows boot loader to the MBR and use f8 to get into recovery mode or repair console?

Some have been able to use f8 from a grub boot of Windows but it is too quick. You have to press key at almost same time or try many times. Often easier just to temporarily reinstall Windows boot loader to MBR.

---

### Post by oXydead on 2014-07-16
Yes and F8 won't work for my laptop from day 1.
Is there at least a way,  that i can access my files to my main hdd so i can format my laptop.

---

### Post by oldfred on 2014-07-16
Not easily when it is hibernated.

You may be able to force it into a read only mode, so you can backup your data. You will probably not be able to backup much else.
 Manual mount read only may work to copy data, change sda5 to your partition.
sudo mount -o ro /dev/sda5 /mnt


Do not reinstall Ubuntu without reading major caution on method to use in link in my signature.

---

### Post by slooksterpsv on 2014-07-17
In previous Ubuntu installations, even if I didn't have a hiberfil.sys I sometimes had an issue with the pagefile. Don't ask me why, just a thought to throw out there. It was some time ago, and I think it was only for shrinking the drive, never mind ignore this post.

---

### Post by oXydead on 2014-07-20
Nope,  the command didn't work. Now,  my laptop only boots in Windows and the dual boot option for Linux won't appear. 
Found out, that Windows boot from X:/
My main Windows are in C:/
No way to mount my hdd.

---

### Post by oldfred on 2014-07-20
May be best to see details. Post link to BootInfo Summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oXydead on 2014-07-20
1st thing 1st.
I had created a partition of 12GB.
I had problems installing ubuntu in the partition, so i went on and installed ubuntu, alongside windows.
But imho, ubuntu was installed in the 12GB partition wich was named X:/ and on the same location (somehow) there was a windows 8 loader installed there.
That is why, my windows woudn't boot.
Afterwards, i also couldn't boot into ubuntu.
So, i took off the HDD and booted ubuntu from a live usb.
Formatted the partition that got lubuntu and the windows loader in it.
Then, i connected the hdd via usb and some folders are missing.
The main thing here, i guess is to boot from C:/ now.

---

### Post by slooksterpsv on 2014-07-20
Hmm... I like to do my own custom installations because I haven't tried install alongside on EFI systems. You could always try to reinstall and do a manual partitioning, meaning explicitly telling Ubuntu to use the 12GB of space, installing GRUB to /dev/sda6 (let's say that's your 12GB Ubuntu partition).

Are you able to get into Windows now?

---

