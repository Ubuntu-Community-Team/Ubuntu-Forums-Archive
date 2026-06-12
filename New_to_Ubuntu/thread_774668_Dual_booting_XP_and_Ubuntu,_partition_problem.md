---
title: "Dual booting XP and Ubuntu, partition problem"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by alex0207 on 2008-04-29
Hey guys, 

So i've been hearing all this hype about the new Ubunut 8.04 and i wanted to try it out. So i've treid the Live CD and i like it, very much. Now i want to dual boot XP and Hardy Heron.

Right so i need to resize my partition, so i've looked on the computer management in XP and found this:
[IMG]http://i170.photobucket.com/albums/u266/Moreton02/untitled.jpg[/IMG]
Now what the hell does this mean? I've got 4 partitions?

Hehe, yup thats Daniweb in the background, dunno why i thought that would be the first place i should post for help...

What is the 2.75 Gb of space that is unknown, how do i correct this?

Since i'm guessing that you can access all your XP files from ubuntu, i only need to create a partition big enough for the actual Ubuntu OS, and upgrades, not any files. 

I've looked at the manual on the ubuntu website, and it explains that you can resize the existing partition, but i think i need to get the existing partition to use up the extra space, ie. the 7Gb of unallocated space and the 2 Gb of unknown partition

---

### Post by free2useemail on 2008-04-29
Ubuntu 8.04 is amazing (defently with the new KDE 4.0) Having two operating systems on your computer is awsome, i have done it with vista and XP, but with Ubuntu and XP??? This is really hard unless you really are good at a command line. I would recommend trying wubi. Search for wubi. Download that, then pick the OS you want to install (OH, just read the directions once you download it)

As for duel booting, it is possible to install linux first then windows XP, but you will have to repair ubuntu's boot file after the install of XP, which can get crazy

---

### Post by neurostu on 2008-04-29
To answer the posters question:
the 2.7 GB partition is a restore partition. Most manufacters put them on the HDD so you don't need windows install cd's to restore your system.  

That ~7GB partition should be plenty of space to install ubuntu.

What you can do is open the Partition Manager on the live cd (System-->Administration-->Partition Manager) to resize your partitions, but be sure to back up everything.


If I were you I would delete the 2.75 gb partition and I wouldn't touch the first or the windows partition (also when you install grub (the linux boot loader) you probably won't be able access this recovery partition anyway, also installing with an XP disc is always easier).  Theoretically gparted can move and manage partitions without problems, but this doesn't always happen in practice.  Then when you install ubuntu use the free space to create a new EXT3 partition and install ubuntu there.

---

### Post by enigmaniac23 on 2008-04-29
Check out this tutorial on how to dual boot with XP and Ubuntu, if you have XP already loaded (which you do)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by neurostu on 2008-04-29
*

---

### Post by alex0207 on 2008-04-29
Ah that makes sense, yea i've looked at Wubi and that looks so much easier. Cheers. It doesn't even need a seperata partition, and you can still "dual boot" effectively?

Although i have heard of loads'a problems when using a 8800GT graphics card when using this new ubuntu, i have one of these, and how likely am i to have a massive problem?

However, i still would like to know what thse wierd extra partitions are, is it possible to combine them with my existing XP install partition so i get the extra 10Gb of space?

---

### Post by shearn89 on 2008-04-29
Its simple - you just need to make sure you go slow.
Boot into the live cd, hit alt-f2 and type "gksudo gparted". This will open the partition editor, and allow you to move and create partitions. BE CAREFUL! this is dangerous, and you could wipe your windows install. Backup data first. 

You want to resize a partition with lots of space, and create a partition of at least around 6gb in the space. Format it as ext2. If you can, make a "swap" partition of at least the size of your RAM in some free space. format it as linux-swap. REMEMBER THE NAMES OF THESE! they'll be something like sda3 or sda4 etc.

You can get to windows partitions from ubuntu, but it requires installation of seperate modules, so i'd recommend just keeping it for internet and email etc, until you can make the switch fully. 

I can't see your images as i'm behind a firewall, but there may be OEM recovery partitions on your windows install.

If you don't want to install the extra modules, you'll need about 10gb for basic usage (ie, not loads of music and games etc).

