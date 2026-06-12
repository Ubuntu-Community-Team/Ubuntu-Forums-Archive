---
title: "Grub doesn't offer Windows 10 after Ubuntu 18.04 LTS dual boot install"
date: 2018-08-01
forum: New to Ubuntu
---

### Post by sharb on 2018-08-01
Hello,  I am new to PC (from Mac), so very inexperienced here.

I was trying to install ubuntu 18.04 lts to dual boot with windows 10 on my new Dell latitutde 5490 with windows installed.  After installing, the grub menu only offers ubuntu, advanced options for ubuntu, windows boot manager (on /dev/nvme0n1p2), System setup.  
My install went as follows: partitioned my windows hard drive to 200gb 'unallocated' and unformatted by shrinking in windows disk management; turned off fast start; turned off secure boot; changed RAID to ACHI. Used Rufus to create a bootable flash drive using GUID/GTP; UEFI, FAT32, cluster size 32gb), amd64. I installed Ubuntu into 'free space' nvme01n1p2 (the only option available) and created subpartitions for root (30gb), boot (500mb), swap (6gb), home (remaining 163.5gb), EXT4 journalling.  Upon restarting, the grub menu only offers ubuntu as above.
 
 F2 at dell screen tells me &#8216;restart&#8217; or repair &#8211; how? Restart returns to Ubuntu only grub and F2 again returns to PC with errors page.

I used gparted to get partition info (see pic). NB: tried to paste pic in but wouldn't post, so you can probs see info in boot repair link.

I used boot-repair to do a diagnostic: [http://paste.ubuntu.com/p/V7kr8zdrRH/](http://paste.ubuntu.com/p/V7kr8zdrRH/)
Then did a boot-repair: [http://paste.ubuntu.com/p/65kkcyctKV/](http://paste.ubuntu.com/p/65kkcyctKV/)
I am now supposed to make my BIOS boot on nvme0n1p2/EFI/ubuntu/shimx64.efi file!
 
 Grub offers many things, but still no Windows.

So, can you tell if my Windows system is still OK?
How to I make BIOS boot on nvme0n1p2/EFI/ubuntu/shimx64.efi file! ?
Should i just uninstall and start again? how?

Thank you.

---

### Post by oldfred on 2018-08-01
It shows default boot correctly.
F10 or f12 should give you UEFI boot menu, but it will only show descriptions. Several are the same, see this to tell them apart:
see this in report or from terminal in live installer.
sudo efibootmgr -v

You also show an old Windows entry 0000 that uses a GUID that does not now exist.
One Windows entry uses the fallback or hard drive entry and one is typical UEFI boot entry.
Boot-Repair normally copies /EFI/Boot/bootx64.efi which is the hard drive entry and makes it be an Ubuntu boot entry.
So one Windows entry 0002 will boot Ubuntu and one should boot Windows 0003.

Looks like you made most of the changes required for Dell.
Did you also update UEFI form Dell to latest version, or check that yours is also the latest?
Many found that solved issues.
Also some have had to update SSD firmware, but most of those seemed to be Samsung?

---

### Post by Geoffrey_Arndt on 2018-08-02
Some who are more familiar with dual-boot than I will be responding to your pastebin file . . . BUT . . . as temp work-around to allow Windows access . . . your PC should have a Function key that invokes the special UEFI Boot Menu.    This menu displays all OS's including those on portable attached devices (like usb flash-sticks or usb SSD's), and the user can scroll down to the option they want to boot.   On HP's, that Function key is F9, opon Acers, it's F12.   Since I've never had a Dell, I'm not sure what it is for that make.

**Edit**:   Looks like Fred beat me again (got to improve my typing speed!)

---

### Post by sharb on 2018-08-02
Thank you oldfred and Geoffrey,

BIOS is current for Dell 5490 (1.3.2), Acces UEFI boot meny by F12 with Dell. I ran a BIOS diagnostic and all ok.

UEFI boot menu:
 Ubuntu
 Windows Boot Manager
 Windows Boot Manager

which I assume corresponds to the order from efibootmgr -v as follows:

So i went into sud efibootmgr -v and saw the 4 boot options and boot order: 0001, 0003, 0002
0000 Windows HD(1,....0x145000)/File\EFI\Microsoft\Boot\bootmgfw.efi) as you said is redundant
0001 ubuntu (\EFI\ubuntu\shimx64.efi)
0002 Windows Boot Manager File (\EFI\Boot\bootx64.efi)
0003 Windows Boot Manager HD(2,....0x100000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)

Then on the Ubuntu grub i selected Windows UEFI bootmgfw.efi (since it resembled 0003) and that didn't work. and then I tried other options offered which also didn't work.

Should I change the Windows Boot Manager Order in settings to 1 2 3?

In the BIOS events log I had multiple messages Alert? Firmware update is failed. - maybe from when I get to the blue PC page and it restarts and fails?

Another message I just got from ubuntu grub was:
Failed to open \EFI\Boot\grubx64.efi - Not Found
Failed to load image \EFI\Boot\grubx64.efi: Not Found
start_image() returned Not Found

