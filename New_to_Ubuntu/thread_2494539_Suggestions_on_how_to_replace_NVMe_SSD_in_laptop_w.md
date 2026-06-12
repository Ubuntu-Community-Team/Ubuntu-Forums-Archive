---
title: "Suggestions on how to replace NVMe SSD in laptop with larger"
date: 2024-01-19
forum: New to Ubuntu
---

### Post by cwmoser on 2024-01-19
Looking for suggestions on how I can replace my 256GB NVMe SSD in my laptop with a larger NVMe
and transfer my Ubuntu OS and /home to the new NVMe.

I really want to save my OS root partition rather than reload the Ubuntu 22.04.
I have all my /home data in a separate partition.

I have a Lenovo T470s laptop but don't think it has two slots.
Would I need to find an enclosure for the target NVMe until I get it copied?
Is Clonezilla the cloning software I need to use?
If my newly copied NVMe won't boot, how do I make it bootable?

---

### Post by TheFu on 2024-01-19
Cloning should only be performed if the new storage has the say block size as the old storage.
You can use any tool you like to clone an entire storage device.  On Linux, any tool that copies bits from A ---> B can be used. No special tool is required, however, the source storage device and target storage device cannot be in-use (i.e. mounted) during this process.

I find clonezilla to be overly complicated for this task.  If it was me, I'd boot off an Ubuntu desktop (any supported flavor), install **ddrescue** (the package may be gddrescue) and use that to clone from the top level device.  It should be obvious that both devices must be connected concurrently for this to work.  Be 100% certain that you know the whole disk device names for each NVMe storage device.

A risk is that if you use a USB adapter for either device, then the block size of the real storage may be faked to a completely different value by the USB controller. If that happens, it will make the copy unusable.  Of 4 USB adapters for regular storage devices, 1 has screwed with the actual, true, block sizes.

If you copy the entire disk, then any partitioning and partition flags will be copied over as well. It will boot.  After the copy is complete, only 1 of those storage devices can be connected to the same computer at a time.  This is because the whole device-level copy also copies the UUIDs, LABELs, as well. Duplicate UUIDs aren't allowed and will confuse the fstab (and other) mounting software.

---

### Post by oldfred on 2024-01-19
I really recommend new install & restore from backup.

I did exactly what you are doing a couple of years ago. Found I like external SSD so much, I have used it in place of my many flash drives that are now so slow in comparison. And then bought another adapter & NVMe drive to use as an external. Full installs on both external SSDs that are different than desktop, but have copies of /home. 

You cannot reboot with both drives connected if clone as duplicate UUIDs not allowed. But if new install, then you can use external as data copy & emergency repair drive.

Newer adapters seem to be both SSD or NVMe. But not sure NVMe is real advantage unless you can use faster USB-c port.
My first drive was a M.2 SSD which I used this adapter. Not sure if still sold.
Fideco M.2 to USB3.1
Samsung M.2 SSD 850 (not NVMe) was in my desktop.
My second external:
2023
SSK Aluminum M.2 NVME SATA SSD Enclosure Adapter, USB 3.2 Gen 2 (10 Gbps) to NVME PCI-E SATA M-Key/(B+M) Key Solid State Drive External Enclosure Support UASP Trim for NVME/SATA SSDs 2242/2260/2280 
SAMSUNG 980 SSD 1TB PCle 3.0x4, NVMe M.2 2280, Internal Solid State Drive, Storage for PC, Laptops, Gaming and More, HMB Technology, Intelligent Turbowrite, Speeds of up-to 3,500MB/s, MZ-V8V1T0B/AM 

You want this in spec for better support, later found:
UASP (USB Attached SCSI Protocol)

---

### Post by TheFu on 2024-01-19
+100 on doing a fresh install.

There are a few issues when you clone a disk into a larger disk that I didn't mention.  
a) you want to have a GPT partition table these days. Older installs might have MBR which has all sorts of stupid limitations that haven't been necessary since 2010.  Some Ubuntu installers as recent at 18.04 created MBR partition tables.

