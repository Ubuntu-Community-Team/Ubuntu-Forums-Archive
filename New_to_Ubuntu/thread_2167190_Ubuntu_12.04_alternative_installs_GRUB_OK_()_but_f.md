---
title: "Ubuntu 12.04 alternative installs GRUB OK (?) but fails to boot after restart?"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by Karl_Wallin on 2013-08-12
Hi!

Sorry if my post is overly bloated with information but I wanted to get so much info in as I could since it might aid the troubleshooting.
And "Hi Everybody" *voice of Dr Nick*! :)

---

Gigabyte GA-965P-DS3 Rev. 1.0 BIOS: F14
2x Samsung HD103UJ


BIOS Settings (revert to fail-safe settings and then changed this below):
SATA AHCI Mode: AHCI
SATA Port0-1 Native Mode: Enabled (Work at Native IDE Mode)
Onboard SATA/IDE Device: Enabled
Onboard SATA/IDE Ctrl Mode: RAID/IDE


HDD:s connected to the two SATA-ports that are supported by the Jmicron RAID Controller. Believe its Jmicron anyway (?).
USB with drivers for the RAID controller seems to have to be inserted to enable me to go into the RAID bios (CTRL+G) after POST otherwise the 
array fails.


Settings in RAID BIOS:
Name: GRAID
Level: 0-Stripe
Disks: HDD0 & HDD1 (Both Samsung HD103UJ) [SMART status and short disk test on both drives reports them as "OK"]
Block: 128 KB
Size: 2000GB
Model Name: RDD0: GRAID
RAID Level: 0-Stripe
Capacity Status: 2000 GB
Status: Normal
Members (HDDx):
01


Ubuntu 12.04 AMD x64 Alternative Installer (w. ethernet cable connected)
Language: English
"Install Ubuntu"
Select a language: "English - English"
Select your location: "other" - "Europe" - "Sweden"
Configure locales: "United States - en_US.UTF-8"
Configure the keyboard: Detect keyboard layout? "Yes" (Detecting keyboard correctly as "se")
Configure the network: Hostname: "ubuntu"
Set up users and passwords: "ubuntu" "ubuntu" "ubuntu" (Weak password = "OK")
Encrypt your home directory?: "No"
Configure the clock: "Yes" (Timezone correctly identified)
Detect disks: Activate Serial ATA RAID devices? "Yes"
Partition disks: "Guided - use entire disk"
Select disk to partition: "Serial ATA RAID jmicron_GRAID (stripe) - 2.0 TB Linux device-mapper (striped)"
Following partitions are going to be formatted:
partition #1 of Serial ATA RAID jmicron_GRAID (stripe) as ext4 (I believe this is /dev/mapper/jmicron_GRAID1 in a later step)
partition #5 of Serial ATA RAID jmicron_GRAID (stripe) as swap (I believe this is /dev/mapper/jmicron_GRAID5 in a later step)
-> Write changes to disk -> Yes
Configure the package manager: HTTP proxy information (blank for none): "Blank" (no text)
Install the GRUB boot loader on a hard disk: Device for boot loader installation: "/dev/mapper" (default)
!Unable to install GRUB in /dev/mapper, Executing 'grub-install /dev/mapper' failed.
This is a fatal error.
Running "ls" in the terminal in "/dev/mapper" and that returns:
control jmicron_GRAID jmicron_GRAID1 jmicron_GRAID2 jmicron_GRAID5
/dev/mapper/jmicron_GRAID1/ fails as well
/dev/mapper/jmicron_GRAID1 works (where to install GRUB to)
Finish the installation: is the system clock set to UTC? "Yes" (?)
Finishing installation -> Rebooting
System restarts -> RAID BIOS reports drives as OK (still in RAID-0) and then when it should boot into Ubuntu I get a cursor that just blinks.


Rebooting with CD -> Rescue mode -> Entering partition step -> Enable RAID Devices -> entering terminal -> "blkid":
/dev/sr0: Ubuntu DVD
/dev/sda: TYPE="jmicron_raid_member"
/dev/sdb1: LABEL="NY VOLYM" UUID="B058-47CE" TYPE="vfat" (probably USB stick with RAID drivers)
/dev/sdc: TYPE="jmicron_raid_member"


