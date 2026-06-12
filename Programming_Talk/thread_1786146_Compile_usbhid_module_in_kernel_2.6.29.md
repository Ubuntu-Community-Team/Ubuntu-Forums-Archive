---
title: "Compile usbhid module in kernel 2.6.29"
date: 2011-06-19
forum: Programming Talk
---

### Post by jeperipi on 2011-06-19
Hi guys,

anyone have a sample to create usbhid driver module in linux kernel 2.6.29? i need to compile a custom hid driver is because i need special function that usbhid doesn't have. 
i try to compile usbhid source from kernel 2.6.29, but kernel crashed when i run it. after trace, looks like the error comes from 
         ```
__hid_register_driver function. 
```
in this line 
         ```
ret = driver_register(&hdrv->driver); 
```


i use these files
- hid-core.c (usbhid)
- hid-core.c (hid -- need to comment the start and finish module function)
- hid-debug.c
- hiddev.c
- hidraw.c
- hid-input.c
- hid-pidff.c


really appreciate for your help. thank you.

---

