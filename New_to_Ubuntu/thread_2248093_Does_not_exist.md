---
title: "Does not exist"
date: 2014-10-12
forum: New to Ubuntu
---

### Post by dave6 on 2014-10-12
Hi all
This may be in the wrong place, but bare with me as LibreOffice comes with Ubuntu.

I have had to prepare a presentation, so I used LibreOffice Impress, got it all togather, now I am unable to export the file / presentation ff the computer, it keeps telling me Error saving docutment "name of doc" /media/ USB stick/ "name of doc" does not exist

Yet I can see it in the document folder on the drive, I have tried to copy / paste, export save as to USB stick

Help, I need this in 24hrs on the USB to run on (MS) in the hope of getting a job

Dave

---

### Post by bapoumba on 2014-10-12
Can you save it to the computer hard drive as .odp and then copy the file to the usb stick ?

---

### Post by dave6 on 2014-10-12
It is saved to the hard drive as a .odp file, but I can not paste it to the stick, nor drag it, nor move it ???
Dave

---

### Post by bapoumba on 2014-10-12
Can you "save as" and use another name ?

---

### Post by dave6 on 2014-10-12
Been there, done that, no go ??? I am at a real loss as to what is blocking this file, it's the bit at the end: does not exist

Dave

Update, I have just noticed that there is a little pad-lock sign thing on every folder and file on this stick ??? would THAT have some thing to do with, "does not exist" error reading ?
Dave

---

### Post by cariboo on 2014-10-12
Depending on what version you are using, the usb drive should be automagically be mount when you insert the drive in the usb port. The permissiond should look something like this:

```
-rwxrwxrwx 1 cariboo cariboo  388 Aug  8 19:06 Change_upper_to_lower_case.txt
```

note the -rwxrwxrwx at the beginning of the line, this shows permissions that allow everyone to read and write to the file.

---

### Post by nerdtron on 2014-10-12
> **dave6 said:**
> Update, I have just noticed that there is a little pad-lock sign thing on every folder and file on this stick ??? would THAT have some thing to do with, "does not exist" error reading ?
Dave

Umount it and try unplugging, replug and mount again. Did it make a difference? If not we can resort to command line for changing th permissions.

---

### Post by bapoumba on 2014-10-12
In addtion to what others have asked, what is the filesystem on the drive ?
You can find out using the **mount** command with the USB drive attached.

---

### Post by dave6 on 2014-10-12
bapoumba, taking your last Q first, FAT32 file format, by good luck more than any thing else, this computor is dual booting, other mount / boot being XP, "Ubuntu is unable to print PDF's with out cutting off the header, where XP prints first it corectly first time every time.

So I tried "saving as" to that drive, it worked, I have rebooted to XP formated the USB stick and it now works. must have had some thing to do with the pad-locks

Thanks for the help all, we can call it sorted, have my presntation safly on USB in many formats PDF and I guess I will have to do it with win (sick)

Dave

---

### Post by bapoumba on 2014-10-12
OK, thanks for the update and glad to see you found a solution (please mark your thread as Solved under Thread Tools).
If this is a very important file, I'd suggest an additional backup so that you have it in 3 different places (the computer, the usb drive + one other place). If you do not have another device to save it to, just email it to yourself :)

---