b) With GPT, there are 2 copies of the partition table - one at the beginning and the other at the end of the storage. If you clone it, the one at the end will be in the wrong place and you'll need to move it.

If the install is old enough to need a new root device, then taking the 15 minutes to do a fresh install is well worth it.  Plus, you'll have an opportunity to NOT install all the old, unused applications and remove any prior cruft settings that were left over from other program installations.

For most users, the only critical data is inside their HOME directory, so if you do a fresh install to the new disk and setup a separate home partition (or use another volume technique like LVM or ZFS provide), then you can keep the OS separate from the HOME directories. This can both make for a cleaner install and easier way to backup the most important files as part of your backup strategy.

---

### Post by cwmoser on 2024-01-20
These are great tips and advice.
I do have a rather "built up" 22.04 Ubuntu OS, and a fresh install as you recommend seems the way to go.
I do have my /home in a separate partition too.

I have read but not tried using dpkg to list the installed software in the old OS to a file,  and use dpkg to reload all that I have installed to a freshly loaded and perhaps next release of Ubuntu.

Have you found that these work well or perhaps there is another way to accomplish the same thing?

These are the commands I was considering:

$ dpkg --get-selections | grep -v deinstall > Installed-Software

$  sudo  dpkg --set-selections < Installed-Software

---

### Post by TheFu on 2024-01-20
**dpkg --get-selections/--set-selections** is one method, but any list it generates should probably be reviewed and cut because packages selected to be installed in that way are forced as "manual", not "dependency" installations.  

There's also the **apt-mark showauto/showmanual** method.

There are subtle differences between the two options.  Both just toggle the "to be installed" flag inside APT, after that is toggled, we still need to ask for APT to actually perform the install. I found **aptitude** to be the easiest way to do that, but I suspect **synaptic** would work as well. For a desktop, both of those tools are installed on my systems, but neither are installed by default, so beware.

Really, the best way to move to a new disk is to use your backup+restore method.  This is the perfect opportunity to test those and ensure they work. When else will you have a zero-risk (except time) chance to test that?  Cloning a disk is not a viable, daily, backup, method.  It isn't even suitable for weekly backups. It is just too cumbersome and if backups cannot be 100% automated, we humans are lazy and won't do them.

The goal for any restore process is to be up and running in as few commands as possible, as quickly as possible, while not requiring 50 full copies of your stuff to provide reasonable backup sets to handle malware and cryptoware attacks.  I've decided for myself that if the restore process takes less than 1 hour per system and about 20 minutes of my time, that's acceptable.  

Having automatic, daily, versioned, backups completely changes how I look at system bugs.  If I can't fix a new issue in 1 hr, I stop, wipe the system and do a restore from the latest backup (usually from about 1am the same day).  A few times I've needed to get older versions of specific files due to corruption.  Once I needed an LDAP file from 37 days ago.  Just happy I had 90 days of versioned backups.  Another time I needed a 3 day old sqlite DB - corruption again. 

Versioned backups can solve hundreds of issues, but only if you have them BEFORE you need them.

---

### Post by oldfred on 2024-01-20
I run dpkg as part of my backup script.
But have had to house clean list as it has everything. Old kernels, and maybe some apps I do not remember & then do not really want.
I now have scripted most of the apps I want.

Last time I used dpkg to reinstall, I got a warning, and had to run dselect.
Not sure if that was because some apps were not in the newer distribution.

Also you have to remove ppas & reinstall them, if upgrading a version. Not all ppa have every version, particularly the latest version. And some are not required with a newer version.

Same with any proprietary drivers like nVidia. You have to reinstall that as part of install with install optional restricted extras. Many systems will only boot to a terminal with grub rescue where you can install proprietary drivers, if you did not install them as part of install. Some will boot to a low quality graphics using nomodeset and then from gui you can add proprietary drivers in System, settings.

---

