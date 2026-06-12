---
title: "Boot-Repair made things worse."
date: 2019-08-14
forum: New to Ubuntu
---

### Post by mechadrake on 2019-08-14
I made recommended repair with boot-repair program and now my windows installation works but linux is dead by kernel panic due to tryindgto mounts vfs from unknown 0,0 block. 
Before I had to select linux or windows from uefi menu and both worked. Just windows partiton had just win boot and linux had only linux one (that one got messed up when trying to restore working boot prompt before windows ate it when it installed win 10 unannounced).
And the grub menu is filled with strange options I have never seen before. Those got added out of the blue. 
Boot-Repair pastebin link: [http://paste.ubuntu.com/p/kBvZPVd895](http://paste.ubuntu.com/p/kBvZPVd895)

---

### Post by oldfred on 2019-08-14
You are not showing any initrd.img-4.4xxx either in boot stanza or list of files. You should have one for each kernel.

Is this a Dell with pre-installed Ubuntu? And upgraded from 14.04 to 16.04?

Boot-Repair adds 25_custom for other .efi bootable files. You can edit or delete those entries.

Make sure you  have good backups as your configuration has some customized settings that are in your Dell grub settings. If not for that, I would suggest a full reinstall of grub using Boot-Repair's advanced options. But then you would lose those custom settings.

---

### Post by mechadrake on 2019-08-15
Yes, this dell had that ubuntu preinstalled. Version 16 just failed to upgrade though. Still worked fine as older version. I have probably rewritten custom dell grub entries while trying to restore grub from command line, I guess the instructions I followed were incorrect, because I did not get back my old grub prompt but only ubuntu boot options, again without windows. It still worked by mashing f12 and selecting u untu or win, but that laptop is used by my not tech savy relative, ant that is nit accceptable... Broke it with that boot repair. I am unclear how do I fix it now, that I am missing those initrd images... Just reinstall the grub from advanced? Boot repair threatens me with bad stuff on that :D I guess I need now to do the drive image on that laptop, that is not what I wanted to do :(

---

### Post by oldfred on 2019-08-15
Not sure you need full drive image. Some prefer that.

But I would be sure to back up /home, /etc & list of installed apps.
And grub settings including /boot/grub/grub.cfg, /etc/default/grub & /etc/grub.d folder with grub scripts.

Boot-Repair in its advanced mode has the full reinstall of grub & most recent kernel.
But not sure if your have upgraded, or not or are somewhere in-between which can cause issues. Report's title on sda4 is 16.04.6. And you have newer kernel, but it seems like not all the boot files. Not sure then what else may be missing.

Part of issue may be that sda4 is at 98% full. Your NTFS partition in sda5 is also very full at 94%. NTFS gets extremely slow if only 10% left, it really likes 30% free to work well.

So if upgrade ran out of space then it did not complete. Best to do a major houseclean or backup & remove some of data in sda4 (and sda5).

Your Windows also is on a gpt partitioned drive. But it shows the old BIOS boot files in the partition? Did you copy a Windows into that partition?

Be sure to use Ubuntu live installer for 16.04.6, add Boot-Repair and boot in UEFI mode for all repairs. Your 14.04 is EoL - end of live or obsolete and repository is closed so even fixes to it are now very difficult.

---

### Post by joris_donders2 on 2019-08-16
Wouldn't a fresh install of Ubuntu 18.04.3 (new kernel / more drivers included/  HWE / better display drivers ..... ) be a better option ? 
With a live session you can save your data on an extern medium (large Gb stick, or removable HD, ..... ) and do a fresh install. 

Or is this a dual boot system ?

---

### Post by mechadrake on 2019-08-16
I am not sure what is going inwith wi dows actuallly, it boots now and booted always. It just one day booted with win 10 instead of perfect and fast win 7, I guess my sister did not kill microsoft suggested upgrade... It messed up partitions and ate a lot of space with old and new win files. 
Will do space cleaning before anything else. Had once before already moved files to free up space so ubuntu would boot.
I am using lubuntu 19.04 live install to look at things/fix things, is it too new to work on the eol ubuntu/incompatible?

---

### Post by mechadrake on 2019-08-16
This is dual boot system, trying to do the file saving thing, with lubuntu 19.04 live stick... 
Trying to rebuild the system for a user who is used to how it worked before... I use manjaro on my micro laptop which is my third computer I use, besides two different win desktops. I have different oses all the time, just the first time grub broke on me like that...

---

