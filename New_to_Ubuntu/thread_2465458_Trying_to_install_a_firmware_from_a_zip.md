---
title: "Trying to install a firmware from a zip"
date: 2021-08-02
forum: New to Ubuntu
---

### Post by timebones on 2021-08-02
I am trying to install the linux CH341SER drivers but I do know how to install them from the zip folder

[http://www.wch-ic.com/downloads/CH341SER_ZIP.html](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)

Any help would be greatly appreciated

---

### Post by yancek on 2021-08-02
Have you tried simply right clicking the zip icon and selecting the Extract option?  There should be a README file that explains installing.  Or in a terminal, just navigate to the directory where the zip file recided and use unzip.

---

### Post by Holger_Gehrke on 2021-08-03
That archive contains source code for the driver kernel module. I could be wrong, but AFAIK the module should already be installed by default as "/lib/modules/$(uname -r)/kernel/drivers/usb/serial/ch341.ko" and you should be able to load it with a simple 'sudo modprobe ch341'.

Holger

---

