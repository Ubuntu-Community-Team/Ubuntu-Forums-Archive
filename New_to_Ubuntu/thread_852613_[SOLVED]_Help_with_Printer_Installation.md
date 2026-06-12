---
title: "[SOLVED] Help with Printer Installation"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by uzzo2 on 2008-07-07
hello all, just purchased a new hp officejet j4540 running ubuntu 8.04. i downloaded the automatic installer to my desktop but am having trouble with the second step. here is the command the instructions say to put in the terminal and i'm getting an error.

phillip@phillip-desktop:~$ sh hplip-2.8.6.run
sh: Can't open hplip-2.8.6.run
phillip@phillip-desktop:~$ 

can someone help me please? thanks in advance

---

### Post by hansdown on 2008-07-07
Hi uzzo2. I don't have Your printer, but I just bought an hp photosmart c4210 all-in-one. Before I hooked it up. I installed python-qt3 and hplip by using the synaptic package manager. Everything worked flawlessly!

---

### Post by kansasnoob on 2008-07-07
"downloaded the automatic installer"

Huh? From where? never heard of such a thing in Ubuntu.

If you're trying to install drivers from a CD forget it!

Most HP printer (and even print/scan combos) are supported from synaptic.

I'll look.

---

### Post by uzzo2 on 2008-07-07
> **kansasnoob said:**
> "downloaded the automatic installer"

Huh? From where? never heard of such a thing in Ubuntu.

If you're trying to install drivers from a CD forget it!

Most HP printer (and even print/scan combos) are supported from synaptic.

I'll look.
from here,
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by uzzo2 on 2008-07-07
> **hansdown said:**
> Hi uzzo2. I don't have Your printer, but I just bought an hp photosmart c4210 all-in-one. Before I hooked it up. I installed python-qt3 and hplip by using the synaptic package manager. Everything worked flawlessly!
ok, did the python qt-3 installation, hplip was already checked but it's not showing up under printers in admin>printing

---

### Post by kansasnoob on 2008-07-07
> **uzzo2 said:**
> from here,
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

That's a very, very bad idea!

Go to System > Administration > Synaptic Package Manager and search for and install

> hplip
hpijs
hpoj
hpoj-xojpanel

Some may already be installed by default, just ignore that or select to reinstall.

I'd give that a 90% chance of working.

---

### Post by kansasnoob on 2008-07-07
Oh since you installed that deb package you should probably run a simple

```
sudo apt-get update
```

to see if you have any problems with repos.

---

### Post by uzzo2 on 2008-07-07
> **kansasnoob said:**
> That's a very, very bad idea!

Go to System > Administration > Synaptic Package Manager and search for and install



Some may already be installed by default, just ignore that or select to reinstall.

I'd give that a 90% chance of working.
ok, i guess i fall into the 10% range, go figure. i had the printer working by just unplugging the usb cord and then plugged it back in. that got the printer going but no scanner. i then applied the changes you gave in your previous post and then did the update and now the printer isn't working again.

---

### Post by uzzo2 on 2008-07-07
Update: got the printer going by unplugging then replugging the usb cable, but the xsane image scanner still isn't working.

---

### Post by uzzo2 on 2008-07-07
> **uzzo2 said:**
> Update: got the printer going by unplugging then replugging the usb cable, but the xsane image scanner still isn't working.
ok, cancel that... just reopened xsane and it scanned, i just love it when things fix themselves, thanks a lot guys.

---

### Post by hansdown on 2008-07-07
Hi uzzo2. When I started up my printer, all that was necessary was to have all connections done and simply turn on the printers power button. Everything started straight up with hp's pop-up windows asking to do a test page.

---

