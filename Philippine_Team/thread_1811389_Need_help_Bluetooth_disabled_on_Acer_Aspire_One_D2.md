---
title: "Need help: Bluetooth disabled on Acer Aspire One D255E"
date: 2011-07-24
forum: Philippine Team
---

### Post by killer_d76 on 2011-07-24
I have installed Ubuntu 10.10 dualboots 11.04 on my wifes Acer Aspire One D255E it has a built-in bluetooth device that can be activated by pressing fn + f3, on 11.04 bluetooth works out-of-the-box but on 10.10 it just shows the icon on the panel when fn + f3 is pressed, it can be turned on and off but it says that the bluetooth is **disabled**, the wifey prefers 10.10 because she find it a bit faster and snappier than 11.04, is there a way that the can enabled in 10.10? thanks in advance! ;)

---

### Post by daison3 on 2011-07-24
You can also re-post this on this link, so that the bluetooth experts can analyze your problem.


[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by killer_d76 on 2011-07-24
thank you so much for the quick reply.. tried some commands and but this one works!

```
sudo service bluetooth restart
```

and the bluetooth starts working like a charm!.. now my problem is removing the 11.04 partition (deleting the whole partition to create an extra hdd space is ok) and editting boot grub to boot intantly in 10.10 :(

---

