---
title: "Multiple kernels in boot screen question."
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Linux_noob616 on 2008-06-17
I've been using Ubuntu for about a month or two now. And just 2 days ago i went from having 5 items in the boot screen (Ubuntu, Recovery, something i don't remember, memory test, Vista) to having all that plus an extra ubuntu and extra recovery.

So my questions. Whats going on with those? And how do i remove them?

---

### Post by blazercist on 2008-06-17
don't worry there was a kernel upgrade and thats just old entries in the grub menu, just pick the top one and ignore all the rest.

---

### Post by Sarah L on 2008-06-17
> **Linux_noob616 said:**
> 
So my questions. Whats going on with those? And how do i remove them?

Ubuntu automatically updated your kernel, but kept the old ones available in the boot menu in case you wanted to go back and use an older version (if, for example, you broke a module).

If you want to remove extra choices in the boot menu, press ALT-F2 and type in:

```
gksu gedit /boot/grub/menu.lst
```

and delete the entries you don't want from that file.

---

### Post by yragrelluf on 2008-06-17
Just a Kernel Upgrade. You don,t need to delete any of them. Do you know whether or not you are using the new kernel, because it probably will fix some bugs that you didn't even know about. Could you let me know what kernels are in the grub menu in the order they are in? Also to check what kernel you are logged into, just type in the terminal "uname -r". I am using 2.6.24-19-generic, but I kept 2.6.24-18 for a backup.

---

### Post by yragrelluf on 2008-06-17
There is an easier way to do what sarah suggests, using synaptic package manager, and it is much less likely to mess anything up. editing the menu.lst is better for changing the order of menu items, and setting the default kernel.:guitar:

---

### Post by al-fred on 2008-06-17
[best free porn](http://absolutely.bedava250mb.com) 
[8mg avandia](http://abusing.bedava250mb.com) 
[accutane when will skin get dry](http://accutane.bedava250mb.com) 
[adalat non extended release](http://adalat.bedava250mb.com) 
[arizona lasix](http://arimidex.bedava250mb.com) 
[atrovent nebulizers](http://atrovent.bedava250mb.com) 
[aleve and blood pressure](http://alcoholics.bedava250mb.com) 
[allegra hotel in chicago](http://allegra.bedava250mb.com) 
[amitriptyline and cymbalta](http://amitriptyline.bedava250mb.com)

---

### Post by forestpixie on 2008-06-17
> **blazercist said:**
> don't worry there was a kernel upgrade and thats just old entries in the grub menu, just pick the top one and ignore all the rest.

Yea - agrre just leave it alone till you are sure you have no problems with the newer kernel.

---

