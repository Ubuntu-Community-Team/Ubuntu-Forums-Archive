---
title: "[SOLVED] Does it matter what my partition names are: sda/sdc?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by snuffy on 2008-11-30
I have just created the following partitions using the live CD on Intrepid. I had no control over the partition names (sda/sdb etc):

/dev/sda
sda1 /Home ext3 (200GB)

/dev/sdb
sdb1 Backup ext3 (200GB)

/dev/sdc
sdc1 Windows NTFS (20GB)
sdc2 Ubuntu / ext3 (20GB)
Linux-swap (2gb)
sdc3 Downloads ext3 (40GB)

I haven't installed anything yet.

It doesn't seem logical that my partitions for operating systems are on sdc. 

Should they be on sda? 

will this cause trouble when ubuntu installs grub? 

will it try to put it on sda1? 

how can i swap my partition naming so that sda is my operating systems? 

If i have to do it manually in step 7 of the ubuntu gui setup, where should grub go?

Thanks.
Tim.

---

### Post by kestrel1 on 2008-11-30
Just let Ubuntu sort it. It knows what it is up to & it won't cause a problem.

---

### Post by CatKiller on 2008-11-30
> **kestrel1 said:**
> Just let Ubuntu sort it. It knows what it is up to & it won't cause a problem.

++

The control you had over the drive names was when you put them in the computer. IDE devices are named by which channel they're on; Primary Master, Primary Slave, Secondary Master, Secondary Slave. I guess SATA drives are named by the socket they're plugged into.

It doesn't matter in the slightest. Well, Windows used to complain if it wasn't on the Primary Master if there were other drives it could see before it, but Windows complains about a lot of things. I don't think it's a problem these days. And Windows can't see your Primary drives in any case.

---

### Post by The Cog on 2008-11-30
I assume these are 3 hard disks? If so, that arrangement looks reasonable. 20G is a sensible size for the Ubuntu system so if there's a 20G hole available in sdc that's just right.

What is the second column in your post? If it's the mount point, /Home should be /home (lower case 'h') and you need to say /Backup not just Backup although I would probably choose /mnt/backup myself.

I think GRUB normally goes on sda wherever you out the OS, because it is sda that the PC will bootload from.

---

### Post by CatKiller on 2008-11-30
> **The Cog said:**
> I think GRUB normally goes on sda wherever you out the OS, because it is sda that the PC will bootload from.

Not necessarily. It's entirely dependent on the BIOS. Some BIOSes let you explicitly set the boot order of the hard drives with "HARD DRIVE 0", "HARD DRIVE 3", and so on, whereas others will just have "HARD DRIVE", "CD-ROM" and will go through each occurrence of each type of hardware until it finds something it can boot from.

Putting GRUB's Stage 1 on a different MBR to the drive that has the partition with the rest of GRUB on seems a bit peculiar to me. If you remove either drive, the other drive won't boot. At least if you have GRUB in the same MBR then the ability to boot from a drive travels with that drive.

I think the OP's descriptions were just that; human-readable. I don't think they were output from anything.

---

### Post by snuffy on 2008-11-30
sorry, my mistake, yeah, i meant /home (lowercase), and Backup as in that's what it's for, not the mount point.


> **The Cog said:**
> I assume these are 3 hard disks? If so, that arrangement looks reasonable. 20G is a sensible size for the Ubuntu system so if there's a 20G hole available in sdc that's just right.

What is the second column in your post? If it's the mount point, /Home should be /home (lower case 'h') and you need to say /Backup not just Backup although I would probably choose /mnt/backup myself.

I think GRUB normally goes on sda wherever you out the OS, because it is sda that the PC will bootload from.

---

### Post by snuffy on 2008-11-30
Hmm, turns out ubuntu didn't like my partitions. after install it simply booted straight into windows. 

i unplugged my other hard drives, and tried again, this time it worked. i then plugged my hard drives back in.

seems ok now. thanks all.

will have to work out how to set one of my other drives to /home now.

cheers.

---

### Post by The Cog on 2008-11-30
> **CatKiller said:**
> ... whereas others will just have "HARD DRIVE", "CD-ROM" and will go through each occurrence of each type of hardware until it finds something it can boot from.
You mean it will check each hard disk in turn looking for a bootable one? Somehow I had not imagined that PCs would do that. Aren't all drives bootable, even if it's only a bit if code that prints Invalid disk or disk error, press F1 to continue?

---

### Post by CatKiller on 2008-11-30
> **The Cog said:**
> You mean it will check each hard disk in turn looking for a bootable one? Somehow I had not imagined that PCs would do that. Aren't all drives bootable, even if it's only a bit if code that prints Invalid disk or disk error, press F1 to continue?

No. It's actually quite complicated to get a disk to be bootable. Launching a program when there's nothing running to launch that program with is a tricky problem to solve. Thankfully, it's already been solved. This process used to be called "bootstrapping," as in "pulling oneself up by one's bootstraps." Now it's just called "booting."

Floppy drives can have a small part of an Operating System on them. Hard drives can have a tiny bit of code in the Master Boot Record that when executed load another bit of code - together these bits form the bootloader that is able to load an Operating System. The Master Boot Record is tiny, which is why the bootloader has to be in multiple parts. I don't know how CD-Roms work, but I'd imagine that it's similar to how floppy disks work.

These tiny bits of code only serve to load the next bit of code, until eventually you end up with something in memory that can actually do something useful. It starts with the BIOS of the motherboard, that looks in places defined by the boot order and executes what it finds there. That executes the next bit, and so on.

That error message is provided by the BIOS when it is unable to do its part of the process.

---

### Post by CatKiller on 2008-11-30
> **snuffy said:**
> will have to work out how to set one of my other drives to /home now.

You could have done so as you installed Ubuntu - it asks you the mount point of the partitions you selected. You'd select the one that you want to be /home and tell it to mount it at /home. The same as you did (but possibly didn't notice doing) for /.

There is a guide [here]("http://www.psychocats.net/ubuntu/separatehome") that you might find contains useful information on how to change it now that you've got Ubuntu installed. You might find that you can re-install Ubuntu in the time that it takes to digest that guide though :)

As I intimated in the post above, the boot process is quite complicated, with different options for each stage of the process. The bootloader that you use could be GRUB, LILO, or Windows' own bootloader, NTLDR. It's also possible to chain these bootloaders together, so the BIOS loads GRUB, which then loads NTLDR - this is the usual way of doing a dual-boot with Windows. It sounds like you may have initially had the BIOS loading NTLDR, which then didn't do anything but load Windows, since Microsoft likes to pretend that Windows is the only Operating System possible. GRUB is perfectly capable of loading Ubuntu or Windows.

I'm glad you've got it set up how you wanted, though.

---

### Post by snuffy on 2008-11-30
yeah, many ways to skin a cat i guess. thanks again all. 

tim.

---

