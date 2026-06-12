---
title: "GRUB2 menu not appearing on startup"
date: 2016-03-23
forum: New to Ubuntu
---

### Post by madnessman on 2016-03-23
Hi, I'm trying to turn my Ubuntu only laptop (Acer V7) into an Ubuntu/Win 10 dual boot system. I made a Win 10 bootable USB which wasn't recognized by my BIOS as a bootable device. So, I started to make a bootable partition as per [this guide]("https://askubuntu.com/questions/599746/how-do-i-burn-the-windows-10-iso-to-a-usb") when I realized that I wasn't seeing the GRUB 2 menu even after I changed GRUB_HIDDEN_TIMEOUT to 10. What I do see is a blank purple screen for a few seconds before Ubuntu launches. I'm sure I'm probably missing something obvious but I can't figure out what I'm doing wrong. Thanks in advance for your help! My laptop runs on UEFI & GPT.

Boot Info: [http://pastebin.com/VTvMfqCT](http://pastebin.com/VTvMfqCT)

[LIST]
[*]sda1 - EFI boot partition
[*]sda2 - ubuntu /
[*]sda3 - ubuntu /home
[*]sda4 - ubuntu swap
[*]sda5 - empty NTFS for win 10
[*]sdb1 - win 10 installer (internal ssd)
[*]sdc1 - win 10 installer (usb drive)
[/LIST]

Is this related to the problem?
```
Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    25823696 of the same hard drive for core.img, but core.img can not be 
    found at this location.
```

---

### Post by grahammechanical on 2016-03-23
If Ubuntu is the only OS on the machine we do not see a Grub boot menu. It is still there but there is no need to display it. If you have not updated grub.cfg then as far as Grub knows there is still only one OS on the machine.

```
sudo update-grub
```

Watch the printout to screen. What are the listed boot options. You will need to run that command once Windows 10 is installed to put the Windows 10 boot loader into the Grub boot menu. That is after you have re-installed Grub. The Windows installation process will most likely over-write the Ubuntu boot loader.

You might find what the Grub manual says in relation to this subject useful.

> &#8216;GRUB_TIMEOUT&#8217;

Boot the default entry this many seconds after the menu is displayed, unless
a key is pressed. The default is &#8216;5&#8217;. Set to &#8216;0&#8217; to boot immediately without
displaying the menu, or to &#8216;-1&#8217; to wait indefinitely.

&#8216;GRUB_HIDDEN_TIMEOUT&#8217;

Wait this many seconds for a key to be pressed before displaying the menu.
If no key is pressed during that time, display the menu for the number of
seconds specified in GRUB TIMEOUT before booting the default entry. We
expect that most people who use GRUB HIDDEN TIMEOUT will want to
have GRUB TIMEOUT set to &#8216;0&#8217; so that the menu is not displayed at all
unless a key is pressed. Unset by default.


If GRUB_TIMEOUT is set to '0' and I guess that it is, then that is the reason that GRUB_HIDDEN_TIMEOUT is having no effect.

Regards.

---

### Post by yancek on 2016-03-23
> 
Is this related to the problem?

Being unable to find the core.img file means you won't be able to boot.  It looks for it at the sector mentioned in the output you posted and it isn't there.  I'm not sure why it isn't there as there is nothing in the instructions from the link you posted that would require you to move it.  In Ubuntu 14.04, the core.img file should be in the /boot/grub/i386-pc directory.  Mount sda2 from a Live CD and take a look to see where it is if anywhere.  

The instructions on the link tell you to put the extracted folder/files from the windows iso on the ntfs partition you want, sdb1 or sdc1.  This partition needs to be formatted ntfs and needs to be marked as active/bootable and then you simply put an entry in the grub.cfg file of your Ubuntu install, save the changes.  Do not run update-grub.  You could also put the entry in the /etc/grub.d/40_custom file and do run update-grub.

---

### Post by oldfred on 2016-03-23
If system is UEFI, then probably better to use UEFI to boot.
And best to have all installed systems in UEFI boot mode.
UEFI & BIOS are not compatible, but you should be able to boot Ubuntu in BIOS and Windows in UEFI with gpt partitioned drive, but only from UEFI boot menu, not grub. Once you start booting in one mode you cannot switch.

With gpt and BIOS boot grub has to have the 1 or 2MB unformatted partition with the bios_grub flag for grub2 to correctly install. That is where the core.img is stored when using gpt.
But on gpt partitioned drives Windows will only boot in UEFI boot mode, not BIOS.
And Windows with BIOS has to have MBR(msdos) partitioning. 
Windows will either not install or totally erase drive if installing in wrong boot mode.
Both Windows & Ubuntu install in UEFI or BIOS based on how you boot install media.

Windows in UEFI mode needs several partitions:
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Some other Acer:

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by madnessman on 2016-03-23
> **grahammechanical said:**
> If Ubuntu is the only OS on the machine we do not see a Grub boot menu. It is still there but there is no need to display it. If you have not updated grub.cfg then as far as Grub knows there is still only one OS on the machine.

```
sudo update-grub
```

Watch the printout to screen. What are the listed boot options. You will need to run that command once Windows 10 is installed to put the Windows 10 boot loader into the Grub boot menu. That is after you have re-installed Grub. The Windows installation process will most likely over-write the Ubuntu boot loader.

You might find what the Grub manual says in relation to this subject useful.



If GRUB_TIMEOUT is set to '0' and I guess that it is, then that is the reason that GRUB_HIDDEN_TIMEOUT is having no effect.

Regards.

I went back and updated GRUB_TIMEOUT to '5' and updated grub. Here's the output. I still see a blank purple screen (clicking buttons does nothing) before Ubuntu boots.

```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Adding boot menu entry for EFI firmware configuration
done
```

> **yancek said:**
> Being unable to find the core.img file means you won't be able to boot.  It looks for it at the sector mentioned in the output you posted and it isn't there.  I'm not sure why it isn't there as there is nothing in the instructions from the link you posted that would require you to move it.  In Ubuntu 14.04, the core.img file should be in the /boot/grub/i386-pc directory.  Mount sda2 from a Live CD and take a look to see where it is if anywhere.

Huh it's strange that I'm getting that error. I found core.img in the /boot/grub/x86_64-efi folder (using 64 bit). 

> **yancek said:**
> The instructions on the link tell you to put the extracted folder/files from the windows iso on the ntfs partition you want, sdb1 or sdc1.  This partition needs to be formatted ntfs and needs to be marked as active/bootable and then you simply put an entry in the grub.cfg file of your Ubuntu install, save the changes.  Do not run update-grub.  You could also put the entry in the /etc/grub.d/40_custom file and do run update-grub.

I did that but I'm still only seeing a blank purple screen. Here's an updated boot repair status log: [http://paste.ubuntu.com/15481624/](http://paste.ubuntu.com/15481624/). 

```
=================== User settings
The settings chosen by the user will not act on the boot.

```

This probably has something to do with it right?

> **oldfred said:**
> 
With gpt and BIOS boot grub has to have the 1 or 2MB unformatted partition with the bios_grub flag for grub2 to correctly install. That is where the core.img is stored when using gpt.
But on gpt partitioned drives Windows will only boot in UEFI boot mode, not BIOS.
And Windows with BIOS has to have MBR(msdos) partitioning. 
Windows will either not install or totally erase drive if installing in wrong boot mode.
Both Windows & Ubuntu install in UEFI or BIOS based on how you boot install media.


To be honest, installing Windows alongside an existing Ubuntu installation is starting to sound like it's beyond me. I don't mind losing all my data so would it be a better strategy to just wipe my drive, install Windows 10, then install Ubuntu? If only I could get this bootable win 10 USB working!

---

### Post by oldfred on 2016-03-23
Are you still in BIOS boot mode or UEFI boot mode.
Best to always boot in UEFI mode, both hard drive & flash drives.

If still BIOS, did you add the bios_grub partition and reinstall grub?
Or if you want UEFI you must have the ESP - efi system partition which is a FAT32 formatted partition with the boot flag.
And Acer in UEFI mode requires you to set trust in UEFI for grub boot files, as posted in links above.

If you have correct partitions for gpt, either bios_grub or ESP, then Boot-Repair can reinstall grub for either BIOS or UEFI.
I typically manually partition and add both ESP & bios_grub, so I can install either (or both) grub.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

