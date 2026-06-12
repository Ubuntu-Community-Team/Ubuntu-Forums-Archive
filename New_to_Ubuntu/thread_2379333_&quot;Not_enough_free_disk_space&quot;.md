---
title: "&quot;Not enough free disk space&quot;"
date: 2017-12-04
forum: New to Ubuntu
---

### Post by feller102 on 2017-12-04
Hi there, new here, have a problem with updating 'ubuntu base' on my Ubuntu MATE OS. Every day, I get an update notice, and every day I try to update, but each time I get a message like this:

"Not enough free disk space"
"The upgrade needs a total of 115M free space on disk '/boot'. Please free at least an additional 65.3M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I have used 'sudo apt-get clean' and 'autoclean' over and over but it doesn't seem to free up any space on '/boot' or anywhere else and I've got no trash to empty. Can anybody suggest any other way to free up space on '/boot' or offer any other advice?

Thanks for reading.
Dieter

---

### Post by howefield on 2017-12-04
Try the command..

```
sudo apt autoremove
```

most likely you'll need to manually remove some older kernels but try the easy stuff first.

---

### Post by leunam12 on 2017-12-04
Do you have /boot on a separate partition? Post the results of ```
lsblk
``` use code tags please.

---

### Post by feller102 on 2017-12-04
Thanks a million, thats working like a charm!

---

### Post by feller102 on 2017-12-04
-deleted info
```


```

---

