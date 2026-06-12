---
title: "Installation failed 22.04 from Thumb Drive ..."
date: 2022-08-08
forum: New to Ubuntu
---

### Post by cwmoser on 2022-08-08
Tried to install Ubuntu Mate 22.04 to partition /dev/sda4 on my hard drive.
Keeping Ubuntu Mate 20.04 as backup on /dev/sda1.

Mate 22.04 boots up OK from Thumb Drive and runs as expected.
When I select to do "Installation", and the disk setup where you select "Something Else", I selected /dev/sda4 but 
the hour glass just circulates and I cannot select other settings.

So I selected to "quit", then shutdown but again I get a continuous hour glass, then I RESET the PC.
Then the Thumb Drive installation gives me an HEI error probably means that I need to redo the Thumb Drive.

Another observation, booting off the Thumb Drive seems much slower than prior versions of Mate.

I have not checked on my /dev/sda4 partition that had Mate 19.4 and its likely to be corrupted now.

---

### Post by cwmoser on 2022-08-08
Should I rebuild the Thumb Drive and try again?  
Or is there an issue with this installation?
Or should I just wait until issues like this are ironed out.

---

### Post by oldfred on 2022-08-08
I would redo USB flash drive, but that it works in live mode should indicate it is ok.

But often the hour glass is because it cannot find/open a partition?
Is your old install corrupted?

I might run fsck or e2fsck  on every ext4 partition on HDD from live installer so partitions are unmounted.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by cwmoser on 2022-08-09
Rebuilt the Thumb Drive using another stick.
Using Unetbootin to create the bootable stick.

This time it fails complaining that there is not boot area on /dev/sda, but my 20.04 Ubuntu Mate boots just find off /dev/sda.
It also wants to use UEFI.

Now my PC is older, it does not support UEFI, still its an Intel i7 cpu and runs very fast.

---

### Post by guiverc on 2022-08-09
In your first post, you mention

> Then the Thumb Drive installation gives me an HEI error probably means that I need to redo the Thumb Drive.

but I don't know what a HEI error is, is that how it shows?  "HEI error" as I've not see that before.

> **cwmoser said:**
> 
This time it fails complaining that there is not boot area on /dev/sda, but my 20.04 Ubuntu Mate boots just find off /dev/sda.
It also wants to use UEFI.


Ubuntu MATE uses the `ubiquity` installer, which defaults to wanting to create an ESP (*EFI system partition*), but it does **not** require it's creation if using a legacy partition table, as I've tested that on BIOS boxes for all releases of Ubuntu MATE including 22.04 LTS (ie. boxes as old as from 2005 that pre-date the i-series intel processors too).

I can't offer advice, as I'm unsure what you're trying to describe. It may help if you were exact with messages you see, or providing links to where you've stored photos of the screens may also help

---

### Post by ActionParsnip on 2022-08-09
Did you verify the ISO before you used it, or used torrents to download the file?

---

### Post by oldfred on 2022-08-09
What system is it. And what video card/chip?
Almost all i7 systems are UEFI.
UEFI became the standard in 2012 when Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives.
Are you not installing to sda.
And if installing in UEFI mode, it wants an ESP - efi system partition on first drive, usually sda.

---

### Post by cwmoser on 2022-08-09
I downloaded Ubuntu 22.04 instead of Mate.
Still no joy.

I get:
No EFI System Partition was found.
The System will likely not be able to boot successfully,
and the installation may fail.
Continue
... it appears to install, but then ...
Unable to install GRUB in /dev/sda
Executing 'grub-install /dev/sda' failed.
This is a fatal error.
OK

Failure on my PC - HP 8200 Elite Microtower i7-2600 3.4Ghz 16GB RAM SSD and also two regular HDs.
Radeon 6570 Video Card

---

### Post by oldfred on 2022-08-09
> No EFI System Partition was found.
That error is from an UEFI install without an ESP.

Are you sure system is not booting live installer in UEFI mode?
You should have two boot modes for live USB installer. One is clearly UEFI with UEFI:XXXX and one is BIOS as XXXX. Where XXX is name or label of flash drive. My system often uses PMAP.

---

### Post by cwmoser on 2022-08-09
I found a fix.
I just ignore the warnings about "No EFI ...".
After the error "Unable to install GRUB in /dev/sda", I just shut down and reboot into my old 20.04 installation.
Then drop to command prompt and run:  update-grub /dev/sda
It scans all the hard drives for an installation and creates entries for booting.

Still not everything setup in 22.04 as I had with 20.04, sooo I think I'll next try to upgrade my old 20.04 to 22.04 rather than create a new copy.

---

### Post by oldfred on 2022-08-09
If you just copy /home you get all your settings & data from old install.
And if you export list of installed apps, you can easily reinstall them.
Both should be part of your standard backup anyway.

---

