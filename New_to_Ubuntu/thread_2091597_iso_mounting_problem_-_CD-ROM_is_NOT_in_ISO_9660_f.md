---
title: "iso mounting problem - CD-ROM is NOT in ISO 9660 format"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by qarka on 2012-12-05
Hey guys, Linux newbie here :)
I'm running Ubuntu 12.04 and trying to mount an .iso image file, when I mount it it doesnt appear anywhere and if I try to explore/extract it I get the error: CD-ROM is NOT in ISO 9660 format...

 I've had a look around the net and apparently I should be using iat to convert it. So I tried putting the file through iat, but it just gives me a couple of lines like this "Detect Signature RAW 2 at 2656042" and then nothing. No new iso file.

 I'm kinda stuck so if any of you guys have experience using iat could you let me know where I'm going wrong. 
Thanks in advance

---

### Post by squakie on 2012-12-05
How was this ISO created?  Where'd you get it?  What is it?  Several things like that will help us help you ;)

---

### Post by qarka on 2012-12-05
Its a game called Galactic Civilizations 2 :D, I know... for Windows, but supported in Wine apparently. I made it using PowerIso from the CD (My laptop doesn't have CD drive) on a windows pc. Is this helpful?

---

### Post by squakie on 2012-12-05
Does it do this right when it mounts?  Have you had any luck right-clicking on the autorun on the CD and opening it with Wine?  Other than that, I really don't know more at this time.  I'll try to do some searching and see if something shows up.  Hopefully someone will know the answer to this and post back soon!  Sorry I'm unable to help you further at this moment, but I will be searching.

---

### Post by qarka on 2012-12-06
I'll give it a go with Wine, do you mean try and open the iso with Wine?

---

### Post by qarka on 2012-12-06
Sweet, fixed it.
I mounted the iso in the terminal using
```
sudo mkdir -p /mnt/disk

sudo mount -o loop image.iso /mnt/disk
```

then used wine to run the autorun file. 
Thanks a lot for your help

---

### Post by squakie on 2012-12-07
Sorry, I didn't think of mounting the thing first!  I'm just glad you've got it working! ;)

---