Once you're done with the partitioner, hit apply to apply the changes. It may take a while. Then run the installer, and when you get to the bit about partitioning, choose manual, and tell it to put "/" on the large ext2 partition, and "swap" on the small swap one. Then continue as normal, and your done! Before you boot back into windows you'll have to edit /boot/grub/menu.lst and check that there's an entry for windows there, but it might do it automatically. Ubuntu needs to be installed after windows, otherwise windows nerfs the boot loader, and you can't boot back to ubuntu.

EDIT: too slow at typing! you can probs view those extra partitions from inside ubuntu, and see whats on them.

---

### Post by Hamchan on 2008-04-29
Dual booting Ubuntu and XP is incredibly easy. This is my first attempt at linux and I was able to dual boot very successfully.

Be sure to defrag your windows partition before you do any sort of resizing of it (if you decide to resize your windows partition), but that 7 gig part should be enough. Ubuntu doesn't take up much space.

---

### Post by neurostu on 2008-04-29
alex0207:
Did you read my post?

the 2.75 gb partition is a restore partition.
the 63 mb partition is for booting the restore partition.
the free space is probably so they could sell you a 150gb HDD labelled as a 140gb hdd

---

### Post by alex0207 on 2008-04-29
> **enigmaniac23 said:**
> Check out this tutorial on how to dual boot with XP and Ubuntu, if you have XP already loaded (which you do)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Hmm yea i think i've read that before, cheers i was looking for something like that!

Wicked, so there is no real partition stuff that i need to do, other that resize the existing one on the LiveCD! Wicked, i didn't know that i thought i had to do some really complicated partitioning on XP first...

And i'm guessing installing it like this will make it run faster than if it was installed using Wubi?

But what about these odd extra partitions that i have, are they needed?

---

### Post by neurostu on 2008-04-29
I personally have never used WUBI but people are having mixed experiences with it.  Yes all you really have to do is resize the NTFS (windows) partition, then create a EXT3 partition in the blank space.  Then install Ubuntu to this partition.

Keep the first partition, its only 63 mb and it will be a pain if you delete it b/c you will have to move your XP partition to recover the lost space (this will take a TON of time a couple hours).  But feel free to delete the 2.75 gb partition as its a stupid recovery partition.

Good luck!

---

### Post by alex0207 on 2008-04-29
So start up the Live CD and combine the 2.75Gb and the 7Gb partition to make 10Gb and install on there?

Man, sorry but i'm a real Noob with partitions, some help with this would be great!

---

### Post by Hamchan on 2008-04-29
Don't forget to defrag your windows partition before you resize. It's possible to cut off some valuable (necessary) files if you don't. I forgot once and now XP can't find my network card.

---

### Post by neurostu on 2008-04-29
Listen, DONT RESIZE YOUR XP Partition. Your just testing out Ubuntu for now.  All your music, pictures, videos, etc... can stay on your XP partition. Until you know you are going to need more space on your Ubuntu installation leave your XP partition alone.  I really screwed up a XP partition by resizing it. I also have resized several without problems.  As a noob I would advise against resizing your XP partition.

Yes, delete the 2.75 gb partition and install Ubuntu on the left over 10gb. That should be more then enough.

---

### Post by neurostu on 2008-04-29
Hamchan: Did you try reinstalling the drivers for your network card?

---

### Post by alex0207 on 2008-04-30
Right okay, i've deleted the spare 2 Gb partition and now i have 10 Gb of unused space. 

So i go into the installer and i don't want to resize my XP partition, i want to use the unused space. So do i go into manually choose a partition?

Anyway thats what i did, and i select this partition and it says specify a mount point, whats that? I've read somewhere that you need to split up the partition into 3 partitions, the swap, root and home or something, but i don't know what the hell im doing...

Cheers

---

### Post by alex0207 on 2008-04-30
Or do i select "use the largest continuous free space"?

---

### Post by neurostu on 2008-04-30
Select the unused space and set the mount point as "/" and format it to ext3.

Don't worry about a /home partition.  You really only need 2 partitions a Filesystem partition (the ext3) and a swap (similar to virtual memory in windows). But really for now you don't need the swap if you have a decent amount of ram (>=1gb). In the future when you move to a mainly linux system you will want to create a swap partition, but until then you can live without one.

---

