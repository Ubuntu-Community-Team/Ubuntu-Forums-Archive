---
title: "Installing ubuntu, error in one file."
date: 2014-10-29
forum: New to Ubuntu
---

### Post by Dedalo on 2014-10-29
Hi. I've downloaded the last version of ubuntu lts a few hours ago. I wanted to install it. I donwloaded it in my notebook, I have a dell inspiron, with ubuntu 11.10 installed. Then I copied it in an usb drive, and took the .iso file to another computer with windows, and used the UUI to create the bootable installer. Then I came back to the notebook, and booted it. The installer offered an option to check for errors in the drive, and it found an error in one file. What should I do? now I'm downloading Ubuntu again but from the windows computer this time. The .iso file I downloaded from the notebook was fine, I've checked it with the md5sum command in the terminal after I copied it to the usb drive, and looked for the hashes in ubuntus page. Perhaps the file was corrupted when I copied it to the computer with windows, or perhaps something happened while creating the bootable installation, I'm not sure.

Any suggestions? as it found that error I didn't even try to install it. I think that was the right think to do, right?

---

### Post by yancek on 2014-10-29
If you have a running Ubuntu 11.10 it would seem simpler to just download unetbootin from their site and create the bootable usb.  That would save a few steps, copying to a flash drive, moving the flash to the windows computer, copying the iso to windows and then using UUI.  Might work better if you now download it to windows and use UUI as you are taking away two steps which could cause problems.

You forgot to  post the error and the file name.

---

### Post by oldrocker99 on 2014-10-29
+1 for unetbootin. Just make sure you format the USB drive as FAT first, otherwise it may not boot.

---

### Post by Dedalo on 2014-10-29
I'm not sure on how to do that. The version of ubuntu I have doesn't have support since more than a year ago.

It didn't say anything about the error, I looked for errors, because the installation offered that option, and it found one error in one file, but it didn't say anything about the file I think, perhaps I missed something.

---

### Post by Dedalo on 2014-10-29
I've tried again, now with the .iso downloaded directly from the computer with windows. I have the same problem, one error in one file when I check for errors. Then when I try to "try" ubuntu, running it from the USB drive it just keeps loading and loading. Could it be the usb drive? it's an old kingston of 4gb.

---

### Post by yancek on 2014-10-29
You can download the Linux version of unetbootin from its home page.  Read the instructions before starting which are also on the page.  It might be a bad flash drive also.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Bucky Ball on 2014-10-29
Did you make sure to FORMAT the USB dongle prior to using UUI? It needs to be completely empty. The one file it is not liking may be a left over that was previously on the USB dongle. 

Format the USB to FAT32 and try again (don't just remove all files and folders, format it).

---

