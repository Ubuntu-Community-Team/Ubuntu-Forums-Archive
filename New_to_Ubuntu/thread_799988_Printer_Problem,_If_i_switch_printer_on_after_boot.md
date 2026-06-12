---
title: "Printer Problem, If i switch printer on after boot, can't print. Reboot then can"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by philinux on 2008-05-19
E [19/May/2008:19:08:30 +0100] Pause-Printer: Unauthorized
E [19/May/2008:19:08:40 +0100] Resume-Printer: Unauthorized


Jobs just get stuck, processing.

Is there a way to kickstart the printer. I dont want to reboot with printer on just to print.

---

### Post by plucky on 2008-05-19
> Is there a way to kickstart the printer. I dont want to reboot with printer on just to print.


Have you tried restarting Cups print server?
```
sudo /etc/init.d/cupsys restart
```


After you power on the printer,assuming it is a USB printer,does it appear when you type **lsusb** in a terminal window?

---

### Post by philinux on 2008-05-20
> **plucky said:**
> Have you tried restarting Cups print server?
```
sudo /etc/init.d/cupsys restart
``` 
Not tried that will give a go though thanks.


After you power on the printer,assuming it is a USB printer,does it appear when you type **lsusb** in a terminal window?

Yes it shows up fine.

Funny thing is when I rebooted before the pc started up the printer spit the page out I wanted.

---

