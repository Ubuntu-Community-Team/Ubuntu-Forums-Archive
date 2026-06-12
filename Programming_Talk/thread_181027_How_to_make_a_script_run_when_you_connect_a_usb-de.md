---
title: "How to make a script run when you connect a usb-device?"
date: 2006-05-23
forum: Programming Talk
---

### Post by DrSkalpell on 2006-05-23
Hi!

Does anybody have an idea about how to make this work?

I have a usb-disk and a backup-script (rsync) that copies data to the disk. I would like the script to run automatically whenever I connect the disk to my laptop.

Earlier today I learned how to create pop-up messages with zenity (thanks kvark and tkjacobsen) so the perfect solution would be something like this:

1. I connect the usb disk and turn it on
2. The script starts automatically and generates a pop-up message asking me if I want to do backup to the disk
3. Yes: backup, No: skip backup this time
4. Thats it!

Any good ideas?

---

### Post by egon spengler on 2006-05-23
[ivman](http://ivman.sourceforge.net)

---

### Post by DrSkalpell on 2006-05-24
Thankyou!

Worked excellent

---

