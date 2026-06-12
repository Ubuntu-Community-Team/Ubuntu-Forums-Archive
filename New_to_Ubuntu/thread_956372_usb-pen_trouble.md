---
title: "usb-pen trouble"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by cmay on 2008-10-23
hi.
i have some usb sticks i have trouble with. the first one i tried to get dream linux on. but the pen drive installer somehow corrupted it or at least i cant acces it at all anymore. the dream on a pen does not boot and it is not there i can see with gparted.
 the other one i have all my back up on i created long time ago but now i cant get acces to it either. the file permissons is read and write but while i am still the owner i cant get to put anymore on the stick even that there is no content it claims to be full. i erased all the stuff i had on it to burn it on cd so it should be all clear and now i would like to use it again for back up but it wont let me copy anything to it since ubuntu thinks it is full. 
can anyone help me .
thanks.

---

### Post by kpkeerthi on 2008-10-23
What does **df -h** say? If you have already backed up, why not format it again?

---

### Post by cmay on 2008-10-23
> /dev/sdb              2,0G  2,0G   36M  99% /media/diskoutput of df -h on the one that should be completly emty.
the other one with the dream linux install that failed
> /dev/sdb1             981M   18M  914M   2% /media/diski am not sure what is the best way to format a usb stick to be honest.

---

### Post by kpkeerthi on 2008-10-23
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by cmay on 2008-10-23
i forgot to include this screen shot with the message which is the same for both usb sticks
it says.
permissions could not be determined. 

i wonder why it does that. i only erased the folders one by one after copying them to the home folder to burn them . now all of the sudden i cant get any acces to any of my usb sticks. two of them including the one i have tried to install dream linux on. 
and thanks for the reply by the way.

---

### Post by C.S.Cameron on 2008-10-23
Using the Ubuntu Live CD go to Administration, System, Partition Editor.
Make sure you are seeing the correct drive using the button at the upper right, double check that the drive does not have more GIB than your flash drive. It is probably /dev/sdb if you only have one hard drive.
Right click on the partition and select "Unmount".
Right click on the partition and select "delete", click on the green check mark to proceed.
Right click on the empty space and select "Format to", select FAT32, click on the green check mark to proceed.
Close gparted and you should find that the drive is mounted and writable.
Good luck.

---

### Post by cmay on 2008-10-23
hi there.
thanks it works. i did use gparted before that way using fat16. i just never used fat32. 
the one i thought was corrupt works now other than i still cant set file permissions on it.
but i have permission to copy stuff to it and from it. i am going to try the other one now in a minute when i have walked my dog.  i still just wonder how can the usb stick claim it is empty and full at the same time? 

oh , and another completely  off topic question but is fat32 not a microsoft specific filesystem ?. i used to think so anyway so i did not use fat32 over just fat or fat16 since to my understanding it should be not copyrighted or anything.  just a question about not using a file system that could be not so well supported on linux.

---

### Post by cmay on 2008-10-23
:)

---

