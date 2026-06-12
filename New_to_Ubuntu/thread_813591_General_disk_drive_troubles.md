---
title: "General disk drive troubles"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ucal on 2008-05-30
In trying to mount an iso, I ran into some problems.  I'm using gmount iso to avoid using the terminal for this (it is just a graphical shell to the terminal commands right?).  Unable to mount the image, I turned to burning the image onto a disk, but I can't open my disk drive.  The physical object that is.  No matter what, it won't open in Ubuntu.  It works fine in Vista though.  

The most pressing problem is opening my disk drive.   Any advice?  After that, it would be nice to figure out how to mount these isos.  I did notice something strange about them.  They are in the .ISO format, as opposed to .iso, and gmount iso doesn't recognize them as .iso.

---

### Post by quelx on 2008-05-31
A reboot doesn't let you open the drive?  Is there a disk in there now?

rename the .**ISO** > .**iso** and see if gmount will let you mount it.

otherwise you may want to try the terminal

[http://ubuntuforums.org/showpost.php?p=5081684&postcount=3](http://ubuntuforums.org/showpost.php?p=5081684&postcount=3)

---

### Post by ucal on 2008-05-31
Reboot didn't work.  Interestingly enough when I try and eject the disk by right clicking on the drive in the computer folder, I receive the error message that the volume can't be mounted.  No idea if this is relevant.  

Also, renaming the file helped Gmount-iso to recognize the file, but the mounting was unsuccessful.  I suspect this is due to my own incompetence though.

---

### Post by ucal on 2008-05-31
Oh, and there isn't a disk in the drive to my knowledge.

---

### Post by ucal on 2008-05-31
Bump:  Some more information that I remembered.  The last disk I put in this thing had a Word Document or three on it, and that's it.  I wasn't able to open the drive in Ubuntu, so I rebooted, opened it in vista, and took the disk out.  I haven't been able to open the disk drive since. EDIT:  Haven't in Ubuntu.  I haven't had cause to try in vista yet.  I'll try it out now.

EDIT (again):  I can open the drive just fine in Vista.  Actually it took a couple retrys, because for some reason the empty drive was in use, but it did open.

---

### Post by ucal on 2008-06-03
Bump.  I can get the disk drive open in ubuntu now.  Not through the eject command, but simply applying liberal amounts of pressure on the disk drive button, and letting it open itself.  I don't like doing this though.  It doesn't accomplish anything, because Ubuntu still doesn't recognize that there is a disk in the drive.  Its like Ubuntu isn't even physically connected to my actual dvd/cd disk drive, but rather to an imaginary one.

---

### Post by ucal on 2008-06-07
Bump?  Any help?

---

### Post by cariboo on 2008-06-07
Mounting an iso file is way easier to do in a terminal than it is trying to use a gui. Just open a terminal type:

```
sudo mount -o loop whatever.iso /mnt
```

and hit enter. replace whatever with the name of the iso file, also if there are spaces in the file name encapsulate the file name in quotes eg:

```
"whatever the heck the name is.iso"
```

Jim

---

### Post by ucal on 2008-06-08
Okay, I'll try that. (covert bump)  I think the problem was that what I was trying to mount wasn't a valid iso.  I'll mount on a regular iso when I can manage to download one.

EDIT. Now the drive is giving me trouble in vista, and won't open.  I guess this isn't an Ubuntu problem then.  Sorry for wasting your time.

---

