---
title: "Installing Ubuntu with Win8"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by DRatJr on 2013-04-20
So I am completely new to ubuntu, I have used Wubi in the past on other laptops, and installed it easily, but nothing very technical. I have many questions I need answered and help with.

Info:
Samsung Series 7 (15.6'') Computer
I have EFI and Secure Boot on, Idk about if HDD boots with EFI or what.
I have 12.10 .iso file
No USB Drive / CD slot

Now here's what I want to know:
How do I go about installing Ubuntu? I have read the problems associated with EFI but I don't know what guide to follow.
How can I install it without a USB drive or CD slot?
I want to dual boot it with Win8, not within but in its own partition. How can I do this?

I have read many guides but all seem different and I am not sure what to do at this point.

Thanks!

---

### Post by sandyd on 2013-04-20
> **DRatJr said:**
> So I am completely new to ubuntu, I have used Wubi in the past on other laptops, and installed it easily, but nothing very technical. I have many questions I need answered and help with.

Info:
Samsung Series 7 (15.6'') Computer
I have EFI and Secure Boot on, Idk about if HDD boots with EFI or what.
I have 12.10 .iso file
No USB Drive / CD slot

Now here's what I want to know:
How do I go about installing Ubuntu? I have read the problems associated with EFI but I don't know what guide to follow.
How can I install it without a USB drive or CD slot?
I want to dual boot it with Win8, not within but in its own partition. How can I do this?

I have read many guides but all seem different and I am not sure what to do at this point.

Thanks!
Are you talking about [URL="http://www.amazon.com/Samsung-Series-NP700Z5A-S0AUS-15-6-Inch-Laptop/dp/B006R103MQ#productDetails"]this laptop?
[/URL]

Also, at the moment, Wubi does not work with UEFI/Non-MBR partition tables

---

### Post by DRatJr on 2013-04-20
No, it is [This one]("http://www.bestbuy.com/site/Samsung---15.6%22-Touch-Screen-Laptop---8GB-Memory---1TB-Hard-Drive---Metal/8048198.p?id=1218863727568&skuId=8048198"). I know wubi doesn't work with it, or from what I've read I've learned it. But is there any other way to install it?

---

### Post by sandyd on 2013-04-20
From a quick glance - a few options
[LIST]
[*]Check if your computer supports booting from SD/memory card
[*]Use PXE (but you need to setup another computer with the PXE server)
[/LIST]

Getting a USB drive is the cheapest/easiest imo

Also - no guarantees that the touchscreen will work - some do some dont

---

### Post by DRatJr on 2013-04-20
Ok well I can get a USB. If I do, how do I go about installing then?

---

### Post by sandyd on 2013-04-20
> **DRatJr said:**
> Ok well I can get a USB. If I do, how do I go about installing then?

General Steps
[LIST=1]
[*]Disable Secure/Fast boot in UEFI
[*]Use UnetBootin to get the Ubuntu iso onto the USB drive. Drive must be formated as FAT32
[*]Boot and install from USB Drive
[*]Restart and/or Use Boot Repair ([http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)) to restore boot loader (EFI)
[/LIST]

---

### Post by oldfred on 2013-04-20
Some more info. Is this an UltraBook? That makes a bit more difficult as it has a small SSD, but it is RAID.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

### Post by DRatJr on 2013-04-20
> **oldfred said:**
> Some more info. Is this an UltraBook? That makes a bit more difficult as it has a small SSD, but it is RAID.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.


Ok so I have turned of Fast Start in control panel, is that what you're referring to?

I have the 64 bit version of 12.10, is this fine?

How do I make the flash drive boot in EFI mode?

How do I back up the EFI and Windows partitions?

I have shrunken my partition by 50 gb, thats what I want ubuntu to have. It is unallocated space as of now.

And do I need secure boot on or off with 12.10? 

Remember I am really noob so I am not sure of some things, hence all the questions.

---

### Post by oldfred on 2013-04-20
Also backup efi partition.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

How you boot installer is how it installs. From UEFI menu on flash drive should be two choices, one UEFI and the other BIOS/CSM/Legacy/AHCI or something.
      
 Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 

