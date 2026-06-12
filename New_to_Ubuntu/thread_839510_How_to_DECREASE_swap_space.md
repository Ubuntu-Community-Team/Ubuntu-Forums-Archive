---
title: "How to DECREASE swap space?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by knut100 on 2008-06-24
When I installed Ubuntu 8.04 I did something terribly wrong.
I made a swap partition of 50 GB! 

I quickly understood that this was neither wise or useful, and therefore I ask you, lovely, intelligent forum masters:

-How do I decrease my swap partition safely?




INFO:
Acer Aspire 7520
Ubuntu 8.04 Hardy Heron (AMD 64)
Hard drive with swap problem - 160 GB ATA

---

### Post by VChief on 2008-06-24
I would say download gparted Live CD from here:  [http://sourceforge.net/project/showfiles.php?group_id=115843](http://sourceforge.net/project/showfiles.php?group_id=115843)

Then, reboot your computer with the CD in there and you can fix your swap issue there. You can decrease your swap partition and increase a different partition

---

### Post by Ub1476 on 2008-06-24
You can install gparted from the repos, and open it under the administration menu. From there you can right click on swap -> swap off -> rezise partition.

I have never rezised my swap partition my self, but I guess it works fine. ;)

---

### Post by VChief on 2008-06-24
> **Ub1476 said:**
> You can install gparted from the repos, and open it under the administration menu. From there you can right click on swap -> swap off -> rezise partition.

I have never rezised my swap partition my self, but I guess it works fine. ;)

That'll work too, but you wouldn't be able to resize a mounted partition (say /home) to fill the new space. That's what the LiveCD works really well for.

---

### Post by knut100 on 2008-06-24
Wow, great response. 

It worked beatuifully, but now I'm wondering;

If I format it to fat32, then I can use it to install Vista? Because I need Windows for some programs...

---

### Post by VChief on 2008-06-24
Somebody will probably know more...but as far as I know, Vista will require ntfs. Vista also requires at least 20GB, I believe (it says 20 GB with 15GB free). Also, I assume it's like previous Windows in that you'd have to use a Live CD to get back in and reinstall GRUB since Windows, in the past versions, overwrites the MBR. If you're up for that, there are a lot of resources on how to reinstall GRUB using a Live CD.

Another option is to install a virtual machine, like VirtualBox, and running Windows in there. That's how I run XP for the very few times I need XP (mostly as a test platform when other people need help). As far as I know it works well for just about anything that doesn't require DirectX. Just a thought.

---

### Post by knut100 on 2008-06-24
Okay, then how about win XP? I only want to run photoshop cs3 actually... at least that's what I miss atm.

---

### Post by VChief on 2008-06-25
CS3 should work in the vm without a problem. As far as I know (the only programs I currently have installed in mine are Visual Basic and Visual C++). I'm still pushing that because I think it's a lot easier than having to dual boot. XP will install on FAT32 but according to MS's website, you can only format up to 32GB on setup. You'll also still have the issue of the MBR being overwritten so you'll still need a Live CD handy to reinstall GRUB. 

No guarantee, but I would think you can format that space as FAT32 and Vista will offer to change it to NTFS. But that's above my level. I haven't tried to install Vista. XP fits me rare needs without sucking up a ton of RAM.

---

### Post by rockerphil on 2008-06-25
if i remember correctly you should be able to run Photoshop through Wine without too much hassle thus saving you the hard drive space from installing Windows XP on either a dual-boot system or a VM. to install wine just type this in terminal

sudo apt-get install wine

Wine allows you to run Windows executable files in Linux. so to run a Windows app in your Linux OS just navigate to the directory where the Windows executable is stored using the cd command (works just like Windows DOS, at least with that command) and then type

wine <windowsprogram.exe>

remember to replace <windowsprogram.exe> with the name of the Windows executable without the <>. hope this info helps

---

### Post by VChief on 2008-06-25
> **rockerphil said:**
> if i remember correctly you should be able to run Photoshop through Wine without too much hassle thus saving you the hard drive space from installing Windows XP on either a dual-boot system or a VM. 


Good point. the AppDB on WINE's site has CS3 listed as Bronze. That would definitely be a good alternative to installing Windows.

---

### Post by lazyart on 2008-06-25
Just be prepared to reinstall grub.  Installing Windows after Linux will make the latter unbootable until grub is restored.  Research it now, and keep that live CD handy cuz you'll need it.

---

### Post by knut100 on 2008-06-25
I already have WINE, and use it for uTorrent. But, when I tried to install CS3, nothing happend. I've deleted it, but I guess I'll try again.

Thanks for the useful help so far!

---

### Post by hopelessone on 2008-06-25
Google poured a heap of money into wine to get CS3 working update to the latest WINE by:

[http://ubuntuforums.org/showthread.php?t=795714](http://ubuntuforums.org/showthread.php?t=795714)

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

BTW use "deluge" instead of uTorrent.....

---

### Post by It_Was_Luck on 2008-06-25
> **knut100 said:**
> Wow, great response. 

It worked beatuifully, but now I'm wondering;

If I format it to fat32, then I can use it to install Vista? Because I need Windows for some programs...

For running windows apps you could try Wine 1.0, which has hundreds of Applications that will run at the platinum level, in other words, they have been emulated so darn well you'll think your running these apps on a windows machine.

---

### Post by kansasnoob on 2008-06-25
If you decide to dual boot these guides are simple and have worked well for me:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

They both include instructions for dealing with GRUB after the installation is complete.

---

### Post by Tuxoid on 2008-06-25
wow, thanks. I had a GParted CD, but I didn't know I could resize swap from it.

---

### Post by DanteG on 2009-01-08
Hehehe... Sounds familiar. I did almost the same thing. I partitioned my 60Gb drive in 2 equal partitions for Vista/Ubuntu DualBoot & after installing all applications & updates on Vista I came really close to running out of space on that partition (8.85Gb free) & realized Ubuntu wouldn't be needing 27.9Gb for it to run. Came across a couple of good threads here that helped me decrease the Ubuntu partition & increase Vista's partition. One thing I'd like to add, which might be useful for other people encountering the same issue: In GParted the swap partition needs to be turned off to allow resizing the complete partition. Otherwise GParted will only allow for the Ubuntu partition to be resized.

---

