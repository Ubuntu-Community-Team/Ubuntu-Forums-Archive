---
title: "Entering wireless password on multiple computers"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by japhyr on 2011-10-31
Hello,

I need to configure a number of machines to access my school's wireless network.  I have a script that modifies a number of other configurations such as samba automatically, through configuration files.

Is there a way to enter the wireless network password through a terminal command?

---

### Post by azmyth on 2011-10-31
Do you mean the WPA2, WEP password? If so, use iwconfig to set this and the network, etc.

---

### Post by aeiah on 2011-10-31
you can specify it in your /etc/network/interfaces file i believe

---

### Post by The Cog on 2011-10-31
If you edit the network connections on one PC (using the network manager widget in the system tray) and check the box to make it available to all users, then a config file is created in /etc/NetworkManager/system-connections/. A separate file is created for each connection. You can copy this file(s) to the same location in other PCs and they will immediately connect. No restart needed.

---

### Post by japhyr on 2011-11-02
Thank you all.  I ended up configuring the first batch manually, but I will try to use this information on the next batch.

---

