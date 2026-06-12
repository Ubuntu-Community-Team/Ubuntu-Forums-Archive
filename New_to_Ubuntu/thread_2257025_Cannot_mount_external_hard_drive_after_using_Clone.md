---
title: "Cannot mount external hard drive after using Clonezilla"
date: 2014-12-16
forum: New to Ubuntu
---

### Post by Anonymous_Human on 2014-12-16
[COLOR=#333333][FONT=Helvetica Neue]Linux Mint 17 Qiana 64-bit. Cinnamon.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]Yesterday I tried to back up my internal (where Linux resides) hard drive's image to my external USB hard drive using Clonezilla. Last month this operation went successfully and the external USB drive is nearly brand new. But this time, the operation failed at the end where Clonezilla checks the saved image for restorability, I got some I/O errors I didn't write down or note. Now, after rebooting I cannot access my external drive. I see it's icon but when I click it to mount I get this:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][IMG]http://i.stack.imgur.com/pAzhE.png[/IMG][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]My external drive is NTFS formatted since I used to use Windows before. Do I need to do an equivalent of scan and repair file system on it? If so what utility would I use?[/FONT][/COLOR]

---

### Post by sudodus on 2014-12-16
Welcome to the Ubuntu Forums :-)

Try according to the instructions in the error output window:

Connect the drive to a Windows computer and run

```
chkdsk /f X:
```

where X: is the drive letter.

Chances are, that the drive will work after that treatment. (Maybe you have to reboot the computer an extra time as is also written in the error window.)

-o-

If you cannot repair the file system, and need not use it with Windows, I suggest that you re-format it with the ***ext4*** file system. Use ***gparted*** for that purpose. In my experience, linux works faster and more reliable with linux file systems.

---

### Post by Mark Phelps on 2014-12-16
If you don't still have Windows available then you will need to download and burn a CD of the ISO file of Minitool Partition Wizard Boot CD.  This is a Windows-based partition management tool.  

When you have that, boot from the CD and choose the option to Check the filesystem on that drive.  That runs CHKDSK on that partition.

---

