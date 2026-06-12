---
title: "Ubuntu 11.10 new install almost there"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by Joerice50 on 2011-10-31
Ubuntu 11.10 on a NVIDIA GeForce 8200 motherboard 

Hi All

I did fix this with your help in 2009 but then the Ubuntu hard disk crashed so I carried on with Win XP. However, I would like to get Ubuntu working and it’s almost there, so your help is appreciated again.

I installed Ubuntu 11.10 via moving the iso to the same directory as wubi. I had problems on the reboot until I selected the acpi workaround option. This seems to work as I  have now installed the whole package on a new e: drive  but on selecting Ubuntu from the #boot option at the start  Ubuntu boots a little but hangs with a pink to purple screen and no errors displayed! I suspect that its not detecting the SATA drive as there is not much disk activity.

Are there any strings like pci=nomsi all_generic_ide that I need to insert to make it more forgiving or is this all fixed in Ubuntu 11.10?

If I need to insert this string I recall booting from CDROM and adding this instruction to a file, can you please remind me which file and how I get write privileges?

# can anyone suggest how I can extend the display time for this selection display as I have about a second to select Ubuntu before windows boots automatically?

Cheers and thanks in anticipation 

Joe Rice

---

### Post by oldfred on 2011-10-31
Most nVidia systems require nomodeset. You then may need your other settings also, but these show how to add settings to the grub menu. Is this a wubi install? I am not sure what differences that may make.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by Joerice50 on 2011-11-01
Hi Oldfred

Thanks for the info I will try it tonight and let you know how I get on. On a related matter when trying to install Ubuntu back in 2009 I found a solution in this forum at this url see: [http://ubuntuforums.org/showpost.php...&postcount=322](http://ubuntuforums.org/showpost.php...&postcount=322) but this dosent work anymore, can one search by the showpost code =322 and if so how?

---

### Post by oldfred on 2011-11-01
The entry you have was shorten in the display in the forum. It does that and then if you copy it, the copy has the ... , not the full link. You would need the thread also.

But most of the info from 2009 is obsolete. That may have been old grub legacy and did not have the video issues that new installs often have.

---

### Post by Joerice50 on 2011-11-02
Hi Oldfred

Sorry for the delay but I had some problems booting the CRrom so made another copy at a slower write speed and this boots. I included pci=nomsi in the f6 boot option string and this gets me to a working ubuntu desktop. but cannot see the harddrive plus no harddrive mounted

I used the command in terminal sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26932692

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1465127999   732563968+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97c4cc3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   42  SFS


So I have a drive,  just need to find out now how to mount it and edit the grub boot section with pci=nomsi

I will update you on progress as it occurs

Cheers

Joe Rice

---

### Post by oldfred on 2011-11-02
This is one problem.

> /dev/sdb1              63   976768064   488384001   42 [COLOR=Red] SFS[/COLOR]

That says it was converted to dynamic partitions. Or you have encrypted it.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by Joerice50 on 2011-11-06
Hi Oldfred

Well I tried various things to get Ubuntu 11.10 installed including a non wubi approach using an install from the CDROM obviously I needed to use the pci=nomsi command to enable write access to the new hard drive but this also proved to be problematical in that the install would fail through slower and slower plus repeat readings from the CDROM. The computers response would take minutes to react to a mouse click and would eventually hang with no mouse input or video output and constant access lights on the CDrom and the hard drive. My assumption is that these areas of memory were overwritten. 

So I have given up with trying to install Ubuntu and installed puppy linux instead or rather fatdog512 the 64bit version of puppy which worked. I have a few issues to clear up but its working so I will persevere with this version of linux until I gain a bit more expertise.

Thanks for your help, but I think I was just defeated trying to battle through the ubuntu and my oddball hardware incompatibility issues, and I don't know why puppy works when its largely based on Ubuntu! 

Regards

Joe Rice

---

