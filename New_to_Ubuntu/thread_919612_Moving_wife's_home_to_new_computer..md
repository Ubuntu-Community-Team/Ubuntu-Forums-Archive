---
title: "Moving wife's home to new computer."
date: 2008-09-14
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-09-14
For fun I built myself a hundred dollar computer that fits inside a cigar box.
My wife tried it and liked it much more than her old Celeron.
She wanted her home folder as is, no changes, none.
I tried just copying it over, ran into problems and got fast help using these forumns.
Eventually, what worked was:
Ctrl-Alt-F1
on her old computer,
sudo cp /home/wife /media/disk/wife
to copy it from her computer to usb hdd.
Then built her a home folder on the new computer using 
Users and Groups.
I then rebooted as wife.
This adds some folders and files to her home folder, making booting possible after the transfer.
Rebooted and loged back in as myself.
I copied her folder from the usb hdd in gui using  
Alt F2, 
gksu nautilus
I did not allow the merge from wife to wife to overwrite any files created in the reboot to wife.
Booted ok using wife's username and password but ran in to problems with permisions.
Solved this in terminal with
sudo chown -R wife /home/wife 
Rebooted and logged in as her.
Her old desk top appeared, 
same background, icons, programs, wine, even firefox opened as it was last left.
She is happy, I am relieved.

---

### Post by k33bz on 2008-09-14
thats good, 

Glad you had transfered all your wifes files, and settings over to the CIGAR box :) with out any hassles :popcorn:

---

### Post by Bucky Ball on 2008-09-14
[QUOTE=C.S.Cameron]She is happy, I am relieved.[/QUOTE]

And you are a legend! This is wacky and wild. Needs to be a special feature, forget sticky! Love it. Are you a minimalist or is that your wife, or both? \\:D/

---

### Post by k33bz on 2008-09-14
> **Bucky Ball said:**
> And you are a legend! This is wacky and wild. Needs to be a special feature, forget sticky! Love it. Are you a minimalist or is that your wife, or both? \\:D/


lol, that is something. All the things I can do, pleasing my wife, and keeping her pleased, isnt one of em.   Congrats on that as well...



oh, just out of curiousty, are you goin to take pics and show specs of your cigar box computer?

---

### Post by Bucky Ball on 2008-09-14
Yea! Pics! I gotta see this C.S.Cameron; the cigar box in the hands of wife with appreciative smile! And ... this thread should be in testimonials, not Absolute Beginners ... man, you are a pro. :) Moderators!

---

### Post by C.S.Cameron on 2008-09-14
I have dropped a SketchUP 3D model into Google 3D Warehouse
[http://sketchup.google.com/3dwarehouse/details?mid=1d0bb8169309fa449e8f6a9b76d5748&prevstart=0](http://sketchup.google.com/3dwarehouse/details?mid=1d0bb8169309fa449e8f6a9b76d5748&prevstart=0)
Motherboard is Intel DG945CLF (mITX)
2.5" HDD is Seagate ST9120822AS
Ram is Kingston KVR800D2N5/2G
External Power Brick is PicoPSU-120
Wireless is Belkin F5D7050
Cigar box is Old Owl replica.

---

### Post by Bucky Ball on 2008-09-14
Brilliant. Love it.

---

### Post by k33bz on 2008-09-14
good job, looks good on paper, urrr, or rather looks good drafted, lol....

---

### Post by dhtseany on 2008-09-14
Agreed! Pictures!

---

### Post by OldDirtyTurtle on 2008-09-14
Oh now that is too cool...=D>

---

