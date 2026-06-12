---
title: "Uninstalled Ubuntu, now cannot see hd it was installed to in windows"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by hemfill on 2008-06-29
I have two hard disks, which used to be categorized as C: and D: under vista. (C: is where i kept my music and movies and vista installation, D: is where i kept my video games) 

Earlier today i installed ubuntu onto D: but when i booted back into Vista i noticed that i could no longer access D; it wasn't showing up at all in windows explorer. So i downloaded GParted and deleted the ubuntu partition (and i fixed the MBR so it loads into vista fine). but i still can't see the drive formerly labeled as D:. 

The data on drive D is not very important. I can just wipe it and reformat it if i really need to. But it would be a big pain to reinstall all my old games, and i would lose all of my saves. So i wanted to know if there was an easy way to fix this problem within vista (which is what i'm using to write this message). 

Also, my ultimate goal is to recover the D drive and partition it again so that I can reinstall ubuntu onto that smaller partition. Is this the right course of action? (I basically want a small, secure ubuntu that i can boot into occasionally but not do all that much on aside from browse the web)

---

### Post by iaculallad on 2008-06-29
> **hemfill said:**
> I have two hard disks, which used to be categorized as C: and D: under vista. (C: is where i kept my music and movies and vista installation, D: is where i kept my video games) 

Earlier today i installed ubuntu onto D: but when i booted back into Vista i noticed that i could no longer access D; it wasn't showing up at all in windows explorer. So i downloaded GParted and deleted the ubuntu partition (and i fixed the MBR so it loads into vista fine). but i still can't see the drive formerly labeled as D:. 

The data on drive D is not very important. I can just wipe it and reformat it if i really need to. But it would be a big pain to reinstall all my old games, and i would lose all of my saves. So i wanted to know if there was an easy way to fix this problem within vista (which is what i'm using to write this message). 

Also, my ultimate goal is to recover the D drive and partition it again so that I can reinstall ubuntu onto that smaller partition. Is this the right course of action? (I basically want a small, secure ubuntu that i can boot into occasionally but not do all that much on aside from browse the web)

Remember that by default, ALL m$ windoze versions cannot access Ext2/Ext3 filesystem. Try installing the Explore2Fs application in your vista to access your Ext2/Ext3 drive (Formerly of your Ubuntu application).

Try to boot from your LiveCD first to check if that drive still has your Ubuntu partitions. You could use the LiveCD to reformat it back to NTFS partitions if former data's are not important to you.

---

### Post by lwvmobile on 2008-06-29
I don't know, it sounds like you already formatted your old D drive when you installed Ubuntu. If that hard drive had only one partition, and if not mistaken you cannot install the root of Ubuntu onto NTFS, it was most likely formatted to EXT3 upon installation.

Can you right-click on my computer in windows, go to manage, and then get a screen cap of disk management? That would answer a few questions.

---

### Post by bobbob1016 on 2008-06-29
The reason you couldn't see the D: drive anymore was because Vista, or any Windows for that matter, doesn't read Linux filesystems without the driver.  When you deleted the Ubuntu partition, you didn't give the drive any filesystem, so Vista doesn't show you a D: drive.  What you should do, is since you said you were reinstalling Ubuntu, run the LiveCD, boot and partition the drive with whatever you want for Ubuntu, I'd say 10gig for everything, you could go to 4 or 5gig though.  Then leave the rest either blank, or fat32 (you can make fat32 in the installer).  Vista and Ubuntu have no issue reading/writing fat32.  You can't get files over 2 or 4gig, not sure which though.  You could do NTFS, but it isn't 100% in my opinion still, it's 99.9999%.  As in you can read/write just fine, but only if Windows was shut down safely.

---

### Post by Victormd on 2008-06-29
> **hemfill said:**
> Earlier today i installed ubuntu onto D: but when i booted back into Vista i noticed that i could no longer access D
When you installed ubuntu, how did you do this? If you installed in D, then you formatted it to change from NTFS to EXT3.

> **hemfill said:**
> it wasn't showing up at all in windows explorer. So i downloaded GParted and deleted the ubuntu partition (and i fixed the MBR so it loads into vista fine). but i still can't see the drive formerly labeled as D
You couldn't see the HD because it's formatted in EXT3 and windows doesn't recognize it. 

> **hemfill said:**
> The data on drive D is not very important. I can just wipe it and reformat it if i really need to. But it would be a big pain to reinstall all my old games, and i would lose all of my saves. So i wanted to know if there was an easy way to fix this problem within vista (which is what i'm using to write this message).
I don't think you have anything on your D partition anymore since you've deleted it in Gparted.

---

### Post by hemfill on 2008-06-29
[IMG]http://i28.tinypic.com/1zf5xso.jpg[/IMG]
basically the reason i am posting this is that i want to save the information on the disk. i know i can just reformat it.

---

### Post by king leoric on 2008-06-29
Have you installed ubuntu manually or you just select "next" by default. Because if by default, probably it was just resized. Or have you installed ubuntu using the WUBI installer? 

If you have done it manually, maybe you have already formatted D:. You can run the live cd again and check your partitions or drive because windows cannot access nor read linux:)

Hope it helps:)

---

### Post by hemfill on 2008-06-29
> **iaculallad said:**
> Remember that by default, ALL m$ windoze versions cannot access Ext2/Ext3 filesystem. Try installing the Explore2Fs application in your vista to access your Ext2/Ext3 drive (Formerly of your Ubuntu application).

this sounds like it'll fix the problem. you guys are really fast, thanks.

---

### Post by Victormd on 2008-06-29
Your 150GB partition, (guessing this was your D) has no file system, thus, no data to be saved. Looks like you did loose all your games... (you mentioned that you used gparted to delete the ubuntu partition so I'm guessing this is what happened.)

---

### Post by hemfill on 2008-06-29
> **Victormd said:**
> Your 150GB partition, (guessing this was your D) has no file system, thus, no data to be saved. Looks like you did loose all your games... (you mentioned that you used gparted to delete the ubuntu partition so I'm guessing this is what happened.)

i used the demo for this software: [http://www.partition-recovery.com/](http://www.partition-recovery.com/)
it said that i still had all the files on there, i could actually see the files but because it's just a demo it wouldn't let me copy them.

---

### Post by lwvmobile on 2008-06-29
Yeah, looks like no file system, thus no files, unfortunately. If it were EXT3 or any other unrecognized file system, it would say 'unrecognized' or similar were the file system denotation is in disk manager. Its just a healthy blank disk waiting for a format. 

Since it has already been formatted once I believe to EXT3, the chance of recovery is bleak. I would just go ahead and reformat with NTFS. If you want to try out Ubuntu though, I would recommend using Wubi, just put in the disk in Windows and it will auto run. Then you can install on your new D drive without having to worry about losing your data/file system.

---

### Post by hemfill on 2008-06-29
> **lwvmobile said:**
> Yeah, looks like no file system, thus no files, unfortunately. If it were EXT3 or any other unrecognized file system, it would say 'unrecognized' or similar were the file system denotation is in disk manager. Its just a healthy blank disk waiting for a format. 

Since it has already been formatted once I believe to EXT3, the chance of recovery is bleak. I would just go ahead and reformat with NTFS. If you want to try out Ubuntu though, I would recommend using Wubi, just put in the disk in Windows and it will auto run. Then you can install on your new D drive without having to worry about losing your data/file system.

im serious the demo for this software: [http://www.partition-recovery.com/](http://www.partition-recovery.com/)
showed me that the files were still there. and its not like it took half an hour to convert the drive into another format, the installation was really quick.

---

### Post by king leoric on 2008-06-29
Try this for recovery
[http://www.thefreecountry.com/utilities/datarecovery.shtml](http://www.thefreecountry.com/utilities/datarecovery.shtml)

haven't tried them though

---

### Post by lwvmobile on 2008-06-29
Well in that case I hope recovery works out for you.:guitar:

---

### Post by bobbob1016 on 2008-06-29
It is highly unlikely recovery will bring you anything back.  You should reinstall following my directions in my previous post, that will get you Ubuntu back as well as a partition Windows can read.  I would not suggest using the Windows driver for ext2/3, because if you get a virus of some sort, it could pass to your Linux, I highly doubt it, since it'd have to be Linux aware, but a Linux with a fat32/ntfs shared partition should do what you need.

Edit:  I noticed you said some software said your data was still there.  It is possible as I said, but unlikely.  It is even less likely that all of it is there, as in since you said you installed games there, crucial files could be missing.  I wouldn't suggest buying the software unless you know ALL your data will come back.

---

### Post by king leoric on 2008-06-29
> **bobbob1016 said:**
> It is highly unlikely recovery will bring you anything back.  You should reinstall following my directions in my previous post, that will get you Ubuntu back as well as a partition Windows can read.  I would not suggest using the Windows driver for ext2/3, because if you get a virus of some sort, it could pass to your Linux, I highly doubt it, since it'd have to be Linux aware, but a Linux with a fat32/ntfs shared partition should do what you need.

Edit:  I noticed you said some software said your data was still there.  It is possible as I said, but unlikely.  It is even less likely that all of it is there, as in since you said you installed games there, crucial files could be missing.  I wouldn't suggest buying the software unless you know ALL your data will come back.

Agree with this matter regarding virus and shared fat32/ntfs.

I don't agree however about buying such recovery tools. Try first the free tools and recover ONLY the important files. As for games installation, I believe resinstalling them would be the best option because you will also reinstall or fix registries.

---

### Post by Victormd on 2008-06-29
> **hemfill said:**
> i used the demo for this software: [http://www.partition-recovery.com/](http://www.partition-recovery.com/)
it said that i still had all the files on there, i could actually see the files but because it's just a demo it wouldn't let me copy them.

When you format a partition, depending on the level of formatting you use, all it does is remove your file allocation table (FAT) which is basically a list of all the files on your partition (a table of contents for your drive). If you don't write anything to that drive, then most of the times you can recover the data, and what most recovery softwares do, is try to recover your fiile allocation table and check the referenced files to see if they're intact, and if so, the software confirms them in your FAT.

From what I understood, when you installed ubuntu, this partition was formatted in EXT3 and part of the data overwritten by ubuntu so that portion will not be recoverable. Furthermore, you modified the file system from NTFS to EXT3 so I don't know if you'll be able to recover anything at all.

The fact that the software "sees" the files, does not necessarily mean that you'll be able to recover everything that it's showing.

With that said, recovery softwares do provide a means of recovering your data, to a certain degree. I don't know of any free or open source programs for this. You would have to see whether it's worth paying to try to recover the data in that partition or not.

EDIT: Just saw the link on a prior post showing a free recovery software. I would try that to see if you'll be able to recover instead of purchasing a software without being sure if it'll work or not.

---

### Post by bobbob1016 on 2008-06-30
> **king leoric said:**
> Agree with this matter regarding virus and shared fat32/ntfs.

I don't agree however about buying such recovery tools. Try first the free tools and recover ONLY the important files. As for games installation, I believe reinstalling them would be the best option because you will also reinstall or fix registries.

I wasn't suggesting buying the software, he said he had a demo, and I said it probably wouldn't work.

---

