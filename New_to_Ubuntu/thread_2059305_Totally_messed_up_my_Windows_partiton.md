---
title: "Totally messed up my Windows partiton"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by CraigD92 on 2012-09-17
Hi all, please bare with me. I am quite new to Linux and will try to explain my problem as well as I can.
 
I recently got a new laptop and wanted to install Ubuntu on it after enjoying so much on my old laptop. I installed it via USB and everything went fine, until I tried booting into Windows 7 from the Grub menu. I got an error message regarding an incorrect EFI path. After a bit of searching I found out that the Boot Repair programme should be able to fix it. So I ran that in Ubuntu and it created 3 new options on the Grub menu, two of which allowed me to boot into Windows.

However, Windows froze up earlier today and I thought I had no option but to hold the power button and reset. When I tried to boot into Windows again I was met with a "Boot into Windows Normally" or "Repair Start Up" option. I tried starting Windows normally but it just hung at the "Starting Windows" screen. So I tried to repair, which sent me into an Asus repair page, but I was met with a massive "ERROR" logo in red letters. 

I then got a grub error message. So I reinstalled Ubuntu and ran the Repair Boot programme again so that I could access Windows. I am still getting the exact same problem.

I do not have a Windows recovery DVD because the laptop is only a few days old. Also, it does not have a disk drive (it is an Asus X501A). I am now completely unable to access my Windows partition. I am wondering if any of you guys would be able to suggest something I could do or help me?

I have downloaded a Windows recovery ISO to copy to a USB, though I'm not sure if that will help.

---

### Post by heyandy889 on 2012-09-17
> I have downloaded a Windows recovery ISO to copy to a USB, though I'm not sure if that will help.If your laptop can boot from USB (access options in BIOS, usually something like F12 while computer is booting), then maybe the Windows recovery tool can help you. This might destroy any GRUB settings you had, and possibly the Ubuntu partitions as well.

> I am now completely unable to access my Windows partition. I am  wondering if any of you guys would be able to suggest something I could  do or help me?I would try a live CD. You probably used a live CD, or a live USB, to install Ubuntu. Rather than selecting "install Ubuntu," you just select "Try Ubuntu" to run as a live distro. Then, go into any files folder, find the "Computer" option. This will let you see the other partitions. You should be able to dig through the Windows folders and copy whatever you want to an external hard drive, or send something via email, FTP, scp, something like that. 

I don't know if a "fix" in the current state is possible. In general, you want to install Windows first because it has this little partition at the "front" of the disc. edit: also, because GRUB supports multiple operating systems, and I don't think the Windows bootloader will support multiple OSs.

| random windows partition | regular windows partion | other hard disk space |

and you can put Ubuntu and its swap partition in your other hard disk space. 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/Partitioning%20issues]("https://help.ubuntu.com/community/Partitioning%20issues")

Also I think Nixie Pixel has a good video about partitioning. Godspeed Craig, and good luck.

---

### Post by oldfred on 2012-09-17
You should have a repairCD or USB or liveCD for the current version of every system you have installed. 

We used to have a site that offered free Windows repairCD ISO. But they now charge $10 when you can make it yourself. But now you need another system with the same 64bit Windows to make the CD.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Be sure to boot Windows in efi mode, and Ubuntu in efi mode as once system is efi booting in MBR mode will mess it up.

---

