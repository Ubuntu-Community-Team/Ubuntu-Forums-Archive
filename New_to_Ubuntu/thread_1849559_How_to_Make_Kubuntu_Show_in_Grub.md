---
title: "How to Make Kubuntu Show in Grub?"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by Wiking on 2011-09-24
Hi, I installed 2 Linux distros on the same HD. For the first distro I made the following partitions; /boot, /, /home/ and a swap partition.

For the second distro I just made the /, /home partitions.

Originally I had Dual boot set-up with Kubuntu 11.04 and W7 on separate hard drives. Using EasyBCD in Windows I was able to setup Grub so that W7 was my default OS and Kubuntu my other OS.

Now that I installed the other Distro, the Grub selection boots into the second Distro, and I have no way of booting into Kubuntu, but the partitions that belong to Kubuntu do mount.

I tried updating Grub using ```
update-grub
``` in a console in the second distro, but when I reboot I only have the option of 2 OS's; Windows, and the second distro.

I tried using the BCD tool in windows but it only lets my point to the partition, not a folder, so I can only select the /boot partition which the second distro took over.

I would like to be able to boot in all 3 OS's. 

I'm sorry if this has been answered before but I've been working on this for a day now, reading the forums, and I've made some progress compared to where I was. I just need to get Grub to point to Kubuntu.

---

### Post by Blasphemist on 2011-09-24
Please install boot-repair and at first just click the boot info summary and post it's url for us to review. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Wiking on 2011-09-24
[http://paste.ubuntu.com/696395/]("http://paste.ubuntu.com/696395/")

---

### Post by Blasphemist on 2011-09-24
Here are my notes as I try to sort this out in the script results.

Grub2 but not the most current version is installed to the MBR of sda and looks to the BackTrack partition for it's boot files. There is no boot loader installed to the sdb windows drive and it appears that drive may not have been read well. Sdc is confusing. It looks like it has a copy of the MBR from sda but not the same partitions. Grub2 looks to a non-existent partition for its files. Windows seems to have written to the mbr of sdd but no boot files are found. I can't tell what the other device found is. Is Kubuntu on sda6?

Your Grub entries are wrong and I can't see just how that happened. The first entry point to sdd1 an NTFS partition. That entry even has previous kernel versions shown. The next entry is found by the Grub2 os prober and is windows 7 on sdb1, which could be correct. sda6 does have grub files and that grub has entries for windows on sdb1 and ubuntu on sdd3 (sdd3 doesn't seem to exist). fstab on sda6 shows it as / mount point, sda7 as /Home and sda5 as swap. 

The backtrack partition (sda8) has grub files that have entries for itself and windows in the right partitions. It uses old hdx notation for devices and must be an old grub. It shows / on sda8 and /Home on sda9 in fstab.

From all of this I wondered about RAID being involved and the script results do show RAID errors that I can't interpret. This is in the boot-repair log.
> sda8 contains The OS now in use - Ubuntu 10.04.2 LTS (linux)
sda6 contains Ubuntu 11.04 (linux)
sdc1 contains Windows 7 (windows)
I also wonder about LBA being in use on sda from the log. The log makes me think that boot-repair thinks it can fix grub but I'm not sure at all about that. I believe it would purge and reinstall grub2 on sda8. That could be enough and right and I don't expect that to make it worse.

I don't feel like I've given you great information and a solution. I'll see if I can get anyone else with more experience to take a look if they haven't while I've been doing this.

---

### Post by Wiking on 2011-09-24
The RAID error is from a PCI-E Sata card which the HD with both distros is connected too. It has an option for RAID but is not configured it just goes through a screen when booting.

sdb and sdd are both NTFS for storage and don't have any OS's on. I had to mount one of them manually as Kubuntu was not recognizing one. 

sdc I know has W7 installed and is where it boots.

Kubuntu is on sda6 and I believe the /home folder is sda7.

---

### Post by wildmanne39 on 2011-09-24
Hi, it is quite possible from looking at it that the boot repair may fix it the boot issue with kubuntu, but with the errors about the raid and several grubs being installed in different partitions, I think we are better off waiting on the experts.
Thank you

