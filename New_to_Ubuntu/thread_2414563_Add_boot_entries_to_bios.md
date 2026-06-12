---
title: "Add boot entries to bios?"
date: 2019-03-12
forum: New to Ubuntu
---

### Post by francktheminer on 2019-03-12
Hey,
I own a Lenovo y50-70 Laptop, and I had triple boot set up on it (Windows, Kali, and MacOS).
When I was installing Ubuntu over Kali, I noticed that both had GRUB entries on my boot menu, so I went ahead and deleted their folders on the EFI folder... As you may imagine, I'm new to linux, so I ended up somehow deleting ALL boot entries... Thankfully, I had a feeling that could've happen, so I backed up the EFI folder before I did anything, except for the Kali and Ubuntu folders (didn't want those anyway). Problem is, somehow even with all the needed bootloader files (including the *****.efi files), when I try using bootmgr (or whatever the name of the linux command is, they never save to the bios, and I currently have two unusable os's (I've since reinstalled Ubuntu on the partition it was in). I can't create any Windows Install Media, as I've lost my flash drive that was bigger than 4Gb, and the install media is 4.something Gb...

TL;DR: Have all files from the EFI partition, still can't get them to show up on my BIOS menu, can only use ubuntu.

Can anyone try to help me?

---

### Post by francktheminer on 2019-03-12
Ok, after some thinking I managed to add them to the BIOS, Clover at least seems to work, but the Windows Boot Loader entry tells me there's no OS for some reason... I have gone through this once, I think it's a BCD problem, but I never managed to get the fix to work, and it would require me to use the Install media, which as stated above is kind of impossible to happen at the moment... Does anyone know how I can fix it?

---

### Post by yancek on 2019-03-12
Could you at least from Ubuntu, run the command and post the output so we have some details to work with:

> sudo efibootmgr

Have you tried 'boot repair' software.  You can get it at the site below, use the 2nd option on the page to download the ppa and follow the instructions.  When you run it select the option to Create Boot INfo Script and do NOT try to make any repairs.  Post the resulting link here so members can view it as it will show details on your drives/partitions OS files and EFI files.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Exactly how did you delete the boot entries for Kali and Ubuntu, from which OS?  How did you try to save/copy your saved EFI boot files back to the EFI partition on the drive?  Which OS did you use?  How, terminal, GUI?

> I can't create any Windows Install Media, as I've lost my flash drive that was bigger than 4Gb, and the install media is 4.something Gb...

If you are able to boot Ubuntu, you can create a 4/5GB ntfs partition and extract/cop the windows iso and use it to install but that' a somewhat convoluted process and it may be easier to diagnose the current problem.

---

### Post by oldfred on 2019-03-12
Thread Closed.

We do not support violation of Apple's terms of use. Which does not allow use of the Mac operating system on any other PC.

You agreed to Code of Conduct as part of signing up for forum.
       [http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)
Ubuntu Forums Code of Conduct
[http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)

---

