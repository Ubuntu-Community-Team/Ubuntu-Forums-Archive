---
title: "Removing Win7"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by robert1305-gmail on 2014-04-21
Hi There,

I am at this moment in time using a dual boot, with Ubuntu 14.04 and win 7, but win 7 has gone belly up big time,:mad:  how do I remove win 7 and use just Ubuntu.):P

Regards Bob

---

### Post by kc1di on 2014-04-21
The easiest way is to run gparted (install it with this command in a terminal) ```
sudo apt-get install gparted
```  

Delete  the windows partition and make a new one formated to ext4 that will wipe windows 7 from your machine. 
rename the New Partition /data or something to you liking and your will have regained that space for storage. 
good luck

(NOTE: be very careful that your delete the correct partitions , not your ubuntu ones.  after that is complete - go to a terminal and run the following command
```
sudo update-grub
``` That should remove windows 7 entry from your grub boot menu.

---

### Post by david98 on 2014-04-21
As kc1di said use gparted. If it was me I would use a live dvd or usb disk to use gparted to delete the windows partition and then resize the ubuntu partition to use the unallocated space made available by deleting windows. You may need to run boot repair afterwards but better to have the full drive for ubuntu then have a partition you are not going to use in my opinion.

---

### Post by robert1305-gmail on 2014-04-21
Thanks for the info guys, I was just about to ask if I could get rid of the Win7 partition and use the whole of my HD for Ubuntu 14.04, but David98 beat me to it.

I am going to send for the starter pack, as I like to look at other ditros on my laptop.

Thanks again, Regards Bob

---

### Post by david98 on 2014-04-21
If you are happy that this is solved then please use the thread tool's at the top right hand corner of the thread and mark it as solved. I hope you have fun trying other Linux distro's ):P

---

