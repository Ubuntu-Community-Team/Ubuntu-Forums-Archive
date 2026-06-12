---
title: "Boot hanging at initramfs"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by hartwith on 2012-08-16
I have virtually no experience with Ubuntu!

A customer has asked me to recover his data (created in Ubuntu). This on a Toshiba laptop with Win Vista dual boot. Whenever the option to  boot to Ubuntu is taken then it hangs at "initranfs" and goes no further. The machine will boot into Vista safemode but is horrendously slow in normal Vista; this because of a recent power-out and overheating due to cooling fan failure (now rectified).

As a complete Ubuntu ignoramus, what I need advice on is:how can I access the files from Vista? Is it possible to cure the boot-hang at initramfs? Customer does not want to spend too much cash on this work because the laptop is going to be consigned to the scrapheap once he has his files back.

Please keep any explanation simple because I only have 24 hours in which to get my head around this!!!

Many thanks in advance.

---

### Post by NikTh on 2012-08-16
Hi , 
I keep this

> **hartwith said:**
>  Customer does not want to spend too much cash on this work because the laptop is **going to be consigned to the scrapheap** once he has his files back.

so advice or workaround about recover Ubuntu or / and fix initramfs wil be wasted. 

For files recovery , just boot from Ubuntu Live CD/Usb and you can recover as many files you want. 
Just open nautilus with this command from a terminal (ctrl+alt+t) 
```
gksudo nautilus
``` and you can copy everything (Files from Ubuntu or Vista) to an external Usb or HDD. 

If you don't have a Live session Ubuntu , you can make one from within Vista with Unetbootin program. 

1)Grab the .iso from here --> [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) 
2)Grab the unetbootin from here --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
3) Burn the .iso to a usb stick (at least 2GB) with unetbootin. 
4) Boot from Usb (configure BIOS or press 'One boot key' to select device).

If laptop is incapable to boot from usb , you will need a CD . Same steps but shouldn't use unetbootin but a cd burning program instead.

Thanks

---

