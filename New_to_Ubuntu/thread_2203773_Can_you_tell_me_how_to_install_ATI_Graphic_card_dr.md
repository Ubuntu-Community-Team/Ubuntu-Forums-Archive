---
title: "Can you tell me how to install ATI Graphic card drivers offline"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by someshangale on 2014-02-05
Hi Friends!!

I am using Ubuntu 12.04 LTS along with Windows XP.But since i have updated the graphic drivers in ubuntu and has restarted the desktop i am unable to boot ubuntu as it is showing a message " running on low graphic mode".I tried to correct the problem through the recovery mode but not getting access to it too.I tried some terminal commands but for that the internet need to be connected which i can connect only after booting of system in GUI mode of Ubuntu since i am using 3G dongle.So please help me to resolve the issue.
I am using 1 GB DDR3 ati radeon graphic card
ATI Radeon HD 5400 Series
Using intel i3-2100 CPU 3.10GHz
with intel DHWW61 motherboard

As mentioned above i am facing problem of "Low graphic mode error".
I tried to rectify it but can't since i am having 3G dongle and not wired internet connection hence can't access internet since i am unable to boot into ubuntu and activate the dongle.
[COLOR=#ff0000]**Now i want to know, is it possible to install the ATI graphic card drivers offline by downloading them in pendrive & install them through terminal commands in root mode  from the pendrive ,since i am not having access to GUI of ubuntu**[/COLOR].
Awating your reply
Regards
Somesh Angle

---

### Post by deadflowr on 2014-02-05
Do you know what driver you installed/updated?
Or how you installed them?

Edit: This command can help figure out the driver(or driver version)
```
lspci -nnk | grep -iA3 vga
```

---

### Post by mastablasta on 2014-02-05
here under 3.1.: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

but again you need to somehow download packages and install if they are misisng in your ubuntu.

---

### Post by Mark Phelps on 2014-02-05
IF your Ubuntu version is newer than 12.04.1, you will not be able to install AMD drivers because AMD dropped driver support for their HD 2x/3x/4x-series cards last summer.

Starting with Ubuntu 12.04.2, the X-server got upgraded to a newer version -- one that is incompatible with the AMD drivers.

If you're at 12.04.2 or higher, you already have the most current Radeon drivers already installed.

---

