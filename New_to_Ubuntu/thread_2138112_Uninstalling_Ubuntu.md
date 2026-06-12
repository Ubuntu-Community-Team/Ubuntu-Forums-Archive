---
title: "Uninstalling Ubuntu"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by DRatJr on 2013-04-23
I have researched and just wanted to make sure this was an appropriate guide to do so:

[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

I am on Windows 8 and I have UEFI. Will this still work for me?

---

### Post by AnaheimSam on 2013-04-23
It will work. I have Win 8 and have uninstalled Linux on many occasions.
I am positive that this method of uninstalling Linux will work.

However, with me, I put in my bootable upgrade disk (as I upgraded from Win 7) go to the command prompt and input...
```
bootrec /fixmbr
```
**_AND_**
```
bootrec /fixboot
```
...just to be sure.

But yeah, reading the link you posted, it's full steam ahead, my dude.

---

### Post by DRatJr on 2013-04-23
Ok so you do the steps in the guide, then go in the cmd window and run that after doing all the steps, just to be sure. Correct? Sorry just a noob and I like to know exactly what I'm doing

---

### Post by AnaheimSam on 2013-04-23
Most definitely. Just like in the link you just posted. If you want, you can even download the Win 7 install disk, follow the instructions to the T, and it will still work.

---

### Post by DRatJr on 2013-04-23
I am going to make a recovery media out of my USB stick, as my ocmputer comes with the recovery partition on HDD. To undo the windows recovery media, I can just format the drive again, right?

---

### Post by AnaheimSam on 2013-04-23
You can format your recovery media to get it off of your USB drive, yes.

---

