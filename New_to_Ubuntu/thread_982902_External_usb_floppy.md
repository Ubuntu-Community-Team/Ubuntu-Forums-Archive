---
title: "External usb floppy"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by osheasan on 2008-11-15
Hello everyone

I'm running Ubuntu 8.10

OK - I connect my usb external floppy it starts up, then stops - Places/Computer shows a "Floppy Drive" icon but when I double click it error message comes up saying "Unable to Mount Location - can't mount file"

I've searched around forums and found suggestion of running dmesg to see what comes up - I did that and it recognizes it as /dev/sdb - tried adding a line in /etc/fstab but still nothing - 

dmesg does say "Sense Key: Medium Error [current] " and "Add. Sense: Cannot read medium - unknown format" which sounds serious

Some threads mention scsi support needs to be added to kernel - but have no idea how to do that

Can anyone help??!! 

Thanks

---

### Post by swoody on 2009-01-19
Hello, and welcome to the forums! :D

Just to clarify, is this a USB thumbdrive, or a floppy connected through a USB cable? What filesystem is currently on your disk? It sounds like it has a format that Ubuntu can't read. You may want to try reformatting the disk with a 'fat' file system (that Windows and Ubuntu can BOTH read). If you can mount it in Windows, right-click on the drive, and select 'Format', and then make sure in the options that you select it to be formatted as a 'fat' filesystem (this will ERASE all info on the disk! So back it up first!) Then try mounting it in Ubuntu again, and see if you still get the error message. 

Please let me know if this works, or if you encounter any errors! :)

---

