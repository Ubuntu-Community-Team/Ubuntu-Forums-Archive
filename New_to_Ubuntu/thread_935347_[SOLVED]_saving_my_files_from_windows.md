---
title: "[SOLVED] saving my files from windows"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by timstone on 2008-10-01
ok, im "kinda" new to linux, and its just been a while since i used it.  ive got an old pc setup right now just wanted to test everything before i actually got it installed....needed to make sure my wireless adapter would work (and it does!!)

so now i want to go ahead and get my main pc on Ubuntu, but would like to save as many files as possible, like pictures, music, blah blah blah - do I just need to make sure that drive is NTFS?

---

### Post by wolfen69 on 2008-10-01
you can save your files by booting the live cd and transfering the files to a flash drive or whatever. ubuntu should see the windows drive.

---

### Post by timstone on 2008-10-01
so it doesnt matter whether its FAT32 or NTFS?

---

### Post by Crafty Kisses on 2008-10-01
Sure. Paste this code into the terminal:
```
sudo fdisk -l
```
Look for the drive in question. Let's just say, for the sake of this example, that it's /dev/hda1 and NTFS (if it's something else, post it back here, and I or someone else will help you modify the appropriate command). Then paste these commands into the terminal:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222

```
Launch up the file browser and browse the /media/windows directory, and you should see all your files. There is probably a GUI way to do this, too, but it depends greatly on what version of Ubuntu you're using... or if you're using Kubuntu or Xubuntu.

---

### Post by timstone on 2008-10-01
sorry, maybe i was misleading and didnt supply enough info...

i have 2 hard drives on the machine i want to put Ubuntu on, Ubuntu will be on the primary drive and the other will serve as storage and such, and i just want to make sure that ill be able to take what files i'd like to save that i currently have here, and put them on the slave drive and still be able to access them after i install ubuntu, but i see that you are saying it should be NTFS, so ill go ahead and convert it with windows right now if it isn't already

---

### Post by halitech on 2008-10-01
actually Ubuntu can read FAT32 and NTFS (NTFS *can* be a little flaky at times but so far I've had no problems) so you can use either one. When you do your install, just make sure you select the right drive (been there done that, lost everything) or if you feel comfortable, just disconnect the drive while installing and hook it back up when you are done and then we can help you edit fstab to mount it on every boot.

---

### Post by timstone on 2008-10-02
> **halitech said:**
> actually Ubuntu can read FAT32 and NTFS (NTFS *can* be a little flaky at times but so far I've had no problems) so you can use either one. When you do your install, just make sure you select the right drive (been there done that, lost everything) or if you feel comfortable, just disconnect the drive while installing and hook it back up when you are done and then we can help you edit fstab to mount it on every boot.



yea too late, ive already overwritten everything i wanted to save....i couldnt figure out which partition it was, so i just picked one :)

---

### Post by halitech on 2008-10-02
rut roh :( take heart, you aren't the only one that has done this so don't feel too bad about it

---