While Ubuntu installer should boot with secure boot on, many vendors do not let you. So best to just install with secure boot off, but with UEFI. How you set that varies by vendor.

And some do not boot anything but the Windows efi file once installed. But Boot-Repair has a work around where it renames the grub shim file that has the same Microsoft key to be the Windows file and then from grub you boot the Windows file that has been backed up.

Some other Samsung, but they were UltraBooks which make it a lot more complex. But they may have some hints on other issues.

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by DRatJr on 2013-04-20
Ok So backup Windows and EFI, then turn secureboot and fast startup off?

Then when I attempt to boot from USB it will ask automatically ask me if I want to boot EFI or legacy etc?

Also how do I make it to where I can boot from USB?

---

### Post by oldfred on 2013-04-20
If you have not downloaded ISO. For almost all computers now the 64 bit version is better..

 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by DRatJr on 2013-04-21
I have downloaded it. I mean how do I make my computer BOOT from it. Not how to do it.

---

### Post by oldfred on 2013-04-21
You should be able to directly go into UEFI/BIOS or use a one time boot key (f12 on my system but varies) and choose the flash drive to boot.
Flash drive has to be correctly configured as a bootable device, not just a copy of ISO.
With UEFI you should get two flash drive choices, one UEFI and the other BIOS/CSM/Legacy or something.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by DRatJr on 2013-04-21
I know I usually use netbootin to do it. So hold shift when hitting restart, go into UEFI settings, and find a boot menu?

---

### Post by oldfred on 2013-04-21
I attached my BIOS screen shots and a couple from users with UEFI, but I do not think they are the screens you may see.

---

### Post by DRatJr on 2013-04-21
Ok so heres what I have configured:

Fast BIOS off
Fast Boot Off
Secure boot Off

Now I see the flash drive in the boot menu, what do I do? Put it first? Select to boot from it? Or what?

---

### Post by DRatJr on 2013-04-21
> **oldfred said:**
> I attached my BIOS screen shots and a couple from users with UEFI, but I do not think they are the screens you may see.


This is what  I get when I did those things. It will not boot from my USB though, keeps going into win8.

[IMG]https://dl.dropboxusercontent.com/u/40868833/IMG_20130421_145124.jpg[/IMG]


[IMG]https://dl.dropboxusercontent.com/u/40868833/IMG_20130421_145135.jpg[/IMG]


[IMG]https://dl.dropboxusercontent.com/u/40868833/IMG_20130421_145144.jpg[/IMG]


[IMG]https://dl.dropboxusercontent.com/u/40868833/IMG_20130421_145116.jpg[/IMG]

---

### Post by oldfred on 2013-04-21
Better if you shrink photos and attach not insert. 

I assume Staples is the label on your Flash drive. So can you not boot from it.

Perhaps your is one of those that will only boot from a flash drive with CSM or BIOS mode?

---

### Post by DRatJr on 2013-04-21
No I can not boot from the flash drive. And yes staples is the name.

I tried it in CSM and UEFI mode, and got a screen that said something about Linux not booting

---

### Post by DRatJr on 2013-04-21
Ok update: It says this when I choose CSM Mode only: (see pic)



When I choose CSM and UEFI, it boots Win8.

---

### Post by oldfred on 2013-04-21
How did you create flash drive? Some have issues with one creator or another, or some brands of flash drives. If you got that far flash drive should work.

There were bugs in old versions of syslinux based installer. 

Sometimes these fixes help. Or Sometimes download is not valid and you need to do that again. You can check download with md5sum to verify that it is correct.

 syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
