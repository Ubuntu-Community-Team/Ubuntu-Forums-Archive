---
title: "iso file"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by sundevilcellist on 2008-07-08
Absolute naive question: the file downloaded as an iso file.  Now what?  Please help:(:(
:(
Thanks much!

---

### Post by tamoneya on 2008-07-08
assuming that you are still on windows you should download a program like poweriso and burn the iso file to a CD.  You only need to use the demo version of the program as it is fairly full featured/

[http://www.poweriso.com/](http://www.poweriso.com/)

---

### Post by st33med on 2008-07-08
You need to burn it as an image. Do you have a CD burner software? If not, use [this]("http://software.lsoft.net/Iso-burner.zip").

---

### Post by sharks on 2008-07-08
right click on the file and open it with archive manager or right click on the file and select extract here.

---

### Post by roquefilipe on 2008-07-08
you have to mount it or burn it. 

check gmount-iso

```
sudo aptitude install gmountiso
```

---

### Post by st33med on 2008-07-08
> **sharks said:**
> right click on the file and open it with archive manager or right click on the file and select extract here.

Uh... wrong file buddy ;)

---

### Post by iaculallad on 2008-07-08
> **sundevilcellist said:**
> Absolute naive question: the file downloaded as an iso file.  Now what?  Please help:(:(
:(
Thanks much!

The very first step would be to check if you downloaded a valid ISO file, check for its MD5 hash and compare it to that posted hash equivalent on the source web page.

If it matched the original hash file, try to burn the ISO file as an image and NOT as a file.

For further information, Try reading this [Ubuntu Community Page]("https://help.ubuntu.com/community/BurningIsoHowto") on how to Burn ISO files.

---

### Post by nkri on 2008-07-08
You have to burn it to a CD (that's what .iso is: a file bootable from a CD/DVD).  To do this, insert a blank disc, right-click on the .iso, and click "Write to Disc."  Let it burn.  Now, open the disc drive and shut down.  Put the finished disc in, close the drive, and turn on the computer.  It should boot the CD.  If not, you have to change BIOS options to boot CDs before the hard drive.

Good luck!
-nkri

---

### Post by tjwoosta on 2008-07-08
incase you were wondering..

a .iso is a disk image file (a virtual replica of a cd or dvd)

---

