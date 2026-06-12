---
title: "Compiling old driver for 12.04 kernel needs rt_linux.h"
date: 2013-09-26
forum: Packaging and Compiling Programs
---

### Post by hvn2 on 2013-09-26
Hi,

I'm trying to compile a driver that is written for kernels up to 2.6.36 for 3.2.0 (Ubuntu 12.04). Using the forums I already solved quite a few problems by replacing various headerfiles and struct-members in the driver code, but I'm stuck at this one: 

implicit declaration of function 'usb_buffer_free'

Searching gives this solution:

Edit include/os/linux_rt.h (rt_linux.h ?) to change the two functions usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent and usb_free_coherent, respectively. DO
NOT replace the instances of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and close the text editor.
Now do: sudo su, make clean && make && make install

Other posts point at a similar solution, but I can't find linux_rt.h or rt_linux.h anywhere on my system. The given path however suggests it is part of the driver packages. Is that correct and should I contact the writer of the driver or do I miss a Ubuntu package that provides it? I searched for it but came out empty.

Thanks.

---

