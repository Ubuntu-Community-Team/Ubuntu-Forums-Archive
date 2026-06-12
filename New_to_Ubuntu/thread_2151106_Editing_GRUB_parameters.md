---
title: "Editing GRUB parameters"
date: 2013-06-03
forum: New to Ubuntu
---

### Post by Zenithex on 2013-06-03
Hi guys,
I had alot of trouble when installing Ubuntu alongisde my Windows 8, so I gave up and just added a second hard drive.
Working great so far, both are surprisingly fast (one of my main worries when I started this).
Currently I am using boot order to choose which one to boot to, but that would be too much of an inconvience for others (brothers) trying to boot into windows. When I tried to boot using GRUB it just gives me an error. Do I have to change it because its on a second hard drive or what do I do?

All help is greatly appreciated!

---

### Post by Bashing-om on 2013-06-03
[COLOR=#000000]Zenithex; Hi !

Dual booting: IMHO, using the grub menu is the "easier" method to choose the system to boot, However
What else one might do is install the respective boot loaders onto the MBR of the respective operating system's harddrive, and then when booting -> in bios set the harddrive to boot the desired operating system.
 I have seen where some prefer the bios boot method.
I am reluctant to open my bios to inadvertent corruption, thus I desire to choose from grub the OS I want to boot.  
[INDENT]
ya gotta do some thinking about your situation, look at what options ya can make available, make up a plan, and put plan into action.
[/INDENT]
[INDENT=3]
no step for a stepper
 [/INDENT]


[/COLOR]

---

### Post by grahammechanical on 2013-06-03
You should know from the start that I do not have any Windows OS. I am not talking from experience but, you need to find out what Ubuntu sees each drive as. Is the Windows drive sda (first sata drive) and the Ubuntu drive sdb (second sata drive)? Let us assume that Windows is on sda and Ubuntu on sdb.

Now make sdb the boot priority and load Ubuntu. Open a terminal and run

```
sudo update-grub
```

and watch the output. Is Windows listed as one of the operating systems? If so we are good to go. Now run

```
sudo grub-install /dev/sdb
```

That will install/re-install Grub into the MBR of sdb and when you reboot you should get a boot menu with an option to load Windows. But you have to make sure that you are installing Grub into the MBR of the hard disk that Ubuntu is on to and not into the hard disk that Windows is on as that will mess with your Windows boot loader.

Notice I am talking about MBR because that is what I am familiar with. I know nothing of EFI boot systems.

Regards.

---

### Post by fantab on 2013-06-04
> **Zenithex said:**
> Hi guys,
I had alot of trouble when installing Ubuntu alongisde my Windows 8, so I gave up and just added a second hard drive.
Working great so far, both are surprisingly fast (one of my main worries when I started this).
Currently I am using boot order to choose which one to boot to, but that would be too much of an inconvience for others (brothers) trying to boot into windows. When I tried to boot using GRUB it just gives me an error. Do I have to change it because its on a second hard drive or what do I do?

All help is greatly appreciated!

What computer do you have desktop or laptop? 
Did Widnows 8 come pre-installed? Or did you installed it yourself?
If you installed it yourself then, is Win8 booting in UEFI or BIOS? 
To boot in UEFI Win8 NEEDS GUID Partition Table. If this is the case, then Ubuntu must also be installed in UEFI with GPT.
If it came pre-installed then it is probably booting in UEFI.

You have give us all the above information. Win8 is a mess and installing Ubuntu alongside it can be messier without following the correct procedure.

---

### Post by Zenithex on 2013-06-04
fantab; 
Thanks for the quick reply!
It is a desktop, Fujitsu Esprimo P400
Windows 7 was pre-installed but I downgraded to Windows 8 about 2 months ago.
Windows 8 is booting in UEFI.

I also would just like to clarify my question as somehow it got lost when I was trying to figure out what to post...
When I boot into my second hdd (Ubuntu) I am presented with GNU GRUB when I select the Ubuntu, with Linux option it boots perfectly into Ubuntu with no problems. When I select the Windows 8(loader (on /dev/sda1) option I get the following message;
error: unkown command "drivemap"
error: invalid EFI file path.
Press any key to continue...
What do I do? I thought it was because of the two separate hdds but how can I edit(if I can) the Windows 8 option to boot into my first hdd (with Windows 8 only).
I am sorry if this makes no sense but this is my first experience with Ubuntu or Linux, or even dual-booting and really with BIOS.
Thanks for the quick responses, all help is appreciated.

---

### Post by fantab on 2013-06-04
If you are **sure** that you have both OS installed and booting in UEFI then you should run, [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair"). It should fix it for you. If have still have booting issues after using Boot-Repair then post the output of 'BootInfo Summary' that Boot-Repairs generates.

---

### Post by Zenithex on 2013-06-04
The output of Boot-Repair;
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

---

### Post by fantab on 2013-06-04
No. Not the output of Boot-Repair. We need to see '**BootInfo Summary**'. It is created by boot-repair when you run 'BootInfo-Summary' and you are given a link to copy. Paste that link here.

---

### Post by Zenithex on 2013-06-04
[http://paste.ubuntu.com/5733013/](http://paste.ubuntu.com/5733013/)

---

### Post by fantab on 2013-06-04
Ubuntu on /dev/sdb is booting in EFI mode and the disk thas GPT table. BUT Windows 8 is not booting in UEFI. it is booting in legacy mode.

You have convert either Ubuntu to non-EFI mode or install Windows in UEFI. When dual-booting Both OS MUST be in either UEFI or Legacy BIOS. 
You decide which one it will be and we can guide you further...

[QUOTE=sudo parted -l]
Model: ATA ST3500413AS (scsi) 
Disk **/dev/sda**: 500GB 
Sector size (logical/physical): 512B/512B 
**Partition Table: msdos  **



Model: ATA WDC WD2500KS-00M (scsi) 
Disk **/dev/sdb**: 250GB 
Sector size (logical/physical): 512B/512B 
**Partition Table: gpt  **

[/QUOTE]

---

### Post by Zenithex on 2013-06-04
Thanks, which one would you recommend  (or the easier if it doesn&#8217;t really matter).
How would you change it to UEFI/Legacy?

---

### Post by Zenithex on 2013-06-04
Thanks, which one would you recommend  (or the easier if it doesn’t really matter).
How would you change it to UEFI/Legacy?

---

### Post by fantab on 2013-06-04
If you have Windows8 64bit and if you ask me, then UEFI is what its going to be. It is new and probably future. So re-install Windows8. 
To boot Win8 in UEFI you need to change the Partition Table from 'msdos' to GUID Partition Table or GPT. With GPT you can have more than 100 Primary partitions, so no more Extended and Logical Partiions. But Windows has to be 64bit. 
To install Windows in UEFI: [http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

Then boot into Ubuntu and 
```
sudo update-grub
```
Restart and boot Windows.

There is a known bug in GRUB which may not let you boot Windows8. To fix this you may need to run [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by Zenithex on 2013-06-04
Thanks for the help!
I will probably use Legacy for Ubuntu as I really don't want to mess with my windows files...
Is there a way to keep my files but change to UEFI?

---

### Post by fantab on 2013-06-04
NO. but if by Windows files you mean your personal data files then you can BACKUP. Windows has to be installed in UEFI/EFI mode AFAIK... however you can searh the web to find out if there is any such way.
I would still 'recommend that you boot Windows in UEFI. Also your partitioning on Win8 Disk looks messy, not that it matters in functitionality. However, if you insist on legacy boot for Ubuntu then....

Ubuntu can boot in 'Legacy' from GPT but for that you have make/create a **BIOS-Boot partition of 5MB**, it should be '**unformatted filesystem**' (meaining don't format it with any file system) and then set '**bios_grub**' flag).

**Or**

You can **delete the Gpt partition table **(be careful this will wipe out your HDD clean, backup your data)** and create new 'msdos' table.**

---

### Post by Zenithex on 2013-06-05
Thanks fantab,
GRUB is working perfectly now!
I did choose the use Legacy over UEFI simply because I didn&#8217;t want to mess with my Windows files, I made a BIOS-boot parttion as you suggested.
Thanks for all your help, was so frustrated and scared I would break my PC.
Thanks
-Zenithex

---

### Post by fantab on 2013-06-05
I understand your apprehensions about messing with Windows files. However, next time when you are forced to reinstall Windows do consider insttalling it in UEFI mode.
Glad you got your computer booting the way you wanted it.

---

