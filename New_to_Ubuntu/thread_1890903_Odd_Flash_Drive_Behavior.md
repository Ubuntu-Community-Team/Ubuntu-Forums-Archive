---
title: "Odd Flash Drive Behavior"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-12-04
This is a screenshot of Disk Utility with my 16 GB PNY Attache flash drive plugged in. It doesn't show up on the launcher, and in Disk Utility, It says Unknown - 0.0 kb space. It won't let me format it either. It gives me an error message:```
Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.14 (22-Dec-2010)
mkfs.ext4: Device size reported to be zero.  Invalid partition specified, or
	partition table wasn't reread after running fdisk, due to
	a modified partition being busy and in use.  You may need to reboot
	to re-read your partition table.
```
HELP!

-DG

---

### Post by BC59 on 2011-12-04
Try to load it in Windows. From there do anything to recreate the drive, by formatting, CHKDSK etc.

In any case is a bad sign.

---

### Post by doppel.ganger on 2011-12-04
Thanks, I'll try that.

---

### Post by doppel.ganger on 2011-12-04
Hmmm... Shows up in W1nd0w$ as F:, but when I try to open it, it asks me to put a drive in F:.

---

### Post by logangorence on 2011-12-04
May just be faulty... Format it

---

### Post by doppel.ganger on 2011-12-04
Like I said, It won't let me format it. See above error message.

---

### Post by jockyburns on 2011-12-04
I had exactly this same problem with a 2gb usb flashdrive. Didn't show up on desktop when inserted. Disk Utility showed it as having 0.0kb and was unable to open it. I tried it in a Win OS computer and although it showed up as a drive in My Computer, didn't detect any medium in it. Even opening a terminal and typing in lsusb detected it.  Turns out it was faulty, (or had developed a fault) Just binned it last week as I couldn't do anything with it. 
Yours sounds exactly the same, I'm afraid.

---

### Post by doppel.ganger on 2011-12-04
Uh oh...

---

### Post by cryptotheslow on 2011-12-04
You could try seeing what one of the various low level format tools out there makes of it.

e.g. [http://www.hddguru.com/](http://www.hddguru.com/)

That one runs on Windows only unfortunately. There's plenty of alternatives around.

Clearly don't proceed to the actual format stage if you want to retain any hope of recovering anything from the drive!

Overall though, it doesn't sound too hopeful :(

---

### Post by doppel.ganger on 2011-12-04
Na, just had an old Fedora boot up. I want to format it to put openSUSE on it. dd says it has 0.0 kb too.

---

### Post by doppel.ganger on 2011-12-04
So, is all hope lost?

---

### Post by CharlesA on 2011-12-04
I'd still try it in a Windows box if you can.

Otherwise I'd say the drive is hosed.

---

### Post by westie457 on 2011-12-04
May be I missed something while reading the thread.

Have you tried to rewrite a partition table to the stick?

---

