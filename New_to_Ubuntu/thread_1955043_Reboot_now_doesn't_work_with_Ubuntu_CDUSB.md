---
title: "Reboot now doesn't work with Ubuntu CD/USB"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by dbonneau on 2012-04-09
I am currently using Window XP 64bit and trying to install ubuntu by clicking "reboot now" option in Reboot Required under Demo and full installation button in Ubuntu menu of CD/USB ( I tried both from cd and usb). But It doesn't reboot my machine to install ubuntu. Could you anyone help me how to do that ?

Thanks.

---

### Post by flurospar on 2012-04-09
Does the "Ubuntu" option show up when you reboot?

---

### Post by dbonneau on 2012-04-09
No. It doesn't show ubuntu option. When I restart XP which I have now, it just shows me XP desktop icon.. Thanks.

---

### Post by oklokl on 2012-04-09
Data corruption
Features of usb
(data contaminated)

Burning must be re-

Installing SDHC Memory using
 Is read-only lock function.

---

### Post by flurospar on 2012-04-09
Please edit your boot.ini file from "My Computer (right click) > Properties > Advanced tab > Settings button in Startup and Recovery frame > Edit button" like this by adding a line below everything in the Notepad window:

```

C:\wubildr.mbr="Ubuntu"

```

---

### Post by dbonneau on 2012-04-09
> **flurospar said:**
> Please edit your boot.ini file from "My Computer (right click) > Properties > Advanced tab > Settings button in Startup and Recovery frame > Edit button" like this by adding a line below everything in the Notepad window:

```

C:\wubildr.mbr="Ubuntu"

```

This directory path code was already written in the notepad..

---

### Post by dbonneau on 2012-04-09
> **oklokl said:**
> Data corruption
Features of usb
(data contaminated)

Burning must be re-

Installing SDHC Memory using
 Is read-only lock function.

What do you mean "Burning must be re- "? You mean I need to burn Ubuntu cd again ?

---

### Post by oklokl on 2012-04-09
sorry..

usb..-> 
Burning again
Necessity
Data corruption


Ubuntu 
Was installed incorrectly
Will need to reinstall



How to force the boot
ctrl alt F1

ctrl alt delete

---

### Post by flurospar on 2012-04-09
> **dbonneau said:**
> This directory path code was already written in the notepad..

Go to My Computer (right click) > Properties > Advanced tab > Settings button in Startup and Recovery frame. In the window that appears, tick the check box saying "Time to display list of operating systems" and increase it to 20 seconds.

---

### Post by dbonneau on 2012-04-09
> **flurospar said:**
> Go to My Computer (right click) > Properties > Advanced tab > Settings button in Startup and Recovery frame. In the window that appears, tick the check box saying "Time to display list of operating systems" and increase it to 20 seconds.

It was at 30 seconds and I decreased it to 20 seconds. I clicked the reboot option in ubuntu CD but it doesn't happen anything..

Thanks.

---

### Post by dbonneau on 2012-04-10
My conputer does not show anything when I restarted XP with ubuntu cd in the machine..

---

