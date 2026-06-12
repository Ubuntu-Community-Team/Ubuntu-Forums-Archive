---
title: "Unable to use fwupd to update firmware"
date: 2019-06-04
forum: New to Ubuntu
---

### Post by zerkalo on 2019-06-04
Hi 

I am trying to use the fwupd GNOME application to update the bios of my machine (Thinkpad X1 Carbon 6th gen) but I am getting the attached error message. Previously, there was an error message about AppArmor which I have since disabled. I can't seem to be able to update the bios using the terminal either although my machine is supported by LVFS. I am following the steps in this guide: [https://itsfoss.com/update-firmware-ubuntu/](https://itsfoss.com/update-firmware-ubuntu/)

Any idea what the problem might be? 

Many thanks in advance! 


[ATTACH=CONFIG]283382[/ATTACH]

---

### Post by Xian on 2019-06-04
From a terminal what is the output of these 3 commands:

```
sudo service fwupd start
sudo fwupdmgr refresh
sudo fwupdmgr update
```

---

### Post by zerkalo on 2019-06-05
[B]sudo service fwupd start
[/B]asks for password, but does not return anything. Does that mean the daemon does not start?[B]

sudo fwupdmgr refresh[/B]
Fetching metadata [https://cdn.fwupd.org/downloads/firmware.xml.gz](https://cdn.fwupd.org/downloads/firmware.xml.gz)
Downloading…             [*                                      ] Less than oneDownloading…             [*                                      ] Less than oneDownloading…             [***************************************]
Fetching signature [https://cdn.fwupd.org/downloads/firmware.xml.gz.asc](https://cdn.fwupd.org/downloads/firmware.xml.gz.asc) 

[B]sudo fwupdmgr update
[/B]does not return anything

---

### Post by Xian on 2019-06-05
> **zerkalo said:**
> [B]sudo service fwupd start
[/B]asks for password, but does not return anything. Does that mean the daemon does not start?

It means the daemon has been started --- the operation completed successfully.
> **zerkalo said:**
> **sudo fwupdmgr refresh**
Fetching metadata [https://cdn.fwupd.org/downloads/firmware.xml.gz](https://cdn.fwupd.org/downloads/firmware.xml.gz)
Downloading…             [*                                      ] Less than oneDownloading…             [*                                      ] Less than oneDownloading…             [***************************************]
Fetching signature [https://cdn.fwupd.org/downloads/firmware.xml.gz.asc](https://cdn.fwupd.org/downloads/firmware.xml.gz.asc) 

Good. Exactly how the output should appear. 

> **zerkalo said:**
> [B]sudo fwupdmgr update
[/B]does not return anything

The program found no firmware updates.
If firmware updates exist they are beyond the scope of the program's database.

---

### Post by zerkalo on 2019-06-06
Thanks Xian, that's very helpful. I have assumed that there is a firmware update as I can see it listed on the Lenovo support site (v1.38). It's dated 13.05.2019 so maybe it's not available via fwupd yet? My machine is on v1.34.

There is a .cab file for the newest version, however it only lists Ubuntu 16.04.4LTS as a supported OS - I am running 19.04. Is it worth trying to apply this update using fwupdmgr?

---

