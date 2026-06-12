---
title: "remove last installed distro - uefi/gpt system"
date: 2016-02-28
forum: New to Ubuntu
---

### Post by sukelis on 2016-02-28
I've tried searching for this but haven't found a definitive answer.  I want to remove the last distro I installed without affecting any of the others.  Since it was the last one installed, the partitions are at the end of the disk.  So is it just a matter of deleting the partitions and updating grub?  This is a uefi system so I know I have a efi boot partition, but does the standard grub update work on uefi?

More Details:
Dell Inspiron 3521 laptop which has UEFI and GPT.  It was installed with win8.1 and I've had it with MS so I installed some Linux distros to try out.  Each distro has it's own / and /home, they all share the swap.  They were all installed to use the efi boot partition.

The OS's (and installation order):  Windows 8.1, Mint Xfce, lubuntu and xubuntu.  The Mint is a great windows substitute for mindless use (and showing others) but I mostly use the lubuntu distro.  I added the xubuntu thinking that since mint has xfce and I like it ok, then having ubuntu have the same DE would be a good idea, but I just really prefer the lxde.  

Originally I thought that when I made up my mind I would just delete them all and start over, but it turns out I want to keep both mint and lubuntu, and I want to keep them in their current totally separate configuration, with lubuntu as the defualt boot.  Which really simplifies things... if I can just figure out how to ditch the xubuntu.

---

### Post by X-RED_Tech on 2016-02-28
Yes, grub-update works with UEFI.

---

### Post by sukelis on 2016-02-28
So it's really that easy?  I just boot into lubuntu and delete the xubuntu partitions and run grub-update?  Nothing else?  (OK I know my paranoia is showing, but it just seems too easy... )

---

### Post by Dennis N on 2016-02-28
> **sukelis said:**
> So it's really that easy?  I just boot into lubuntu and delete the xubuntu partitions and run grub-update?  Nothing else?  (OK I know my paranoia is showing, but it just seems too easy... )

No, that won't work. update-grub run from Lubuntu only generates a new grub menu for Lubuntu, and would not change what O.S. boots at startup by default. If you then deleted the Xubuntu partition, no grub menu would even appear on startup (since the default OS providing it is gone). The UEFI boot manager might boot Windows directly, however.

---

### Post by sukelis on 2016-02-28
> **Dennis N said:**
> No, that won't work. update-grub run from Lubuntu only generates a new grub menu for Lubuntu, and would not change what O.S. boots at startup by default. If you then deleted the Xubuntu partition, no grub menu would even appear on startup (since the default OS providing it is gone). The UEFI boot manager might boot Windows directly, however.
What do you mean the default OS providing it?  Since I installed the bootloader into the efi boot partition doesn't that separate it from the individual OS's?

---

### Post by grahammechanical on 2016-02-28
> What do you mean the default OS providing it?  Since I installed the  bootloader into the efi boot partition doesn't that separate it from the  individual OS's?

To understand what the situation is please do a little experiment. Load into Lubuntu & Xubuntu and use the file manager to access /boot/grub. Is there a file called grub.cfg?

There should be. If you open that file in Gedit (or whatever text editor is used in Lubuntu & Xubuntu) and go to the section that is headed by this

> ### BEGIN /etc/grub.d/10_linux ###

You will see the menu entries for the Grub boot menu. The Lubuntu grub.cfg will have Lubuntu as first in line & the Xubuntu grub.cfg will have Xubuntu first in line. You can check this by looking at the set root = line. In each case it will point to the partition each OS is on.

Now. if Grub (in the efi boot partition) is looking for grub.cfg in the Xubuntu /boot/grub/ and you delete the Xubuntu partition Grub will not find its configuration file and you will have a broken Grub boot loader.

The same situation will apply if Grub in the efi boot partition is looking for grub.cfg in the Lubuntu partition or in the Linux Mint partition.

You must load into the Linux distribution that you want to be in control of grub and run

```
sudo grub-install /dev/sda
```

Assuming that you only have one hard drive. If you have two hard drives & Lubuntu is on the second hard drive (sdb) you run

```
sudo grub-install /dev/sdb
```

Then run

```
sudo update-grub
```

Test to see if Lubuntu is first in the boot menu. If it is, then remove the other Linux distributions and load into Lubuntu & run 

```
sudo update-grub
```

again to remove the entries for those now deleted Linux distributions from Grub's boot menu.

The command sudo update-grub updates the grub.cfg of the Linux distro that you loaded into. But if that Linux distro is not in control of the Grub in the efi boot partition nothing will change in the Grub boot menu.

Regards

---

### Post by sukelis on 2016-02-29
grahammechanical - thank you, thank you, thank you!  Your experiment was very helpful in sorting this out for me.  Since I had done Something Else installs and specified /dev/sda1 for the bootloader for everyone, I was really convinced that they were all sharing.  But now I understand that besides the efi boot partition, each distro has it's own /boot folder.  So there are essentially 4 boot folders, well, technically I guess that would be 1 boot partition and 3 boot folders (and we're just ignoring windows).  I had thought they were all mounting /boot on the efi partition, kind of like they do with swap.   Instead they're mounting efi under boot, so they all see the same /boot/efi but not the same /boot/grub.  Big difference.  Now I'm guessing that the "bootloader" that gets put into the efi partition isn't the thing that executes the full boot process but rather something like a traffic cop that tells it where to go.  And I obviously didn't understand that even when I boot a different distro the traffic cop still belongs to the default distro.

I have run the grub-install from lubuntu, and then the first update-grub.  My grub menu now has lubuntu first/default, then Windows and the other linux distros.  I have rebooted and it came up in lubuntu without having to arrow through the list (woohoo!!  happy!  happy!)  

So now to get rid of xubuntu I need to delete the xubuntu partitions and then run update-grub again to get rid of the [then] orphaned entries.   

Again, thank you so very much for taking the time to break this down this way - it was brilliant!  Thanks also to Dennis N for pointing out that I had a flaw in my understanding; probably saved me hours of frustration!

---

