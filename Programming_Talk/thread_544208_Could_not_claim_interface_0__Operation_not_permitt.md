---
title: "Could not claim interface 0:  Operation not permitted"
date: 2007-09-06
forum: Programming Talk
---

### Post by nonoykevin on 2007-09-06
Hey there!

I would like to know more about my Eclipse running in Linux(ubuntu). I have a program that runs smoothly under the terminal application. But when i try to run in Eclipse application, it can't run the program due to the following errors that gives me the result "could not claim interface 0: operation not permitted" and "could not release intf 0: operation not permitted". I am using the libusb libraries such as the usb.h cause i'm using the usb_claim_interface and usb_release_interface. I also declared the usb_set_configuration in my program.

Can anybody explain why Eclipse cannot rum my program? where it can run successfully in Terminal application.

Thanks!

---

### Post by geraldm on 2007-09-06
Could be a permissions issue for the device.

Possibly the interface was already claimed by another thread.

Gerald

---

