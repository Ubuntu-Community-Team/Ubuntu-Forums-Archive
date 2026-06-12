---
title: "Error on running boot-repair - &quot;Please create a ESP partition&quot; (BootInfo included)"
date: 2021-04-08
forum: New to Ubuntu
---

### Post by fosschamp on 2021-04-08
I messed up my system's dual boot(windows 10+ ubuntu 16.04) when I was upgrading my HDD.
Now my grub menu does not appear anymore and always windows loads up even when I manually choose "ubuntu" from boot menu(`F12`).
I tried `boot-repair` to repair with "recommended repair" option and I get this error

> Please create a ESP partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as Gparted. Then try again.

Note, that I'm using `boot-repair` via live usb(ubuntu 20.04)

**Here's the full [BootInfo summary]("https://pastebin.com/PQrwy5iU")**

---

### Post by oldfred on 2021-04-08
You show an ESP, but if Boot-Repair cannot see it, it must have some issue.
Is Windows fast start up off?
Did Windows do an UEFI update & you have a default UEFI setting that secures or locks updates to ESP?

You may need to run chkdsk from Windows (you have to mount ESP to run it). Or run dosfsck from Linux.
sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda2

You also have a lot of old kernels?
Are they still in dpkg, so easily deleted? Otherwise you have to manually delete them.
Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones

And then only if still not shown, manually delete, but you also need to check /lib/modules & /usr/src.
in /boot by version: abi, config, initrd.img, vmlinuz
[https://ubuntuforums.org/showthread.php?t=2413216](https://ubuntuforums.org/showthread.php?t=2413216)


man dosfsck

---

### Post by fosschamp on 2021-04-08
> Is Windows fast start up off?
Yes

> Did Windows do an UEFI update & you have a default UEFI setting that secures or locks updates to ESP?
How do I check this? If you meant Secure Boot, I have disabled that to avoid any issues as many have reported bugs in that. Although when I made some changes in boot earlier(before there were any issues), it was enabled that time(most probably).

> Or run dosfsck from Linux.
> sudo /sbin/fsck.vfat -V <the fat32 device>
> sudo fsck.vfat -t -a /dev/sda2

I just did that and ran boot-repair again. Same error.

> Determine your current kernel with 
Here's the output of `uname -a` 
Linux ubuntu 5.8.0-43-generic #49~20.04.1-Ubuntu SMP Fri Feb 5 09:57:56 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
(Note: I am running uname -a command on "liveusb -> Try Ubuntu"(which is ubuntu@20.04), should I mount "HDD ubuntu - /dev/sda8"(which is ubuntu@16.04) and chroot and then run this?)

> In synaptic search for linux-image to choose to delete old ones
Did you mean to do this on HDD ubuntu - /dev/sda8. Or you mean to do this on the "liveusb->Try Ubuntu" itself?

---

### Post by tea for one on 2021-04-08
Ubuntu 16.04 is unsupported at the end of April and, rather than fighting the boot problem, it may be worth considering backing up your data and installing Ubuntu 20.04 LTS.

It will save you the time of searching and removing innumerable kernels
Also, if you are careful with a fresh installation, the EFI system partition will be repaired and grub will be restored correctly.

Currently, your ESP is not clearly recognised in the boot-repair report.

[COLOR="#0000FF"]Line 154[/COLOR] sda2	: maybeESP
It should state **is---ESP**

---

### Post by oldfred on 2021-04-08
Besides UEFI Secure Boot setting are multiple other UEFI settings. Most do not matter and it varies by brand.
On my Asus motherboard I change 7 or 8 settings, some required & others optional.
My Gigabyte motherboard only requires a few settings, primarily Secure boot off, but have to check for AHCI & some other settings.

We have seen other UEFI systems with settings that "Secure" or lock ESP. That is often separate from Secure Boot, so still has to be off.
Some also have settings preventing USB boot or full USB support as allowing another boot is not Secure, but again a separate setting that has to be changed, if you have it.

---

### Post by fosschamp on 2021-04-08
> **tea for one said:**
> Ubuntu 16.04 is unsupported at the end of April and, rather than fighting the boot problem, it may be worth considering backing up your data and installing Ubuntu 20.04 LTS.

It will save you the time of searching and removing innumerable kernels
Also, if you are careful with a fresh installation, the EFI system partition will be repaired and grub will be restored correctly.

Currently, your ESP is not clearly recognised in the boot-repair report.

[COLOR=#0000FF]Line 154[/COLOR] sda2    : maybeESP
It should state **is---ESP**


That's what I was doing when I ran into problem. I was setting up a new drive where I installed 20.04+windows but I still need to access the old drive because I need access to some accounts. The point where I messed this dual boot was when I inserted the new drive and installed windows+ubuntu20 on that, and then plugged the old drive again, at that point I could not get to the grub menu.

---

### Post by fosschamp on 2021-04-08
> **oldfred said:**
> Besides UEFI Secure Boot setting are multiple other UEFI settings. Most do not matter and it varies by brand.
On my Asus motherboard I change 7 or 8 settings, some required & others optional.
My Gigabyte motherboard only requires a few settings, primarily Secure boot off, but have to check for AHCI & some other settings.

We have seen other UEFI systems with settings that "Secure" or lock ESP. That is often separate from Secure Boot, so still has to be off.
Some also have settings preventing USB boot or full USB support as allowing another boot is not Secure, but again a separate setting that has to be changed, if you have it.

There's no such setting in my system. Some clues that might be helpful to help you guess the problem

* When I inserted the new drive(check my prev. comment) and was installing Ubuntu 20.04 on it, it asked me to enable secure boot and a password for that. I did that and I do remember the password. Later on, in order to fix the dual boot issue, I disabled the secure boot. (Note: the problem I've posted is related to the old drive not this new drive)
* USB boot is working, that is how I am able to get the BootInfo summary
* One weird thing I see in the info via `efibootmgr -v` is that the Windows Boot Manager partition is MBR and the ubuntu partition is GPT. Is it normal? Is it possible to have MBR and GPT both on a system? Could this be the cause of the problem?

Does that give any lead on what should I do next or do you need any additional info?

---

### Post by tea for one on 2021-04-09
> **fosschamp said:**
> That's what I was doing when I ran into problem. I was setting up a new drive where I installed 20.04+windows but I still need to access the old drive because I need access to some accounts. The point where I messed this dual boot was when I inserted the new drive and installed windows+ubuntu20 on that, and then plugged the old drive again, at that point I could not get to the grub menu.

A second drive was not mentioned in your original post and your boot-repair report only showed one drive (sda) with 9 partitions.
It would have been helpful to know complete details.

Anyway, now that we know that you want to create a dual boot (Windows 10 and Ubuntu 20.04) on a new drive:-

Have you got a back-up of both your Windows data and Ubuntu data?
If not, back it up now using a **live **session?

Please confirm when you have created the back-up(s)

---

### Post by oldfred on 2021-04-09
UEFI & BIOS/MBR boot on same drive is not normally possible.
Windows in BIOS mode requires MBR partitioning and must have boot flag on the primary NTFS partition with its boot files.
But UEFI (which should be gpt) puts the boot,esp flags on the ESP - efi system partition.
Ubuntu lets you install in UEFI mode to a MBR(msdos) partitioned drive and probably should not, Windows requires gpt.

Conversion from MBR to gpt will erase drive. There are tools to convert primarily for data drives, bootable drives have various partition requirements which a conversion will not do.

---

