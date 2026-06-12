---
title: "Microsoft Excel files corrupted in Ubunut"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by tdapower on 2011-09-14
[SIZE=3][COLOR=Blue][SIZE=2][COLOR=Black]I'm using Ubuntu 10.10 version and I face serious problem in Ubuntu with Microsoft Excel files(.xls). There are some files which I maintained daily. But earlier times, some of those files corrupted nearly once a month. But recently those files are corrupted regularly(like once a two or three days). Please tell me which could be the cause for this problem and how could I overcome them.[/COLOR][/SIZE]
[/COLOR][/SIZE]

---

### Post by Wim Sturkenboom on 2011-09-15
Can you describe the corruption?

I don't have the solution, but a possible workaround can be to save them as csv files.

---

### Post by tdapower on 2011-09-15
> **Wim Sturkenboom said:**
> Can you describe the corruption?

I don't have the solution, but a possible workaround can be to save them as csv files.

I'm taking backups, But I need to know the reason for corruption to prevent further. The corruption is like most of the data in the file are missing and some are there. But some text parts are missing and original texts are replaced by various symbols in the remaining data.

---

### Post by 3rdalbum on 2011-09-15
Go into Disk Utility and look at the SMART data for your disk. If there's anything there that has failed a test or has a warning next to it, that's probably your corruption problem.

Otherwise, click the Check Filesystem button in the main Disk Utility window.

---

### Post by tdapower on 2011-09-15
> **3rdalbum said:**
> Go into Disk Utility and look at the SMART data for your disk. If there's anything there that has failed a test or has a warning next to it, that's probably your corruption problem.

Otherwise, click the Check Filesystem button in the main Disk Utility window.

Thanks for your advise, I done a test and revealed that there are some bad sectors on the disk, Is that the cause for file corruption?

---

### Post by grahammechanical on 2011-09-15
Are you editing these files in both Excel and Openoffice/Libreffice (or some other Linux spreadsheet program)?
The fonts you use for a document in Windows will not be available in Ubuntu and a substitute font is used which may not have the same characters as the Windows fonts.

Have you copied your Windows fonts over to Ubuntu and installed them?

Regards.

---

### Post by 3rdalbum on 2011-09-15
> **tdapower said:**
> Thanks for your advise, I done a test and revealed that there are some bad sectors on the disk, Is that the cause for file corruption?

If the Reallocated Sector Count value is greater than the Threshold, then it means that you may start to lose data.

Every disk has a couple of spare sectors. If one regular sector goes bad, the disk automatically copies its data to a spare sector. It also remembers which sector is bad and does not write to it ever again. When the disk runs out of spare sectors, if any more bad sectors develop then you may lose the file that spans that bad sector.

So yes, it's possible that the bad sectors have caused this file corruption. It's also still possible that ordinary filesystem corruption has caused the file to become corrupt too. Back up the file and any other really critical files that you have, and then run the filesystem check in Disk Utility.

---

