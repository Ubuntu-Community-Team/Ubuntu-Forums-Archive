---
title: "Usb help"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by manngaurav on 2013-06-14
Hey , i created a live usb everyhting was going fine then i chose the option "[B]Guided – use entire disk and set up encrypted LVM"  and then it asked to create some partition , dont want to mess with my windows installation so i created it on the usb itself(i dont know what kind of partition it was , i just don't know anything being a windows user i am just used to press NEXT NEXT and FINISH :P)
 and then it produced some error and boom it was all black now when i format my usb its size is reduced to 230MB from 8GB , i have tried using the HP disk format tool but it says that the drive is write protected please please help i want to get back my usb that's it
frankly even after this i am going to try installing it until am finished :)[/B]

---

### Post by newb85 on 2013-06-14
You tried to set up LVM on the entire USB drive that was also serving as your install media.  That won't work.  If you want to do this, you will have to use something else (either a DVD or another USB drive) as your install media.

Once you've booted from that install media, you will probably be able to reformat the USB drive in question.  (I'm not familiar with LVM, but I'm guessing Windows and the HP disc simply don't recognize it.)

---

### Post by manngaurav on 2013-06-15
OH i see! what a fool i was , i formatted the same drive that contained the OS , thanks

---