Step: "Devices to use as root file system: "/dev/sdb1"
(Does not list any of my RAID volumes)


How should I set this up?
Will probably do a full reinstall with the correct settings (if I can find them here hopefully) in order to avoid hickups later on.

Appreciate any and all help, not so experienced with RAID and Ubuntu (Linux).

Best Regards / Karl, Sweden

---

### Post by oldfred on 2013-08-13
I do not really know RAID. But you install grub to the MBR or root of a drive. 

Your RAID show have this as the install location of grub:
/dev/mapper/jmicron_GRAID

Example is mounting [COLOR=#ff0000]p1[/COLOR] or / with no separate /boot partition. The install is into path without p1.
       sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0[COLOR=#ff0000]p1[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

### Post by Karl_Wallin on 2013-08-13
> **oldfred said:**
> I do not really know RAID. But you install grub to the MBR or root of a drive. 

Your RAID show have this as the install location of grub:
/dev/mapper/jmicron_GRAID

Example is mounting [COLOR=#ff0000]p1[/COLOR] or / with no separate /boot partition. The install is into path without p1.
       sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0[COLOR=#ff0000]p1[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

Tried removing all data as well as the RAID-array, recreated it and then reinstalled Ubuntu, used /dev/mapper/jmicron_GRAID as the install location of GRUB, everything went fine but the system does not boot, it just sits there after POST and displaying some H/W-info and then does nothing. First there was a blinking cursor, now its nothing, not even a static cursor. Didn't try the terminal command though.

--- 

Edit:

Got an error message after a while when waiting for something to happen:
"error: no such device: acd26bf6-9c70-45a2-84b9-71566771fc489"
"grub rescue: _" (blinking cursor awaiting input)

Any ideas?

---

### Post by oldfred on 2013-08-13
If you only have one install, it does not show grub menu unless you hold shift key from BIOS until menu appears. See it that gives you a menu.
You may have booted, but have video issuses? What video card or chip?

---

### Post by Karl_Wallin on 2013-08-13
> **oldfred said:**
> If you only have one install, it does not show grub menu unless you hold shift key from BIOS until menu appears. See it that gives you a menu.
You may have booted, but have video issuses? What video card or chip?

Have nothing else on the disks only my Ubuntu installation.
I have a friends 8400GS I believe, its an old computer so haven't really checked it out.
I see text above the error message and a blinking cursor so it has not booted, I can give input (i.e. write commands etc.)

Holding SHIFT when starting the computer (RAID-array looks OK btw) gives me:
"GRUB Loading."
then the same error message.

---

### Post by oldfred on 2013-08-13
If an nVidia card you will need to get to grub menu to add nomodeset. 

But you need to get grub correctly installed first.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Karl_Wallin on 2013-08-13
> **oldfred said:**
> If an nVidia card you will need to get to grub menu to add nomodeset. 

But you need to get grub correctly installed first.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Thanks for the reply.
This is before starting the repair tool:
[http://paste.ubuntu.com/5983179/](http://paste.ubuntu.com/5983179/)

Now I am a bit in the process and I can now pick where GRUB should be installed, the program lists:
dev/sda (1TB Samsung HDD)
dev/sdb (1TB Samsung HDD)
dev/sdc (USB-memory for SATA-drivers)
dev/mapper/jmicron_GRAID (2tb: jmicron_GRAID) 2000381MB
dev/dm-1 (1.99TB jmicron_GRAID) 1991791MB

I chose dev/mapper/jmicron_GRAID

New log after finished repair:
paste.ubuntu.com/5983207

---

YAY! It works! Thanks A LOT you guys for your help!

Edited the BIOS boot options for my HDD(s) so my GRAID "HDD" came first before the USB-memory (w. my SATA-drivers) and then it worked :D

---

### Post by oldfred on 2013-08-13
Boot-Repair often defaults to the correct solution. Makes it a lot easier to fix. :)

---

