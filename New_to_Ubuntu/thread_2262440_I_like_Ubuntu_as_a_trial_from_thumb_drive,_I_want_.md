---
title: "I like Ubuntu as a trial from thumb drive, I want to dual boot . Now what?"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by dave166 on 2015-01-24
Hello Everyone,
 I'm a green as can be newbie to Ubuntu so if my questions are silly or if there is a better way, just let me know. I want to get the best ideas from more experienced users. Let me give you a little about how I have come to this point. I have been a Windows user forever it seems. My desktop ran XP and now that it has been retired I have been using Ubuntu from a thumb drive. I like Ubuntu so far but I have not made many changes or customizations. I have bought a laptop with Win 7 installed but I want to dual boot in a Ubuntu/Windows setup. I would like to have each OS in separate partitions and a data partition to share between Ubuntu/Windows so that I can upgrade OS's without removing my data.
  Laptop specs i7pentium processor,8GB RAM,1TB 5400rpm HDD, Win 7 Home Premium 64-BIT, Sager brand.  Since this is much newer than my desktop, I want to set it up as a dual boot before I move any of my data over to it. With a 1TB HDD ,how much space should I allocate to Windows7 and Ubuntu? Anything that I am forgetting or need to know about this kind of setup? I will probably upgrade to Windows10 in the future and Upgrade Ubuntu as needed. I figure that each OS in its partition can be set Windows7 and data partitions as NTFS and Ubuntu partition in ext4. Are these the correct formats?
  Thanks,
   Dave

---

### Post by Bucky Ball on 2015-01-24
Welcome. You're thinking is so far, so good.

I have Win7 on a 40Gb partition, but I hardly use it and don't have a lot of apps installed. You might go for 50Gb. Ubuntu needs 20-25Gb at the most if you're keeping your data elsewhere. I've never used more than 15Gb, but use a minimal install. Before that I used straight Xubuntu which is lighter and smaller than Ubuntu. 

Win7 is probably on a giant partition which uses the whole disk, or a lot of it, so the first thing you'd want to do is shrink that using the disk management tools in Windows. DON'T use Gparted in Ubuntu on the Live disk/USB (the one you would use to install) for resizing Win7 partitions. If you haven't done much with Win7 to date, then defragging prior to resizing probably isn't necessary. If you have, defragment the partition before resizing.

So, you might end up with something like this and in this order from the beginning of the drive (Win first partition):

Win7 - 50Gb partition at the beginning of the drive, NTFS;
/ = the partition where Ubuntu OS goes, 20Gb, EXT4;
/data = as large as you like. NTFS;
/swap = same as a pagefile for Ubuntu, generally 2Gb, but if you need/want to hibernate, it should be the same size as the installed RAM, in your case, 8Gb. 

There's a start. 

Pre-installed Win7 uses UEFI rather than BIOS. Prior to installing Ubuntu, boot into Win7 and switch off hibernation/faststart. This can cause problems as if Win7 is hibernating then Ubuntu will not see it's partition during the install. 

You'll obviously have more questions as you go and I can move the thread to ***Installations & Upgrades*** a bit further down the track where you will probably get more support, but for now, good luck and any more questions, just ask. 

Just a tip: You'll get better support using paragraphs in your posts. Many will not bother to read 'wall of text' posts and will move on. ;)

PS: While Win uses the convention hd0, hd1, etc, for partitions, the Ubuntu equivalent would be sda1, sda2, meaning first drive, first and second partitions respectively. Just thought I'd mention to avoid confusion.

---

### Post by dave166 on 2015-01-25
Thank you Bucky! Your help is much appreciated. I will also try to use better structure in my posts to make things clearer and organized. Regards, Dave

---

### Post by nerdtron on 2015-01-25
What model is your laptop? Does it use UEFI?

For some laptops and computers, dual booting can be as simple selecting "Install Alongside Windows" option on the Ubuntu installer.
On some newer laptops however, sometimes encounters errors on their reboot so let's see what your laptop model is.

---

### Post by Mark Phelps on 2015-01-25
BEFORE you launch into the dual-boot setup, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  You will need that later to recover the boot loader if problems are encountered during the dual-boot setup.

---

### Post by Jonathan Precise on 2015-01-25
> **dave166 said:**
> With a 1TB HDD ,how much space should I allocate to Windows7 and Ubuntu?

Hello dave166.

Answering your specific question, I have 153 GB for Ubuntu, and it is sufficient for me, but need at least 300 GB for Windows because it is a memory/space hog. But again, I have a 500 GB drive.

I recommend you make Windows 500 GB, leave 200-300 GB for Ubuntu, and the rest for all of your data (about 100-300 GB).

[QUOTE=Mark Phelps]BEFORE you launch into the dual-boot setup, use the Backup feature in Win7 to create and burn a Win7 Repair CD. You will need that later to recover the boot loader if problems are encountered during the dual-boot setup.[/QUOTE]

+1 This. Also, depending on your brand/model you might have an option to make recovery disks/USBs to recover in case of disaster. Recovery partition does the same, but if the manufacturer lets you move your recovery partition(s) to a USB disk, I prefer it because if you do, you can delete the HDD recovery partition(s) it frees space and let's you use (almost) all the disk. Listen though: Just DON'T DELETE EFI FAT32 PARTITION (if you have UEFI) OR YOUR SYSTEM WILL BECOME UNBOOTABLE!!!, requiring recovery, deleting everything you have come to know (except your Windows look and feel if you haven't tweaked it with some LiteStep/WindowBlinds...). Also:

[QUOTE=nerdtron]What model is your laptop? Does it use UEFI?

For some laptops and computers, dual booting can be as simple selecting "Install Alongside Windows" option on the Ubuntu installer.
On some newer laptops however, sometimes encounters errors on their reboot so let's see what your laptop model is.[/QUOTE]

+1 to this too. Manufacturer/Brand/Model would be nice, it can help us guide you further.

---

