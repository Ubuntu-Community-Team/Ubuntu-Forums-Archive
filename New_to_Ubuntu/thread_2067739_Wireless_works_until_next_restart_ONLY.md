---
title: "Wireless works until next restart ONLY"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by geeljire on 2012-10-07
I have an Acer emachines E725 and have installed Ubuntu 12.04 using wubi. Initially there was no wireless but I installed the "Additional Drivers" program and installed the Broadcom STA wireless driver.

When I install/enable the driver, the wireless device works well. But if I shut the computer down or restart it, it will deactivate automatically. Then, after the computer is back on, I need to go deactivate it/remove it from the Additional Drivers window and reactivate/enable it again for it to start working again.

Any ideas?

Thanks.

---

### Post by will1982 on 2012-10-07
This article seems helpful:

[http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/](http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/)

---

### Post by bkratz on 2012-10-07
> **geeljire said:**
> I have an Acer emachines E725 and have installed Ubuntu 12.04 using wubi. Initially there was no wireless but I installed the "Additional Drivers" program and installed the Broadcom STA wireless driver.

When I install/enable the driver, the wireless device works well. But if I shut the computer down or restart it, it will deactivate automatically. Then, after the computer is back on, I need to go deactivate it/remove it from the Additional Drivers window and reactivate/enable it again for it to start working again.

Any ideas?

Thanks.



You should be able to get it to automatically load the wl driver at boot time by:

```
sudo su
echo wl >> /etc/modules
exit


```


reboot

---

