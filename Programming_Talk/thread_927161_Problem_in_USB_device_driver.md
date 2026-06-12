---
title: "Problem in USB device driver"
date: 2008-09-22
forum: Programming Talk
---

### Post by santispor on 2008-09-22
Hi, 
  
   I have written a USB device driver program based on usb-skeleton.c. It compiles and I can do insmod. There is no problem in that. 
After this, I do not see anything in "/proc/bus/usb"
I mounted the usb using teh command "mount -t usbfs none /proc/bus/usb"
Then Ican see the file devices but not drivers. 
The lsmod shows the dd as inserted. 
Do I need to do anything else to make this driver identifyiable. 

Thanks

---

