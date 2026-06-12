---
title: "Install packages offline?"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by chanoaji on 2013-01-25
Hey there, is it possible to install packages offline, such as, ndiswrapper?

I have a dual boot system going between Windows Vista/Ubuntu. I have internet access on Vista(via wifi hotspot) but not yet on Ubuntu. I was thinking I could download packages on Vista and put them on an sd card and take them over to Ubuntu and install them. Are there any terminal commands that might make this possible?

Thanks.

---

### Post by MadmanRB on 2013-01-25
Yes, download the appropriate packages you need onto your drive and then install them in ubuntu.
Or just use linux mint, that has ndiswrapper pre installed.

---

### Post by Paqman on 2013-01-25
You might find it easier to just plug straight into your router with an ethernet cable and install that way.

---

### Post by MadmanRB on 2013-01-25
> **Paqman said:**
> You might find it easier to just plug straight into your router with an ethernet cable and install that way.

This is a very good method too.
But like I said maybe linux mint is in your future.

---

### Post by chanoaji on 2013-01-25
I can't connect through Ethernet. I connect using a WiFi USB adapter that connects to the internet through an android smartphone that has potable WiFi hotspot, all wireless. Is there a terminal command that can install them by having them on my desktop?

---

### Post by Paqman on 2013-01-25
> **chanoaji said:**
> Is there a terminal command that can install them by having them on my desktop?

Yes, but it's easier to just double-click on the .deb and it will open in Software Centre.

If it complains that dependencies are not met, you will need to make sure you also have the .deb file for any packages that it depends on. It looks like you'll need [ndisgtk]("http://packages.ubuntu.com/quantal/ndisgtk"), [ndiswrapper-common]("http://packages.ubuntu.com/quantal/ndiswrapper-common") and [ndsiwrapper-utils-1.9]("http://packages.ubuntu.com/quantal/ndiswrapper-utils-1.9"). Install them in this order: common > utils > ndisgtk.

---

### Post by chanoaji on 2013-01-25
When opened through software center the install button is greyed out.

---

### Post by iMac71 on 2013-01-25
supposing that you have more than a package to install and that those packages are all on your desktop, you might use the following bash script:
[PHP]#!/bin/bash

pkgs=$(ls ~/Desktop/*.deb)
for pkg in $pkgs
do
    dpkg -i $pkg
done
exit 0
[/PHP]

---

### Post by Warren Hill on 2013-01-25
All Ubuntu packages can be found here
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can manually install from the deb files.  However, you will need to check the dependencies carefully making sure you install in the correct order.  If a package needs another package then install the needed package first.  Note the needed package may need other packages too.

If you can get internet access apt makes this much easier as it does all the checking for you.

---

### Post by Paqman on 2013-01-25
> **chanoaji said:**
> When opened through software center the install button is greyed out.

Ok, let's see why. Try it in terminal and see what error it spits out:

```
sudo dpkg -i packagename.deb
```

---

### Post by squakie on 2013-01-25
Also, with the USB wireless adapter plugged in:

lsusb

Copy and paste the results back here.  This will let us know the manufacturer id and product id (which points to the chipset used) of the wireless adapter so we can see if we can get a driver for you so you can just install the driver and do things on your own.

That is if I understood you correctly in that you need help getting the USB adapter to work?

---

### Post by GordThompson on 2013-01-25
> **chanoaji said:**
> When opened through software center the install button is greyed out.
The "Install" button is greyed out because of a bug in the Ubuntu Software Centre that prevents installs if the machine does not have an active Network Manager connection. See [here]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/911706") for details.

---

### Post by squakie on 2013-01-25
If the software center won't install a deb file with no network connection, you can always install it just using apt.  Just download the package(s) as I mention, copy to your ubuntu box and use apt.

---