---

### Post by oldfred on 2011-09-25
Older versions of grub2 or boot script do not show drive correctly so grub in sdc may boot backtrack also. 

I do not recommend separate /boot partitions except very old drives or servers with RAID or LVM. It makes it a bit more difficult to reinstall grub and offers little advantage on desktops. Yours is even more confused since your fstab does not show the /boot partition, but all the boot files are in the /boot.

I do believe boot-repair was updated to include /boot partitions, but you have to tell it that. I have not used boot repair. But your fstab in sda6 does not show the separate /boot and the files are not also in / (root), so I do not think it will handle this special case.  Or it may let you boot, but any kernel updates will get writing into root not boot after you boot.

It may be easier to add a boot stanza for Kubuntu to Backtrack and see if it will boot, but it may not unless you chroot into Kubuntu to fully install grub & kernels into root or edit fstab to include the /boot partition. I think it may boot but if you ever have an update it will not update correctly as the updates will go into root since the /boot entry is missing from fstab.

Add this to Backtrack's 40_custom Which is just your entry in Kubuntu but I changed the set root from sdd to sda, since you must have reordered drives. Search by UUID overides the entry anyway.
gksudo gedit /etc/grub.d/40_custom
```

menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 57ae3068-aca7-4c5f-a83b-03053d0de086
    linux    /vmlinuz-2.6.38-11-generic root=UUID=bf8384ed-3a1d-4ca8-bc3f-70d6fd8fcda1 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-11-generic
}

```The only RAID I see is your sdb drive and I do not know why it shows that. Did you turn on a RAID setting when installing sdb? That may be part of why you have trouble mounting it as you have to handle it differently. I do not know RAID except how to remove it.:)

If you can boot back into Kubuntu I would totally reinstall grub &  the kernels. This may obsolete the /boot partition. And then the current entry in backtracks 40_custom will not work.

apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
# possibly this also, which may redo some of above
dpkg-reconfigure grub-pc

---

### Post by Wiking on 2011-09-25
I edited 40_custom and rebooted but Kubuntu did not show up.

I tried re-installing grub and the kernals on sda6 using a Knoppix Live CD and tried inserting the codes but I was met with an error when I tried to access root on sda6.

sudo chroot /media/sda6

I got:

chroot: failed to run command ' /bin/bash': Exec format error

RAID is not turned on, the pci-e card always runs a screen after bios for some kind of boot option, sda is connected to the motherboard through the pci-e card, but the RAID option is off.

---

### Post by garyed on 2011-09-25
Since you've got grub files on different partitions you may be editing a custom file on the wrong partition. It looks like sda8 is where Grub is looking for its menu files but its hard to be certain. I would edit just a title first in 40_custom in that partition, do "sudo update-grub"  & see what shows up. All you need to have in the file is:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry 'KUbuntu partition 8' {
}

```

If that doesn't work try the other partitions until at least the title shows up on the grub boot menu. Once you get the title to show up you should be able to copy from the old menu on sda1 to get it to boot.
Be sure that your custom file is executable too.

Good luck

---

### Post by Wiking on 2011-09-25
I tried editing the 40_custom file in sda6 and sda8 both drives that have the grub.d folder, and it still wouldn't show.

Curiously when I ran update-grub command grub noticed Kubuntu 11.04 in the console terminal but it still would not show up in the GRUB boot menu.

I think I will just go ahead and wipe the whole HD and start a fresh dual installation.

So only one /boot, two / (for each distro), two /home (for each distro), and they can both share a swap. Correct?

---

### Post by oldfred on 2011-09-25
I do not suggest a separate /boot at all and you cannot share it. You can share swap if you do not hibernate.

With multiple installs I prefer to keep /home inside / (root) and use a shared data partition but that is up to you.

---

### Post by Blasphemist on 2011-09-25
> **oldfred said:**
> I do not suggest a separate /boot at all and you cannot share it. You can share swap if you do not hibernate.

With multiple installs I prefer to keep /home inside / (root) and use a shared data partition but that is up to you.

+1, I agree with these suggestions.

---