### Post by CraigD92 on 2012-09-18
Hi, thanks for the tips. I made a Windows Recovery USB with an ISO I found, but it was not compatible with my set up.  I am now stuck as I don't know where to find a recovery image that is compatible with my hardware (Asus X501A).
I would have made a recovery image in due course but the laptop is only a few days old. Is there somewhere else I can find a compatible Windows Repair ISO for free? Or is there a way I can make the recovery partition accessible with Boot Repair? (It is currently inaccessible because of the EFI path problem - edit: here is the URL from my Boot Repair [http://paste.ubuntu.com/1213172/](http://paste.ubuntu.com/1213172/)) 

If none of this is possible, would it be okay to do a clean install of Windows with an ISO from here [http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/) ? I am not worried about losing data from my hard drive as this is a new laptop.

---

### Post by irv on 2012-09-18
This is just a thought. If you have a hidden partition where the recovery for windows is residing it maybe possible to hit a key or combination of keys to boot into the hidden partition to restore your Windows. Check any instruction you might have received with the computer. You might check online at the manufactures website. Just somethings I thought of after reading your posts.

---

### Post by CraigD92 on 2012-09-18
> **irv said:**
> This is just a thought. If you have a hidden partition where the recovery for windows is residing it maybe possible to hit a key or combination of keys to boot into the hidden partition to restore your Windows. Check any instruction you might have received with the computer. You might check online at the manufactures website. Just somethings I thought of after reading your posts.

Yes, I read in the manual that you need to hit F9 in order to get into recovery. However, when I launch Windows 7 in grub, it jumps straight to the "Windows Error Recovery" page, whether I hit F9 or not. From here I can either select "Start Windows Normally", which just hangs at the "Starting Windows" logo, or the alternative option, which then sends me to "Asus Preload Wizard" (not the standard recovery I've seen in normal Windows 7 installations). There are only 3 options here: Recover Windows to first partition only, Recover Windows to entire HD and Recover windows entire HD with two partitons. On every option, it begins to run some commands in a terminal, then goes to a white page with a huge red "ERORR" sign.

---

### Post by oldfred on 2012-09-18
Usually the vendor recovery are just images of the hard drive as purchased. Since you have modified partitions then it may have issues as it expects the standard partitions and sizes?

A new install of Windows from the download will not work with your serial number. You would have to purchase a new serial number (Buy Windows again). 

Asus should be able to support you. Then may have to send new install set of DVDs and may charge you a nominal fee for that.

They may have changed to the new UEFI, but the tools to repair the efi partitions are not up to date?

Just do not tell them you installed another system. Just state that it crashed and will not repair like it should.

---

### Post by irv on 2012-09-18
I believe oldfred is right on this one. But what you said about trying to press F9 after the grub loads is to late. As soon as you turn the computer on you should be hitting the F9 even before the grub. If this doesn't work than you will have to do what oldfred posted. Windows recovery always run before boot up.

---

### Post by CraigD92 on 2012-09-18
> **oldfred said:**
> Usually the vendor recovery are just images of the hard drive as purchased. Since you have modified partitions then it may have issues as it expects the standard partitions and sizes?

A new install of Windows from the download will not work with your serial number. You would have to purchase a new serial number (Buy Windows again). 

Asus should be able to support you. Then may have to send new install set of DVDs and may charge you a nominal fee for that.

They may have changed to the new UEFI, but the tools to repair the efi partitions are not up to date?

Just do not tell them you installed another system. Just state that it crashed and will not repair like it should.

Okay, I will contact Asus and just tell them that it won't repair. Hopefully they won't ask me to return the laptop to the store.

---

### Post by black veils on 2012-09-18
there is a chance if you boot a ubuntu live usb, choose the try option, then open gparted, swap-off the swap partition if necessary by right-clicking it, then delete the partitions which are ext4 and swap by right-clicking them, click apply. 

shutdown, switch on, press F9 repeatedly, and try Windows recovery again.

---

### Post by linuxvstheworld on 2012-09-18
> **black veils said:**
> there is a chance if you boot a ubuntu live usb, choose the try option, then open gparted, swap-off the swap partition if necessary, then delete the partitions which are ext4 and swap, click apply. 

shutdown, switch on, press F9 repeatedly, and try Windows recovery again.

Holy crap, I always wondered how to mess with partitions via Ubuntu, I know I just barged in for no reason on this thread.............. but wow that's simpler than using commands.....

---

### Post by black veils on 2012-09-18
> **linuxvstheworld said:**
> Holy crap, I always wondered how to mess with partitions via Ubuntu, I know I just barged in for no reason on this thread.............. but wow that's simpler than using commands.....

ha well it would mess the bootloader, and be a problem for someone wanting a functional bootloader! the boot-repair tool would be useful in such a situation. but this is an attempt to recover Windows only.

---

### Post by CraigD92 on 2012-09-18
> **black veils said:**
> there is a chance if you boot a ubuntu live usb, choose the try option, then open gparted, swap-off the swap partition if necessary by right-clicking it, then delete the partitions which are ext4 and swap by right-clicking them, click apply. 

shutdown, switch on, press F9 repeatedly, and try Windows recovery again.

Just tried this but all that appears on start is grub rescue.

---

### Post by black veils on 2012-09-18
seems like the windows file system may have got corrupted. there should be some fancy stuff you can do from live usb/cd to attempt recovery of that, then boot-repair again (or an equivalent boot-loader fix).

i think help will be on the way..

---

### Post by oldfred on 2012-09-18
The grub2 menu entry is a chainload to the Windows efi loader. But maybe using the UEFI menu to boot gives a different result or an added choice on repair?

Did you change any UEFI settings?

---

### Post by CraigD92 on 2012-09-18
> **oldfred said:**
> The grub2 menu entry is a chainload to the Windows efi loader. But maybe using the UEFI menu to boot gives a different result or an added choice on repair?

Did you change any UEFI settings?

Not intentionally - I wouldn't know how to.

---

### Post by oldfred on 2012-09-18
See if going into UEFI/BIOS and look at its menu. It may offer something.

Every vendor has different UEFI implementations. But one user said this, so there may be other options? Look for a repair or something else in the Windows folder.

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


---

### Post by CraigD92 on 2012-09-18
> **oldfred said:**
> See if going into UEFI/BIOS and look at its menu. It may offer something.

Every vendor has different UEFI implementations. But one user said this, so there may be other options? Look for a repair or something else in the Windows folder.

In the BIOS there is a "Boot" section which allows for changing boot configuration. The only option though is "Launch PXE OpROM". Not sure what this does. There's also boot option priorities, Network Device BBS Priorities and add new boot option. 

In the Advanced section of BIOS, there is Start Easy Flash but nothing else which appears of interest. 

I am not sure what you mean by "the Windows folder"?

Also, when I go to add new boot option, I have to manually type the 'Add boot option' and 'path for boot option', but I am not sure what to type.

---

### Post by oldfred on 2012-09-18
Many UEFI implementations only have a bit on UEFI but once you get into it, it then offers some more options. It has a limited file capability as it reads the FAT32 partition to load the efi boot files. Where BIOS only knows to jump to the MBR to boot.

I was hoping you might have another efi file in the efi partition to boot into the recovery mode. Grub does not add the additional Windows settings correctly and boot repair only adds the ones needed to boot Windows directly. If recovery is just from BCD then it is only after you start to boot Windows, which you already have issues with.

---

### Post by CraigD92 on 2012-09-19
I am now trying to copy a Windows iso to USB. I have downloaded WinUSB for Ubuntu, however, when I try to copy to iso to my USB stick, I get the following error.

Installation failed !
Exit code: 512
Log:
Formating device...
Mounting...
mount: warning: /media/winusb_iso_1348076374_8267 seems to be mounted read-only.
Copying...
cp: reading `./boot/en-us/bootsect.exe.mui': Input/output error
cp: failed to extend `/media/winusb_target_1348076374_8267/./boot/en-us/bootsect.exe.mui': Input/output error
Error occured !
Syncing...
Cleaning...
/usr/bin/winusb: line 78:  8849 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Umounting and removing '/media/winusb_iso_1348076374_8267'...
Umounting and removing '/media/winusb_target_1348076374_8267'...



Anyone know what this means or how to fix it?

---

### Post by oldfred on 2012-09-19
If it is a Windows program and .exe then it will not work in Ubuntu. I think I have seen some try from wubi but never seen it work.

I had downloaded the Windows 7 repaircd when it was free. But never could get it to correctly install to a USB directly from Ubuntu. But I wrote/burned it to a CD and then from the CD was able to copy to a flash drive using the Windows commands from the booted CD.

---

### Post by mips on 2012-09-19
> **oldfred said:**
> If it is a Windows program and .exe then it will not work in Ubuntu.

It's a linux app to write Win7 iso images to usb from linux.

The OP might try wanna try wiping all partitions on the usb stick with gparted, unmount it and then try writing to it.

---

### Post by CraigD92 on 2012-09-19
> **mips said:**
> It's a linux app to write Win7 iso images to usb from linux.

The OP might try wanna try wiping all partitions on the usb stick with gparted, unmount it and then try writing to it.

I'll try that now. Thanks.

---

### Post by CraigD92 on 2012-09-21
Just to let you guys know - I found out that the ISO I tried to put on a USB was corrupted. So I redownloaded it, set the USB drive to NTFS,copied the ISO using Unetbootin and am now successfully running a Windows 7 and Ubuntu dual-boot.

Thanks for all your help.

---

### Post by irv on 2012-09-21
Why not mark this one solved.
[ATTACH]224504[/ATTACH]

---

