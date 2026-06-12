---
title: "Updates Broke NETGEAR Wireless Driver"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Sam324 on 2008-06-19
Hi.  I updated yesterday and they BROKE the wireless driver.  I've NEVER heard of updates that make things WORSE.:mad:  Now It shows no wireless networks upon right click and left click on the network icon.  It shows my network info in "Edit Wireless Networks..." but includes no option to connect.  How do I fix it?

---

### Post by philinux on 2008-06-19
> **Sam324 said:**
> Hi.  I updated yesterday and they BROKE the wireless driver.  I've NEVER heard of updates that make things WORSE.:mad:  Now It shows no wireless networks upon right click and left click on the network icon.  It shows my network info in "Edit Wireless Networks..." but includes no option to connect.  How do I fix it?

Have you seen all the threads on the first page about updates breaking things. It seems to be hardware related and only hitting some people.

First thing I'd try is this.

reboot at grub stage 1.5 press esc

Choose the previous kernel.

---

### Post by Sam324 on 2008-06-19
:(  I booted into the previous kernel (by selecting it after pressing ESC on GRUB load) and it still had the same network menu.  No option for wireless.

---

### Post by philinux on 2008-06-19
You could try kernel ...17

My guess is you either need to

1. Reinsert you driver with modprobe
or
2. Reinstall the wireless driver.

I'm not an expert on these, I'd make a post in here.
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

They'll have you up and running in no time.

---

