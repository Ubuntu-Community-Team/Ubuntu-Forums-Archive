---
title: "[Kernel] usb_control_msg error -110 (timeout)"
date: 2011-06-20
forum: Programming Talk
---

### Post by jeperipi on 2011-06-20
hi all,

i need to create some application that will access to usb interface inside kernel space.
now the problem is, when i call usb_control_msg(dev, usb_sndctrlpipe(dev,0),0x01,0x02,0x200,0,data,30,1000);
sometime this function return success. but mostly it giving error -110 (error timeout). 

anyone facing this problem before? any idea how to solve it?
i test this in kernel 2.6.29 and 2.6.32-24. but both having the same result.


thank you

---

