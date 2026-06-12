---
title: "Dual boot with Windows 7"
date: 2014-12-09
forum: New to Ubuntu
---

### Post by utterme on 2014-12-09
Hello to everyone in the linux world.):P

I'm trying to do a new ubuntu install and need help with install options.
First. some relevant info.

Desktop PC> Acer Veriton M670G.
C: 300GB sata with win7 ultimate
E: 349MB System reserved
F: 80GB sata with XP Pro
G: 80GB sata empty and formatted NTSF

I already installed ubuntu 14.04.1 from thumb-drive but ended up with win7 dual boot.
Not what I wanted and did a boot repair for win7.
Here's the log> [http://paste.ubuntu.com/9444658/](http://paste.ubuntu.com/9444658/)

I want to install ubuntu to G: 
I have bios set so I can pick which drive to boot from.
TIA for any help.

---

### Post by Mark Phelps on 2014-12-09
> I want to install ubuntu to G: You can't do that -- because that is a Windows filesystem and Ubuntu needs a Linux filesystem.

So, if you want to use that space, in Win7 Disk Management tool, remove partition "G" and leave it unformatted.

Then, when you boot from the Ubuntu, use the "something else" option to select the unallocated space for Ubuntu.

---

### Post by grahammechanical on 2014-12-09
> [COLOR=#000000]I already installed ubuntu 14.04.1 from thumb-drive but ended up with win7 dual boot. [/COLOR][COLOR=#000000]Not what I wanted and did a boot repair for win7.[/COLOR]

Please confirm that C: and E: are partitions on the same hard disk and that F: and G: are separate hard disks.

If G: is a separate drive, then my advice would be to temporarily disconnect all the drives except G: and then install Ubuntu using the entire disk option. That would be very simple install of Ubuntu to do. Then reconnect the other drives and load into Ubuntu and in the terminal run

```
sudo update-grub
```

Updating the Grub configuration files should put the other operating systems into the Grub boot menu. Then set the boot choice in UEFI to boot the Ubuntu Drive and you will get boot menu choices to the other operating systems.

Regards.

---

### Post by utterme on 2014-12-09
> **Mark Phelps said:**
> You can't do that -- because that is a Windows filesystem and Ubuntu needs a Linux filesystem.

So, if you want to use that space, in Win7 Disk Management tool, remove partition "G" and leave it unformatted.

Then, when you boot from the Ubuntu, use the "something else" option to select the unallocated space for Ubuntu.

Thanks Mark, will remove the partition from G:

> Please confirm that C: and E: are partitions on the same hard disk and that F: and G: are separate hard disks.

Yes grahmmechanical, C: & E: are on same disk and F: & G: are separate drives.

> If G: is a separate drive, then my advice would be to temporarily  disconnect all the drives except G: and then install Ubuntu using the  entire disk option. 

Sound advice, thanks. And now to get at it.:cool:

---

