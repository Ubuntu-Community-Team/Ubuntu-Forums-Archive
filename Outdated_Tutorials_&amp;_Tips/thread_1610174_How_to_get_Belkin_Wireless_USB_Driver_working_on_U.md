---
title: "How to get Belkin Wireless USB Driver working on Ubuntu."
date: 2010-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by DirtyPC on 2010-10-31
A common problem for most people with them. This tutorial Applies to the [COLOR="Red"]Belkin N150 F6D4050.[/COLOR] 100& Success rate.

1. Open Application>Accessories>Terminal.

2. Type in **lsusb**

3. Your device ID should read out **050d:935a**

4.If it does read out, in the same terminal, type **sudo gedit /etc/udev/rules.d/network_drivers.rules**

5. A File should open, in this file type **ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935a", RUN+="/sbin/modprobe -qba rt2870sta"**

6. Save and close this file, then in the same Terminal type **sudo gedit /etc/modprobe.d/network_drivers.conf**

7. Another file should open, similar to step 5. Type in **install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935a" > /sys/bus/usb/drivers/rt2870/new_id**

9. Save and Close this file. In the terminal either type **sudo reboot** or just restart your pc as normal.

10. Upon login, a rectangular box will appear saying, wireless networks are available.

Glad I could help
Harry.

---

### Post by khumbulani on 2011-01-11
great stuff!!! its working!!!!!!!!!!!!!! thanks a lot man!

---

### Post by blackaardvark on 2011-04-26
Most excellent!  This worked for me too, Ubuntu 10.10

Thanks a million!

---

### Post by DirtyPC on 2011-06-07
Glad I could help. Didn't realise this even got posted. Thanks

---

### Post by ricohott on 2011-06-14
Almost got it to work, but I am using a belkin F5D7050 ver 4000. lsusb is putting out ID 050d:905c  Ralink RT2573 do you think you can help with that?

---

### Post by DirtyPC on 2011-06-15
5. A File should open, in this file type ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="905c", RUN+="/sbin/modprobe -qba rt2573sta"

6. Save and close this file, then in the same Terminal type sudo gedit /etc/modprobe.d/network_drivers.conf

7. Another file should open, similar to step 5. Type in install rt2573sta /sbin/modprobe --ignore-install rt2573sta $CMDLINE_OPTS; /bin/echo "050d 905c" > /sys/bus/usb/drivers/rt2573/new_id

9. Save and Close this file. In the terminal either type sudo reboot or just restart your pc as normal.

10. Upon login, a rectangular box will appear saying, wireless networks are available.

-that should do it

---