[http://ubuntuforums.org/showthread.php?t=2078599](http://ubuntuforums.org/showthread.php?t=2078599)

      
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

   Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

   [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[URL="http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"]http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/

[/URL]
 Also instructions for DVD or USB
[URL="http://www.ubuntu.com/desktop/get-ubuntu/download"]http://www.ubuntu.com/desktop/get-ubuntu/download
      [/URL]
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

    [URL="http://www.ubuntu.com/desktop/get-ubuntu/download"]
[/URL]

[URL="http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/"]
[/URL]

---

### Post by DRatJr on 2013-04-21
Unetbootin freezes on me.

---

### Post by DRatJr on 2013-04-21
I GOT IT TO BOOT!! Lol

It boots as UEFI: Staples, so I assume that means its in UEFI mode. Also, I set the boot to UEFI mode as well, didn't need to change it to CSM or UEFI and CSM.

Now what do I do? I want to dual boot ubuntu, and do not want to install inside of windows. I have already partitioned and left as unallocated 50 gb for the install. What are my next steps to dual booting ubuntu?

---

### Post by oldfred on 2013-04-21
Progress. From live install check that major things work. Then you can click on the install icon. Did you have to add any boot parameters for video issues?

With 50GB you can have several choices. You can do a standard auto install into unallocated space. It will only create / (root) & swap. If you want you can use Something Else and manually create partitions, but with 50GB it is optional. Install should be similar to any BIOS install, except grub will install boot files into the efi partition in a new folder next to the Windows files.

Many systems have issues with dual booting and grub's os-prober has a bug, so it is best to install Boot-Repair into your install if it boots or the live installer to update your install, and add correct Windows boot entries as a work around on the os-prober bug.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Even with UEFI the basic install process is the same.

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by DRatJr on 2013-04-21
Ok I am noob like I said lol and I am not sure what a lot of that stuff means. I did not do anything to anything. Only hit try ubuntu and it booted. I didnt test video or anything and dont know how to add anything to anything.

Also, I do not understand what your saying. Sorry! :\

---

### Post by oldfred on 2013-04-21
If you have 50GB free, you can then just click on install. Do not choose the option to overwrite entire drive as that eases your entire system. Since you have unallocated space it should offer a choice to install into that. May just be best to run that.

---

### Post by DRatJr on 2013-04-22
But do choose other correct? And use the 50gb I have set aside?

---

### Post by oldfred on 2013-04-22
IF you go about half way down on this do you get the same Installation Type options or one more that says to install into free or unallocated space? If so use that.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I always partition in advance from live installer or a separate download of gparted or Parted Magic which all use gparted as the partitioning tool. The I use Something else so I can manually select partition, format (ext4)  and mount. You need / (root). If you partition in advance and have swap it finds it automatically, otherwise you have to create another partition for swap. If you do not hibernate and have 4GB or more of RAM, just make swap 2GB, if you want to hibernate you need it to be the size of RAM in GiB not GB or a bit larger in GB.

---

### Post by oldfred on 2013-04-22
Auto install into the unallocated would still be the easiest choice. But DO NOT use any choice that says to use entire drive.

More examples:
 Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

See post #8 with example of creating a partition.

 The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Bit older so screen grapics are a bit different but otherwise same process. You do not have to create /home unless you have lots of room.

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by oldfred on 2013-04-22
If you get it installed run the BootInfo report and post link it gives. Do not run any repairs just yet.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by DRatJr on 2013-04-22
Here is my boot info summary:

[http://paste.ubuntu.com/5593372/](http://paste.ubuntu.com/5593372/)

---

### Post by oldfred on 2013-04-22
That looks good, you say Ubuntu boots ok.

Do you have Secure boot off?
Windows will not boot from grub menu as grub has a bug.
this entry is really for BIOS boot and is not configured correctly for UEFI.
'Windows 8 (loader) (on /dev/sda2)'

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Boot-Repair will add a correct entry.
If you go back into UEFI menu with secure boot off, Does Windows boot? Many systems only boot Windows with secure boot on. Try that also. 
If Windows boots without secure boot on, it makes it a lot easier as you do not have to do anything except add a correct Windows dual boot entry. But most do not.

And then with secure boot on does Ubuntu boot? I do not think so, as it looks like you have standard efi files not the shim and signed kernel versions. Boot-Repair should offer to update that also, but you may have to boot from installer, install Boot-Repair to the installer and check off secure boot. Or with secure boot off can you check the secure boot option in Boot-Repair. I have not done it so I do not know all the details but it does work.

And some systems are modified to only boot Windows efi file. For those systems Boot-Repair does a file rename.

 fix-windows-boot backup-and-rename-efi-files

---

### Post by DRatJr on 2013-04-22
OK i don't understand all of what you said but secure boot is off. When i choose windows from efi or pressing f10 it boots fine. Secure boot is off and everything boots fine. 

What steps do i take? Can you enumerate with links? I'm noon remember! Sorry lol

---

### Post by oldfred on 2013-04-22
If Windows & Ubuntu both boot with secure boot off that is great.

Boot repair may try to do too much, I am not sure if you can easily select all the repair options. All you need is a correct Windows boot stanza.

You can do this from Ubuntu to add a correct entry manually. Both should work, I copies your UUID into the second one.

 gksudo gedit /etc/grub.d/40_custom
do not delete the lines already in the file.

After copying entries run this to add to grub menu, they will be at bottom of menu:
sudo update-grub

Copy these two entries into 40_custom. Both should work.

```
 menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows bootmgfw.efi " {
search --fs-uuid --no-floppy --set=root 7A80-A178

    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}



```

---

### Post by DRatJr on 2013-04-22
I added that entry in the code box. Did not work. Is that because it says windows 7?

Also, how do I know if Ubuntu is using the 100 gb I set aside for it? In my menu on the left hand side it says these:

Windows RE tools
869 GB Volume
Samsung_REC2
Samsung_RECi th

But idk if Ubuntu is using the 100 GB I set aside for it, and I want to make sure that it is. On my windows partitioning tool, it is labeled as D: and is a RAW system or w/e. It says it has around 92 gb left of free space so Idk.

---

### Post by oldfred on 2013-04-22
When you set aside 100GB, it often is not exact. New install uses about 4.5GB and whatever you used for swap so 92GB left sounds about right. Any partition Windows sees as unformatted it sees as RAW. I am surprised it shows that much, Windows 7 and before did not show anything other that unknown.

I should have changed desc to Windows 8, you can if you want. But that is just description.
Do you get an error message or what happens when you try to use either of those entries.

I like to label partitions, you can use Disk Utility or gparted and click on your 869GB volume and label it Windows or WinSys or something. Install does not have gparted as you cannot edit mounted partitions, so it is not normally installed by default. If you want it. I use to as I like the view of partitions it gives and I have more than one drive so I can work on other drives or a flash drive from my install.
sudo apt-get install gparted

If from file browser you click on your 869GB partition to mount it and run this from terminal, what does it show.

df -h

---

### Post by DRatJr on 2013-04-22
Ok I will install gparted. But how do I mount and run the 869 from terminal? Not sure how

---

### Post by oldfred on 2013-04-22
If the previous are not working maybe it needs the more complete version. It loads (insmod) several grub drivers that usually are loaded by default anyway.

```
 menuentry "Windows 8 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 7A80-A178

    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}


```

If you click on the 869GB partition in the file browser Nautilus does it open? NTFS has been improved to not open NTFS partitions that are hibernated or need chkdsk, so it may not since the default setting for Windows 8 is hibernation. 
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)

It actually is better to shrink Windows some more from Windows and from gparted create a new NTFS data partition. Then from fstab mount that partition read/write and not normally do anything in the Windows system partition. The NTFS driver shows all files and folders. I used to in Windows turn that on, but occasionally damaged my Windows, so best not to normally use the system partition.

---

### Post by DRatJr on 2013-04-23
Something weird is happening now. I have done nothing at all to ubuntu, but now it hangs a purple screen. This is weird.

---

### Post by DRatJr on 2013-04-23
Also, I do not want windows 8 to be hibernating. I want Ubuntu to run independent, to dual boot and be free of windows. Not to replace it, but to be its own os. Am i doing this or using windows with installing alongside?

---

### Post by oldfred on 2013-04-23
I do not have Windows 8, but the links I posted above say it always hibernates to speed boot. Someone recently did post that the settings to turn that off are buried really deep in the menus.

What video chip/card do you have. It may have updated drivers and not be correct. Or if you have dual video, or Optimus you need special drivers. 

Can you boot from the recovery mode? The is the second entry or may be in the sub-menu?

---

