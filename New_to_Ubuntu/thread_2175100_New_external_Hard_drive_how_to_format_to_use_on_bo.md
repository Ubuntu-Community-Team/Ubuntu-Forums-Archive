---
title: "New external Hard drive how to format to use on both ubuntu and windows laptops"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by Jacobin_Noir on 2013-09-17
I have attached a screenshot of dik utility showing the details of the drive. 
i am a noob but smart enough to follow instruction
thanks a lot

---

### Post by philinux on 2013-09-17
Welcome to the forums. Yep go with ntfs. Ubuntu can read that.

---

### Post by dankojoffrey on 2013-09-17
You can format it in Windows (NTFS) and you can be sure it is gonna work in both Ubuntu and Windows...

---

### Post by flyfishingphil on 2013-09-17
dankojoffrey---Just picked up the Seragate 1TB Plus external and am trying to get it to work with 12.04. Am I reading it right that all I need to do is plug it into windows and set it to run on NTFS so my laptop and Ubuntu 12.04 will recognize it? (Actually wanted to use it with my Toshiba tablet but that's another story!) 

Playing with my Toshiba AT11 and an older 160GB Maxtor external and found I can get into the files by going to file manager. Will play around a bit with the Seagate and see what happens.

---

### Post by Jacobin_Noir on 2013-09-17
so is it already ntfs. no need to do anything just start using it?

---

### Post by philinux on 2013-09-17
> **Jacobin_Noir said:**
> so is it already ntfs. no need to do anything just start using it?
Missed the screenshot as on smartphone. 

Indeed nothing to do already formatted. Enjoy your new drive. :P

---

### Post by flyfishingphil on 2013-09-17
> **philinux said:**
> Missed the screenshot as on smartphone. 

Indeed nothing to do already formatted. Enjoy your new drive. :P

Tried just plugging it in on mine and it shows nothing. Went to "PLACES" and clicked on "SEAGATE BACKUP DRIVE" then clicked on Seagate Dashboard installer.exe and here is what I get when I click on the installer.exe:

[COLOR="#000080"]Archive:  /media/Seagate Backup Plus Drive/Seagate Dashboard Installer.exe
[/media/Seagate Backup Plus Drive/Seagate Dashboard Installer.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/Seagate Backup Plus Drive/Seagate Dashboard Installer.exe or
          /media/Seagate Backup Plus Drive/Seagate Dashboard Installer.exe.zip, and cannot find /media/Seagate Backup Plus Drive/Seagate Dashboard Installer.exe.ZIP, period[/COLOR]

Don't see any options to do a system backup available or any way to get into it. Suggestions?

---

### Post by philinux on 2013-09-17
You would need to do that from windows. Linux does not do .exe files natively. 

You can use drag and drop from ubuntu or there are a few backup apps in ubuntu.

---

### Post by Mark Phelps on 2013-09-17
The Seagate Installer is trying to install an app for Windows.  You do NOT need to do this in order to be able to use the drive.

All you need to do in Ubuntu is click on the folder in Places associated with the drive.  That will open Nautilus to that folder.

---

### Post by holycow131415 on 2013-09-17
Use whats built in. [http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

---

### Post by flyfishingphil on 2013-09-17
Thanks holycow. Backup done. Great, easy to follow instructions. I'll write down that location in case something goes wrong and I need it again.

ffp

---

### Post by flyfishingphil on 2013-09-17
> **Mark Phelps said:**
> The Seagate Installer is trying to install an app for Windows.  You do NOT need to do this in order to be able to use the drive.

All you need to do in Ubuntu is click on the folder in Places associated with the drive.  That will open Nautilus to that folder.

Clicked on the icon and all I get is the view of the folders inside. Which Nautilus do I need to do that?

---

### Post by newb85 on 2013-09-17
The program showing you the contents of the drive *is* Nautilus.

---

### Post by Jacobin_Noir on 2013-09-18
> **philinux said:**
> Missed the screenshot as on smartphone. 

Indeed nothing to do already formatted. Enjoy your new drive. :P

thanks a lot.

---

### Post by Jonathan Precise on 2013-09-18
Please mark as solved by going to thread tools.

---

### Post by CeejRab on 2013-09-18
Hello,

From my experience, I would personally advise against using ntfs between operating systems. Linux was able to read-only ntfs for a long time and now it can write as well I believe but for a reliable format that will work on windows, Linux, and even Mac, FAT32 is still king of the hill. 

I you're not working with individual files larger than 4GB (the fat 32 limit) i would give a +1 for fat32 since it's universally supported and stable. 

Hope this helps, all the best to you. Nice drive by the way, I have a WD passport formatted FAT32 that I like a lot.

---

