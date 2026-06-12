---
title: "Both my drive partitions have Ubuntu intalled on them!"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by TheTechyBrit on 2013-04-11
Hi everybody, get prepared to hear from a complete Linux noob...

So, today I installed Ubuntu onto my laptop, which had Windows 8 already installed.
I did as the website says and rather than using the installer I downloaded a 64-bit version of Ubuntu and installed it myself.
I burned the ISO file to a USB stick and successfully installed Ubuntu.
I created a new Partition Table because I wanted to make the partitions myself. Was I supposed to do this? Or use what I had?
I created the following partitions:
[LIST]
[*]200,000MB /home partition for all downloads, apps, etc. (This shows in the about this computer section as 216GB, which is about half my available storage according to Windows)
[*]500MB of swap space. Do I need more? I have 6GB of RAM.
[*]20GB / (root) partition
[*]100MB EFI boot partition
[*]100MB BIOS boot partition (I don't have UEFI BIOS)
[/LIST]
I think that's all.
So just now, I checked in my BIOS to see if I could boot Windows and Ubuntu was installed on both partitions.

Please help. Thanks in advance.
-

---

### Post by Cheesemill on 2013-04-11
> **TheTechyBrit said:**
> 
I created a new Partition Table because I wanted to make the partitions myself. Was I supposed to do this? Or use what I had?

Creating a new partition table wipes all of the information that describes where all of the files live on your hard drive.

If you wanted to keep any of the data that you already had then your only option is to use testdisk to try and recover the data that hasn't been overwritten.

---

### Post by TheTechyBrit on 2013-04-11
Oh...
Well thanks for informing me.
Maybe I'll wipe my HDD and start fresh.
Again, thanks.

---

### Post by oldfred on 2013-04-11
If you had Windows 8 pre-installed then you do have UEFI. Also many later Windows 7 systems were installed in BIOS mode but system had UEFI, just in BIOS mode. If Windows is in BIOS mode, you really need to install Ubuntu in BIOS, but if Windows is UEFI then Ubuntu needs to be UEFI. And how you boot installer either UEFI or BIOS is how it installs.

Windows only boots from UEFI with gpt partitioning, and you only can have one efi partition per hard drive with gpt. If MBR you do not have efi partition.

---

### Post by TheTechyBrit on 2013-04-11
So...
I wanted to start fresh and try again.
Could I reinstall Windows without my disk?
Aaand... I don't think I have my activation code, since I got this laptop for Christmas and someone else installed the OS for me.y.
-Thanks for your help. Sorry I'm such a newby. :|

---

### Post by oldfred on 2013-04-11
You either have Windows product key on bottom of drive if older system or if new UEFI:

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

How is drive partitioned? 
Do you want BIOS or UEFI? Many understand BIOS with MBR partitioning as that is what has been used since the first PC with hard drive. But UEFI is the new way. Since it has lots of issues with some systems and both Windows & Linux are learning how to work around the bugs, it is not as easy to install.

With UEFI and gpt partitioning Windows has very specific requirements.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by TheTechyBrit on 2013-04-12
My laptop's motherboard does not support UEFI, the only 'form' of EUFI is the windows recovery options. And this only takes me through some menu screens, to BIOS.

---

### Post by oldfred on 2013-04-12
Post this from terminal with Ubuntu live installer.

       sudo parted /dev/sda unit s print

If it says gpt and has an efi partition then you have UEFI. IF it says msdos then you are BIOS.

Although Ubuntu will boot from gpt partitioned drive in BIOS mode, Windows will only boot from gpt with UEFI.

---

### Post by TheTechyBrit on 2013-04-12
It says gpt but no efi partition. Also, I've been having trouble with GRUB, not sure if it's installed. There is no UI or command line, etc. for me to choose my boot options. I think this shows up even if you do only have one OS.

---

### Post by oldfred on 2013-04-12
Ubuntu will install in BIOS mode on gpt partitioned drives. You need a tiny 1MB unformatted partition with the bios_grub flag. Boot-Repair can convert a BIOS Ubuntu install to UEFI if you have the efi partition.
But if installing in UEFI mode you have to have the efi partition. UEFI spec says it should be first, but Windows usually makes it second after its recovery/repair partition.

Windows will only boot from gpt partitioned drives with UEFI and the efi partition is then required.

If you only have Ubuntu installed, you normally do not get grub menu. From BIOS if you hold shift key, then you should get grub menu.

---

