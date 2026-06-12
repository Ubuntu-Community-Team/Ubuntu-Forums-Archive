---
title: "Stumped on where to begin &amp; how"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by zen_rasta on 2012-03-25
I have been runing ubuntu on many different machines , even built a few "fresh" builds from old hardware, i would say i am little above novice . I just bought and built my first comp,
Amd fx 4001 , gigybte 970a-ud3 , asus hd 6670

i had mistakenly looked past for the mobo not having any ide connectors turns out i could not boot anything via usb . I have tried unetbootin , ubuntu live disk creator , different usb's and non of them will take  . So i tried putting in an old sata drive seeing if maybe i can wake grub up  , it kind of worked now the board boots to and old 8.04 install the wont update or boot graphically 

1) is they anyway to boot via usb on this board ? (cannot do cd)

2) can you do a complete reset of 8.04? like back to base code

---

### Post by zen_rasta on 2012-03-25
tried this

[http://ubuntuforums.org/showthread.php?t=1859017](http://ubuntuforums.org/showthread.php?t=1859017)

led no where

---

### Post by Daveth on 2012-03-25
one usually sets the boot device options at low level in the BIOS; it usually has "set first boot device" option and should have usb in the list, and certainly will have cd.

---

### Post by grahammechanical on 2012-03-25
You might find that the BIOS is set up for a floppy drive. If it is - disable it and then you may get options somewhere for USB and setting USB as the first boot option instead of floppy.

This was the situation on my motherboard. so, I pass the information on to you.

Regards.

---

### Post by zen_rasta on 2012-03-25
i have tried above options down to invidual selecting the usb boot , it either just wont recognize the thumb drive , or say boot error , the only time i get it to boot is when i run he hard drive with 8.04 on it , i cant seem to upgrade the 8.04 due to too many errors  , i would to reset to basic install and work from there

---

### Post by wildmanne39 on 2012-03-25
Hi, it sounds like your usb disk may need to be made again from a fresh download of ubuntu, the reason you can not upgrade 8.04 is it is to old and the updates are not available any more.

I would also post the results of these command so we can look at your system specs.
```
sudo lshw
```
Thanks

---

### Post by zen_rasta on 2012-03-25
i cant show the lshw file i am writing this from another computer ,  i have downloaded all (lts & current) the ubuntu files and tried them to no avail , what else you need to know maybe i can be of help ?

---

### Post by theducksfan2010 on 2012-03-26
> **wildmanne39 said:**
> Hi, it sounds like your usb disk may need to be made again from a fresh download of ubuntu, the reason you can not upgrade 8.04 is it is to old and the updates are not available any more.

I would also post the results of these command so we can look at your system specs.
```
sudo lshw
```
Thanks

I had this same exact problem trying to boot Puppy Linux off of a USB drive. Eventually I gave up on it and tried a different smaller thumb drive (4GB vs 32GB) and it ran on first try. It took me 2 days of loading and reloading the USB before I tried another, and that was my problem. I would try a different thumb drive if you have one, as I am now booting up a old Acer laptop without a hard drive in it, that does not even have USB boot in the BIOS options.

I have since got the 32GB thumb drive running, but switching out was the start of my progress.

---

### Post by motoroller on 2012-03-26
In the BIOS settings menu, go to advanced BIOS features, then where it says hard disk boot priority, go into that, and with the Live Install USB inserted, it might recognize it as a bootable volume, whereby you can select it as first priority, then your hard drive as second priority. Hopefully this will force it to boot from your flash drive... I don't know if you've already tried this, but it's worth a shot...

after re-reading the posts I'm thinking you probably already tried this...:redface:

---

### Post by mastablasta on 2012-03-26
no CD, no USB, no floppy.... is there any other way too boot? well you do need a devide you can boot from which seems to be HDD in your case. 
 
Also am not sure why you can't have USB as (1) IDE has nothing to do with it and (2) there are cheap PCI usb cards out there.

---

