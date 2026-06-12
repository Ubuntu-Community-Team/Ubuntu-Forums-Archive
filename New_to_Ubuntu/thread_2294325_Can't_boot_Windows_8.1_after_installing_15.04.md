---
title: "Can't boot Windows 8.1 after installing 15.04"
date: 2015-09-10
forum: New to Ubuntu
---

### Post by chopsueysensei on 2015-09-10
Hi all.
I'm a long time user of ubuntu and linux in general, however my last laptop was super old and I never tried anything newer than Windows 7 at home, until yesterday, so I have no clue about this UEFI business..

Anyway I just bought a new computer with just a 1gb freedos partition, so I installed a new Windows 8.1 partition alongside it. I installed all the needed drivers and configured to taste, and decided the obvious next step was to install ubuntu on the remaining hard drive space.
So I did, and the first warning, which I obviously ignored, is that the installer didn't mention anything about a Windows system installed, only Freedos, even if both partitions were visible in gparted.

Long story short, ubuntu runs flawless (it's super fast on the new laptop!), but my grub doesn't have an entry for Windows 8.1. The ntfs partition is perfectly visible (and accesible) in the file explorer, gparted or fdisk, it just seems grub can't see it for some reason..

I tried adding a manual entry I copied from some forum to grub config (my grub2 skills are next to null), but it didn't work. Next, I tried manually editing the entry to this:

menuentry "Windows 8.1" {
	set root='(hd0,msdos2)'
	chainloader +1
}

(that's what old Windows 7 entries used to look like), and then some text appeared (from the "windows side" it seems xP) complaining about some boot file apparently missing (can't remember the exact text, sorry).

I also tied running boot-repair, but it didn't seem to do a thing (it didn't even delete my manual entry).
Here's the info from boot-repair: [http://paste.ubuntu.com/12329856/]("http://paste.ubuntu.com/12329856/")

I believe my BIOS has been set to Legacy mode this whole time, and since the ntfs partition is visible, that must be the case right?

I really hope some good soul can help me get back Windows, I really need it for my audio stuff!
Thanks in advance!

---

### Post by oldfred on 2015-09-10
Did you leave Windows fast startup or always on hibernation on?
Grub only boots working Windows, and will not boot hibernated or Windows needing chkdsk. Best to always have a repair or install flash drive to make Windows repairs.
Boot-Repair cannot repair most Windows issues.

You also have two essential boot files in sda1. But it is the FreeDOS partition formatted FAT32.
I thought newer Windows only booted from NTFS with boot flag. Normally bootmgr & BCD are in a separate Boot partition, but do not have to be.

Grub2's os-prober found only the FreeDOS in sda1.
I might try moving the folder /Boot with the BCD file into sda2. It already seems to have a copy of bootmgr.
The os-prober looks for both bootmgr & /Boot/BCD to know which partition has Windows boot files. Grub does not use boot flag, but Windows has to have boot flag to install, or repair a NTFS partition so also move boot flag to sda2 with gparted or Windows repair disk.

Then run this & it should find your Windows.
sudo update-grub

---

### Post by Roger Cook on 2015-09-10
Super grub has corrected this same problem for me, download it and give it a try.

---

### Post by Mark Phelps on 2015-09-11
> **Roger Cook said:**
> Super grub has corrected this same problem for me, download it and give it a try.

Unless the OP went to the trouble to disable Fast Startup in Win8, no LINUX utility is going to fix this problem -- as Win8 uses a new form of hibernation that AUTOMATICALLY goes into effect whenever Windows is Shut Down or Restarted -- keeping all previously open partitions mounted, thus preventing any Linux utilities from then mounting those partitions.

To the OP: If you have access to working Windows PC ( a friend, perhaps?) you can use the link to download a legal Win8.1 ISO file and from that, you can burn a DVD from which you might be able to boot Win8.1 and repair it: [http://windows.microsoft.com/en-CA/windows-8/create-reset-refresh-media]("http://windows.microsoft.com/en-CA/windows-8/create-reset-refresh-media")

---

### Post by toxx on 2015-09-11
Try this, then reboot. Grub will scan for bootable partitions and add them automatically

```
sudo update-grub
```

---

### Post by chemist931 on 2015-09-12
This MIGHT help? Sometimes when Grub is messed up this can fix a wide range of problems.
[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

---

### Post by chopsueysensei on 2015-09-15
> **oldfred said:**
> Did you leave Windows fast startup or always on hibernation on?
Grub only boots working Windows, and will not boot hibernated or Windows needing chkdsk. Best to always have a repair or install flash drive to make Windows repairs.
Boot-Repair cannot repair most Windows issues.

You also have two essential boot files in sda1. But it is the FreeDOS partition formatted FAT32.
I thought newer Windows only booted from NTFS with boot flag. Normally bootmgr & BCD are in a separate Boot partition, but do not have to be.

Grub2's os-prober found only the FreeDOS in sda1.
I might try moving the folder /Boot with the BCD file into sda2. It already seems to have a copy of bootmgr.
The os-prober looks for both bootmgr & /Boot/BCD to know which partition has Windows boot files. Grub does not use boot flag, but Windows has to have boot flag to install, or repair a NTFS partition so also move boot flag to sda2 with gparted or Windows repair disk.

Then run this & it should find your Windows.
sudo update-grub

Thanks for the reply. Actually, looking at the output I posted, I realized that for some reason Windows had put its boot files on the first partition instead of its own, so I tried to boot the Freedos partition in Grub and voila! it worked..
I tried to boot Windows into rescue mode in order to repair the boot data using its own tools, but haven't succeeded.
I'll try your suggestion of simply copying the BCD folder and marking the boot flag, and see if that works.. in case grub still doesn't find the Windows partition, would a simple manual entry like the one I wrote work?

Thanks for all the suggestions, this is the reason Ubuntu & linux in general rocks! :)

---

### Post by oldfred on 2015-09-15
Every NTFS partition has to have essential boot data in the partition boot sector. If it does not boot, then that might be the issue. With Vista or later the partition boot sector has info saying to use bootmgr to boot (with XP it says ntldr).

Grub2 has a lot of loadable modules. Many already are configured.

Some boot stanza include the ntfs, msdos, chain modules, but your boot stanza should work. Some also use an alternative direct link to bootmgr.

menuentry "Microsoft Windows Vista/7/8 BIOS-MBR" {
     insmod part_msdos
    insmod ntfs
    insmod ntldr     
    ntldr /bootmgr
}

The ntldr above is really a grub command to load the Windows boot loader.

---