An option on the blue PC troubleshooting page is to reinstall Windows - will these upset Ubuntu install?

---

### Post by oldfred on 2018-08-02
Any entry with Windows boot manager should boot Windows directly.
       \EFI\Microsoft\Boot\bootmgfw.efi 
You should not need to reinstall Windows but if above does not boot then you  need to run Windows repairs. You should have made a Windows repair disk? My Dell wanted Dell backup, Windows backup & I made a full image backup.

 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

    
I have seen others with the /EFI/Boot/grubx64.efi error. That file should not be required, but it may be booting shimx64.efi as /EFI/Boot/bootx64.efi that Boot-Repair copies. Then I thought shim looked for all the rest of its needed files in /EFI/ubuntu.
But try copying grubx64.efi to /EFI/Boot.

---

### Post by sharb on 2018-08-02
Thanks oldfred.

I tried F12 at splash screen, USB option, which gave me 4 further options:
1. Continue (exit and continue to windows 10) - Selecting 'continue' took me straight to ubuntu.

2. use a device (USB/network or Windows recovery DVD) - offered
a. ubuntu,
b. windows boot manager - took me to keyboard options, then looped back to 4 options above,
c. UEFI USB Disk 3.0 PMAP, partition 1 - back to keyboard options and looped back to 4 options above. 

3. troubleshoot (reset)

4. Turn off.

Also, looking at Dell instructions, I was also supposed to enable 'UEFI network stack' and I left 'enable w/PXE' on (option also to just enable UEFI network stack).  Then I ran Boot Repair again for this report [http://paste.ubuntu.com/p/76sWzshQj2](http://paste.ubuntu.com/p/76sWzshQj2)
No changes - grub still doesn't show Windows 10 and options are the same.
You'll notice that the boot order has more options, and has also changed to 0001, 0002, 0003 - so that didn't make any difference.

I'll try the grub repair first - Can you please give me REALLY basic instructions to copy grubx64.efi to /EFI/Boot? (like, go to terminal window and type ....)

I did make an image backup, but before I shrunk the partition. I assume this will override ubuntu partition and installation, so i'll just start from scratch.

thanks again.

---

### Post by oldfred on 2018-08-02
I think when copying files in ESP, I use gui (Nautilus) from live installer.

This should work from terminal:
       sudo cp /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/Boot

---

### Post by sharb on 2018-08-03
Sorry oldfred that didn't work.  I've found the pathways you were talking about now with all of the folders, etc.  I used the terminal window to make the copy, which appears in the folder, but no change to the way the computer works.
By the way, can you just click and drag the files to other folders as an option?

So i can see that
grubx64 as well as shimx64.efi are now in boot/efi/EFI/ubuntu
bootmgfw.efi is in boot/efi/EFI/Microsoft/Boot
bootx64.efi and grubx64.efi are in boot/efi/EFI/Boot
bootx64.efi is in boot/efi/Boot with bootx64.efi.grb (which appears to be blank)

also FYI, when i choose from the grub menu
'windows uefi bootmgfw.efi' the reboo opens the blue windows screen with the messages preparing automatic repair, diagnosing pc which then fails to 'restart' option.
'windows boot uefi fbx64.ef' it loops quickly back to the grub menu
'windows boot manager ( on /dev/nvme0n1p2)' takes me to the 'pc ran into a problem and needs to restart - 'inaccessible boot device'

Anything else I could try?

---

### Post by oldfred on 2018-08-03
This should be your Windows boot files:
bootmgfw.efi is in boot/efi/EFI/Microsoft/Boot

And then that should be used by 
       Boot0003* Windows Boot Manager    HD(2,GPT,[COLOR=#ff0000]18ca9b6f-234e-4150-a0a7-205ceb44b483[/COLOR],0x96800,0x100000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C

Note that report showed another Windows entry 0000 with a different GUID, the long number 18ca.... is the correct one.
GUID is same as PartUUID, UEFI uses GUID/PartUUID to know which ESP to use.
      
 /dev/nvme0n1p2: UUID="C297-2FF0" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="[COLOR=#ff0000]18ca9b6f-234e-4150-a0a7-205ceb44b483[/COLOR]" 
    
You can also see that with this which is what the Boot-Repair shows.
       to see GUID/partUUID for each partition, post with code tags to preserve formatting:
lsblk -o +PARTUUID 

Grub only boots working Windows, so if grub will not boot Windows you have to boot from UEFI and may need f8 to get into its internal repair console. Otherwise you then need your Windows repair/recovery flash drive. You do have that for emergencies?
      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by sharb on 2018-08-03
Holy cow batman.  This morning I selected Windows Boot Manager (on /dev/nvme0n1p2) at grub and was taken to the blue PC startup screen saying it was doing repairs, then to the "Automatic Repair" screen to Restart and it actually RESTARTED!!!!  (I suppose it finally worked out the right repair.)
I am now in windows making another recovery drive and too scared to actually restart my computer.
So I suppose this is now solved.  Thanks oldfred you've been very patient and taught me much.

---

