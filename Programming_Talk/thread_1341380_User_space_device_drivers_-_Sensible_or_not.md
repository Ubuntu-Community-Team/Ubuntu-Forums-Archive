---
title: "User space device drivers - Sensible or not?"
date: 2009-11-29
forum: Programming Talk
---

### Post by PeggySue on 2009-11-29
I am looking into the possibility of using a USB to parallel printer converter as a parallel port.  (Current drivers use URBs for data transfer, I want to address the endpoints directly.)  This is my first look at drivers and would appreciate some guidance as to the best approach.

I would like to end up with a user space driver but I think I need to use usb.h and other kernel space libraries to get to the USB endpoints.  

Is there a standard approach for the use of usb.h etc. in user space or is the idea of driver experiments in user space a daft idea?

Any thoughts would be welcome.


.

---

