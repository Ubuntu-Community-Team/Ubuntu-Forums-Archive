---
title: "External HardDisk and Mouse problem"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Inzo on 2008-05-14
Hei guys, I'm new with linux and ubuntu and really need help. Ubuntu detect my Western Digital MyBook Essential once but after i leave it for 30 minutes the icon on desktop gone. I have try to unplug and plug it but nothing happen. Another problem is my mouse, it works but if I unplug it and plug it back, my mouse wont work.

Can anyone help me please?

---

### Post by steve-shinn on 2008-05-14
I suspect the icon for the WD drive disappears because the HD has powered down after an elapsed period of time.

Why do you want to unplug the mouse and then plug it back in again....you will need to reboot the PC with the mouse attached to get it working again.

---

### Post by Inzo on 2008-05-14
I have try to restart my laptop to see if my external HDD will work after it but it didnt. i unplug my mouse because i dont have enough usb slot for my big flashdisk. And ubuntu cant detect my flashdisk, do you think its my usb slot problem?

Thanks for responding..

---

### Post by steve-shinn on 2008-05-14
Post the output of the command "ls usb" (without quotations)here, with the flash disk inserted.

I don't think it's a usb slot problem if the mouse works when using the slot. The mouse will fail to work if you take it out whilst Ubuntu is running, hence the need to re-boot if you take the mouse out.

If you don't have enough USB slots, why don't you invest in something like this :-
[http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=559220](http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=559220)

---

### Post by Inzo on 2008-05-14
how to do the ls usb ? sorry i never use linux before.

---

### Post by Inzo on 2008-05-14
This is what appear after i enter lsusb:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

after i enter lsusb my flashdisk shown but not the HDD.
can anyone explain and give me solution please?

---

