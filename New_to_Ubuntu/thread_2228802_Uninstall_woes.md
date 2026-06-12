---
title: "Uninstall woes"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by Ryles on 2014-06-09
Hi guys,
so I'm using XMCbuntu and I've downloaded an add-on called LCDproc for customising an LCD display on my HTPC.
 
Anyway I had it working but I've now screwed it up (doh), so I decided to uninstall the app and try again but I can't the damn thing working again.
 
I noticed the config file /etc/LCDd.conf is retaining the old driver settings so even if I uninstall via XMBC it's obviously not completely deleting my config file which I need to reset.
 
IS there a way or completely deleting this program please?
 
Many thanks as always

---

### Post by Vladlenin5000 on 2014-06-09
You already found the configuration file... Delete it.

---

### Post by Ryles on 2014-06-10
Hi i tried but it gives me a permission denied error? :(

---

### Post by anakai on 2014-06-10
have you used the command ```
sudo rm /etc/LCDd.conf 
```?

---

