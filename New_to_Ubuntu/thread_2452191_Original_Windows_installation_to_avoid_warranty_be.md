---
title: "Original Windows installation to avoid warranty being voided"
date: 2020-10-18
forum: New to Ubuntu
---

### Post by kimwh on 2020-10-18
I want to completely wipe out Windows 10 from my brand new Dell laptop (still under warranty) to install Ubuntu.

But in case I have a hardware issue and send it to Dell for repair (after having reinstall W10) they might say the warranty is voided because I have wiped out the original Windows installation and refuse to do anything on it.

To avoid this problem I heard that I have to extract Windows GUID key from my laptop. Download the official W10 recovery image from Dell and add into it the original GUID key. If that's true can you please help to understand how I can do that?

I know that instead I could install Ubuntu alongside Windows in dual boot, but it's not what I'd prefer...

---

### Post by oldfred on 2020-10-18
Some users have posted they remove the Windows HDD and put in a new SSD just for Ubuntu.
Then later if they want to sell system, they just restore Windows drive which then is like new with no user data.
You could do something similar, if that concerned about warranty issues.
If system is broken, you may be able to install or reinstall anything using broken system.

Windows stores its product key inside UEFI. So when installing Windows it automatically finds that key.
[https://support.microsoft.com/en-us/help/10749/windows-10-find-product-key](https://support.microsoft.com/en-us/help/10749/windows-10-find-product-key)

But each vendor has a different image of Windows as it includes the extra drivers required. Those drivers are typically on the vendor's support site. Few vendors now offer a full image and expect users to use the Windows image & install additional drivers as needed.

---

### Post by kimwh on 2020-10-18
Thank you for your quick response oldfred. I appreciate.
I already have a new SSD in my brand new laptop so I don't think I'll buy another one just for that.

For you the Windows product key and the GUID is the same thing?

Don't you think that this: [https://www.dell.com/support/home/en-uk/drivers/osiso/WT64A](https://www.dell.com/support/home/en-uk/drivers/osiso/WT64A) could be a full Windows image?

---

### Post by oldfred on 2020-10-18
Do not know about Dell recovery image.
Most systems have a recovery image as a separate partition on drive. Of course if drive fails that image is worthless.

Product key for Windows is just a code in UEFI.
GUID is a family of codes for partitions. Actually several. There is a unique code for every partition and then a type code to identify the partition.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by kimwh on 2020-10-18
Any idea how I can extract Windows GUID key _**and then incorporate it**_ into the official W10 recovery image from Dell?

---

### Post by QIII on 2020-10-18
The GUID is deliberately hard to extract.  Microsoft wants it that way so that it is difficult to get around their EULA.

There are third party extraction tools, but I would avoid those out of concern for malware.

I don't know for sure about Dell, but there should be a recovery partition on the drive.  It used to be that you could create a "recovery" image, which would use that partition to restore the factory image on the drive.  I'm not sure if that is the case any longer.

If you create a recovery image, leave the recovery partition on your drive (that partition used to be called "D:\" in Microsoft's incorrect terminology calling a partition a "drive".  That would be your first option.

Second option would be to contact Dell and request a DVD of the ***installation*** media for your machine.  That will cost you a small amount.

I don't want to spend your money, but I go with oldfred for your third option -- it's what I do as my first option:  SSDs are fairly inexpensive at about $100 - $150US per TB unless you opt for the top of the line models.  Buy a new one and call it "insurance".  Keep the old device secure and don't mess with it.  If you have problems, pop it back in and see if it is hardware or your Linux installation.  If it's hardware, leave it in and return it for service.  That is the most certain to work and Dell will be none the wiser.

---

### Post by MartyBuntu on 2020-10-18
> **QIII said:**
> 

I don't want to spend your money, but I go with oldfred for your third option -- it's what I do as my first option:  SSDs are fairly inexpensive at about $100 - $150US per TB unless you opt for the top of the line models.  Buy a new one and call it "insurance".  Keep the old device secure and don't mess with it.  If you have problems, pop it back in and see if it is hardware or your Linux installation.  If it's hardware, leave it in and return it for service.  That is the most certain to work and Dell will be none the wiser.


Either buy a new SSD and swap out the drive with Windows, or buy another HDD or external drive to clone the existing installation to.

Either way, you should have another drive for backups...unless you don't place that much value on your data, or time.

---

### Post by Impavidus on 2020-10-18
It doesn't make sense that wiping the original software from a computer voids warranty on the hardware, but swapping the harddrive does not. But then, big enterprises aren't exactly known for being sensible. Swapping the original harddrive out and back in is certainly less detectable.

---

### Post by CelticWarrior on 2020-10-18
You're confusing support requirements with warranty.

Typically, in consumer line of products, only one OS version is supported, the one bundled/preinstalled. Professional, servers and whatnot often have a list of supported OS and then tech support will troubleshoot your issue with any of the supported OS you have installed at the moment.
Installing other OSes does not void the warranty but you're expected to have the supported OS (or OSes) running when you call them for a warranty claim. Furthermore you can reinstall the same original OS as many times you want and for current Windows, as explained already, you don't need any serial number let alone GUID, that would be ridiculous. And you can use the manufacturer's image when there's one or from the recovery partition, preferably, because those include additional drivers, also already explained, or reinstall using the standard Windows image provided directly by Microsoft and then reinstall the drivers. They may at times require you to reinstall the OS and drivers on the call with their instructions if they suspect the problem is software/OS related and not hardware.
This is all there is. You CAN install any other OS, standalone or multi-boot, without affecting the warranty, as long as when you do a warranty claim the troubleshoot must be done with the original OS or, in some cases, with one of the officially supported OS for the given model.

Obviously you won't be able to reinstall if the drive itself failed. In those cases an external diagnostics tool will be used to confirm the hardware issue. Dell have Dell Diags but any of the typical third-party tools are often accepted. They don't care about what's in the failed drive, they'll replace it under warranty, that's all.

---

### Post by metacell on 2020-10-20
> **oldfred said:**
> Some users have posted they remove the Windows HDD and put in a new SSD just for Ubuntu.
Then later if they want to sell system, they just restore Windows drive which then is like new with no user data.
You could do something similar, if that concerned about warranty issues.
If system is broken, you may be able to install or reinstall anything using broken system.

That's a great idea.

If you don't want to spend money on an extra SSD, you can also boot Ubuntu from a USB stick, and save a full image of the hard drive to an external drive.

Then you can restore the image before sending your PC for repairs. If your PC is too broken to boot Ubuntu, you can take out the hard drive and put it in another computer, restore the disk image there, and then put it back.

---

### Post by kimwh on 2020-10-20
> **MartyBuntu said:**
> 
Either way, you should have another drive for backups...unless you don't place that much value on your data, or time.

You're totally right.
I have actually a backup on a HDD... But I'm thinking to subscribe to an online backup service, because I travel a lot and I don't always that HDD with me.

---

### Post by kimwh on 2020-10-20
> **CelticWarrior said:**
> 
[...] you can reinstall the same original OS as many times you want and for current Windows, as explained already, you don't need any serial number, let alone GUID, that would be ridiculous.

I had read that (GUID key, etc) from another forum, but in fact I thought exactly like you!!! 

> **CelticWarrior said:**
> 
You CAN install any other OS, standalone or multi-boot, without  affecting the warranty, as long as when you do a warranty claim the  troubleshoot must be done with the original OS.

That sound so logical. Thank you very much CelticWarrior for sharing your thoughts.

---

### Post by kimwh on 2020-10-20
> **QIII said:**
> The GUID is deliberately hard to extract.  Microsoft wants it that way so that it is difficult to get around their EULA.

There are third party extraction tools, but I would avoid those out of concern for malware.
Then I'll definitely won't follow this path.

> **QIII said:**
> 
[...]  there should be a recovery partition on the drive. It used to be that you could create a "recovery" image, which would use that partition to restore the factory image on the drive.

I had thought about doing something like that but I don't know where is that recovery partition located in the drive.
Can anyone tell me where it can be (see screenshot)?

---

### Post by oldfred on 2020-10-20
The installer does not show labels, it may have a label.
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"

My old Dell from 5 years ago when first booted wanted a Dell recovery DVD, a Windows recovery DVD/flash drive and I made a full image recovery with Macrium.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by kimwh on 2020-10-23
> **oldfred said:**
> The installer does not show labels, it may have a label.
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"


```
NAME        FSTYPE   LABEL                     MOUNTPOINT   SIZE FSUSED MODEL
sda         iso9660  Kubuntu 20.04.1 LTS amd64             14.5G        USB_Flash_Drive
&#9500;&#9472;sda1      iso9660  Kubuntu 20.04.1 LTS amd64 /cdrom       2.4G   2.4G 
&#9500;&#9472;sda2      vfat                                            3.9M        
&#9492;&#9472;sda3      ext4     writable                  /var/crash  12.1G  54.8M 
nvme0n1                                                     477G        PC611 NVMe SK hynix 512GB
&#9500;&#9472;nvme0n1p1 vfat     ESP                                    230M        
&#9500;&#9472;nvme0n1p2                                                 128M        
&#9500;&#9472;nvme0n1p3 ntfs     OS                                   474.3G        
&#9500;&#9472;nvme0n1p4 ntfs     WINRETOOLS                             990M        
&#9492;&#9472;nvme0n1p5 ntfs     DELLSUPPORT                            1.3G
```

The recovery partition seems to be:
&#9500;&#9472;nvme0n1p4 ntfs     WINRETOOLS

Can I delete the rest of *nvme0n1* expect the one above?

Or perhaps keep also:        
&#9492;&#9472;nvme0n1p5 ntfs     DELLSUPPORT

---

### Post by oldfred on 2020-10-23
Both Windows & Ubuntu use the ESP - efi system partition for UEFI install's boot files.
You may want to make ESP slightly larger. Many suggest 300 to 500 as suggested sizes. 
But if only booting Ubuntu it does not have to be larger.

The p2 partition is Windows System Reserved and is unformatted, so often shown as an error in partition tools as they do not like unformatted partitions.
Your p3 is then your Windows main drive. I thought now it also wanted or created another small partition after the main install or is that labeled as Windows recovery?

WinRE recovery partition after main NTFS
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)

---

### Post by kimwh on 2020-10-25
Oldfred, sorry but English  is not my first language and I don't fully understand what you're telling me.

I think I've understood that I should keep: ESP (eventually larger) and also p2
But then, I don't quite understand this:
> **oldfred said:**
> 
Your p3 is then your Windows main drive. **I thought now it also wanted or  created another small partition after the main install or is that  labeled as Windows recovery?**

---

### Post by oldfred on 2020-10-25
I saw a while back that Windows was going to add a small recovery partition after the main install. And that could cause issues.
That may just be the partition you show as recovery.

Windows standard partitions:
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

You only need p2 if using Windows as that is the Windows system reserved as unformatted space for "hidden" serial numbers or other data.

With old BIOS, Windows wrote that info in the space after the MBR and before first partition. That does not exist with gpt. And back then grub also used that space and Windows DRM like flexnet also used it creating conflicts that grub ended up working around.

Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by kimwh on 2020-10-25
> **oldfred said:**
> I saw a while back that Windows was going to add a small recovery partition after the main install.

If you're making reference to p4 & p5, perhaps it's because I made a mistake when I was trying to install Ubuntu for the first time.
I got an Error Code 141 and to overcome that issue I read that I had to disable RAID and instead used AHCI. I did that and it worked. No more error message.
Perhaps  (I think) p2 & p5 has been created when I started to boot again on Windows.

> **oldfred said:**
> You only need p2 if using Windows as that is the Windows system reserved as unformatted space for "hidden" serial numbers or other data.

Ok, so when installing Ubuntu I can erase everything except p2 & ESP partition, correct?

I'll probably get that Error Code 141 again and so I'll have to disable RAID and instead used AHCI... Any objection?

---

### Post by oldfred on 2020-10-25
Linux does not use Windows system reserved, so you can also delete p2.

Only if partitioning in advance for Windows would you then add a system reserved before first NTFS partitions. Windows automatically creates that with its install into unallocated space.

My system allows me to update UEFI by reading an update file in a FAT32 partition. So I like a larger ESP, so I can also use it for updates.
But Ubuntu changed to hide it with settings in fstab(0077). I change to defaults, but I believe they changed settings for security reasons, so may change back in future.

```
14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

```

---

### Post by kimwh on 2020-10-25
**I made a typo error in my previous message. **
> **kimwh said:**
> Perhaps  (I think) _**p2**_ & p5 has been created when I started to boot again on Windows
I meant, _**p4**_ & p5 has been created (I think) when I started to boot again on Windows, after having disabled RAID and used instead AHCI.

> **oldfred said:**
> Linux does not use Windows system reserved, so you can also delete p2.

Ok, so I'll keep ESP partition only, which I'll expand to 500 MB.
You don't have an objection to the fact that I might have to disable RAID and instead use AHCI to install Ubuntu?

---

### Post by oldfred on 2020-10-25
As far as I know the Intel RST/RAID will not work with desktop installer.
Or you have to change to AHCI.

---

### Post by kimwh on 2020-10-26
I tried to make ESP (p1) partition to 500 Mb but it does not work. I got a message error:[I]

GNU Parted cannot resize this partition to this size.
[/I]
Although I had beforehand deleted all unnecessary partitions

Perhaps I don't do it properly. All installation guide I found are quite old. Can you direct me to the right method for manual installation? There must a tutorial somewhere...

---

### Post by oldfred on 2020-10-26
Did you first delete p2? It cannot move another partition to make room?

Or did you have it mounted?
You have to unmount before you can change it.
Or does it need repair/check.

Multiple links in the link in my signature below for many issues.
You can skip the Windows screens if you have removed Windows.
[https://www.tecmint.com/install-ubuntu-alongside-with-windows/](https://www.tecmint.com/install-ubuntu-alongside-with-windows/)
Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

