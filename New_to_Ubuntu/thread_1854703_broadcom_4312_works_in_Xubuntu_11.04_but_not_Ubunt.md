---
title: "broadcom 4312 works in Xubuntu 11.04 but not Ubuntu 11.04"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by beew on 2011-10-04
I am trying to install Ubuntu 11.04 on an old hp laptop which has a  broadcom4312 driver. I installed the driver with Addditional Drivers and  everything seems to work until I restarted to complete update then it  becomes "activated but not installed" . 

The strange thing is installing the driver in xubuntu works flawlessly. I  checked the packages installed in Xubuntu 11.04 and they are  bcmwl-kernel-source 5.100.82.38-0ubuntu3.2 broadcom-sta-common 5.60.36-3  broadcom-sta-source 5.60.36-3 and bc43-fwcutter1:013-3   Iinstalled these same packages in Ubuntu 11.04but  the problem still persist (driver activated and in use before restart   but after restarting driver no longer in use). I would like to know why.  Thanks.P.s Also installing the bcmwl-kernel-source in Synaptic doesn't  install the driver at all for some reason. Instead of activated but not  in use, the driver is not activated at all, attempt to install the  driver through jockey gives the the error that wl driver does not exist  and cannot rebind wl driver.

---

### Post by garvinrick4 on 2011-10-04
In next post a graphic, make sure in synaptic you put bcm in search and remove all but the 2 in graphic.

---

### Post by garvinrick4 on 2011-10-04
remove all but these two with 'bcm" in search window of synaptic. Just the 2 installed reboot without wired connection.

---

### Post by beew on 2011-10-05
Hi, thanks for the answer.

It seems that the problem is that I have upgraded the kernel to version 3.xx and somehow it broke the bcmwl kernel source package,--the xubuntu install has not been upgraded. Removing the kernel and downgrading some packages solved the problem. You are right about only installing the two packages (and let jockey finds the bcmwl-kernel-source). I had previously installed the broadcom-sta packages as well and I think that resulted in the bcm43xx drivers being blacklisted.

---

### Post by garvinrick4 on 2011-10-05
Glad you are up and kicking again beew.

---

