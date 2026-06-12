---
title: "GRUB won't load Ubuntu.."
date: 2008-10-04
forum: New to Ubuntu
---

### Post by KS1987 on 2008-10-04
I made a new partition using Windows Vista and GRUB didn't want to load afterwards. I used [this](http://ubuntuforums.org/showthread.php?t=224351) guide, but now Ubuntu doesn't want to boot from GRUB, only Vista does. In the install step I first messed up and chose setup on the same disc my GRUB was situated and not just hd(0), if that matters.. Any input is appreciated! Thank you!

---

### Post by gnuvistawouldbecool on 2008-10-04
First step, ideally, would be to try *every* boot option for Ubuntu, which will be displayed at startup.  if none of those work, then some more interesting approaches are needed.  

Using a different system, such as puppy linux and using that to reinstall grub is a possibility.

---

### Post by melojo on 2008-10-04
[https://help.ubuntu.com/community/Re...tallingWindows](https://help.ubuntu.com/community/Re...tallingWindows)

have a look here

---

### Post by KS1987 on 2008-10-04
Thank you, but none want to load. The system says they won't mount because of error 17.

---

### Post by melojo on 2008-10-04
here is a link for grub error 17, I don't know if it will help.  Its worth giving it a try.

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by caljohnsmith on 2008-10-04
Since you repartitioned, probably Ubuntu's partition changed numbers in Grub. On start up when you get the Grub menu, select a Ubuntu entry, hit "e" to edit it, select the line that says "root (hd0,X)" where X is a number, press "e" to edit it, change it to increment X by one or "root (hd0,X+1)", press return to save the change, then press "b" to boot. If that doesn't work, then decrement X by one or "root (hd0,X-1)" and try again. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note if it works, you'll need to modify your menu.lst to make the change permanent, so when you get into Ubuntu do:
```
gksudo gedit /boot/grub/menu.lst
```
And replace all the (hd0,X) entries for Ubuntu with whatever worked. 

If the above strategy doesn't work, then please post:
```
sudo fdisk -l
```
And also let me know what the (hd0,X) value is for your Ubuntu entries. Let me know how it goes or if you need more info/details.

---

### Post by KS1987 on 2008-10-04
Hi, thank you but the first link didn't work. Then I found the solution [here](http://ubuntuforums.org/showthread.php?t=244788), only to see I was helped here too. Thanks anyway!

---

