---
title: "Pairing computer with phone"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-05-03
Are there any programs for linux where I can use bluetooth to pair up my computer with my phone and send files over bluetooth?

---

### Post by wesley_of_course on 2008-05-03
Synaptic provides both KDE  and GNOME Bluetooth tools respectively .  Have not tried but am sure its been tested a time or two .   Heres a link if you'd like to explore it further ; [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)    Let others know how it went , it might help them  to learn about it  .

---

### Post by glennric on 2008-05-03
Install bluez-gnome.  You might also need bluez-utils.  

Then go to System->Preferences->Bluetooth and make sure the input service is running, and that "Never display icon" under Notification Area in the General tab is not selected.  

If your computer has bluetooth then the icon will show up in the system tray.  Right click and select "Browse device" after setting your phone to discoverable.

Edit: This is for gnome.

---

### Post by RadiationHazard on 2008-05-03
i have a wireless card built into my laptop
do i need something special?

---

### Post by glennric on 2008-05-03
wifi is not bluetooth.  wifi is a wireless network device.

---

### Post by RadiationHazard on 2008-05-03
> **glennric said:**
> wifi is not bluetooth.  wifi is a wireless network device.

i didn't know if since it brought in signals if it could bring in bluetooth also.

well i guess i can't do it then
thanks for the help anyways

---

### Post by glennric on 2008-05-03
Unfortunately bluetooth devices can't communicate with wireless network devices.  You can get a usb bluetooth adapter for $10-$20 though.

---

### Post by RadiationHazard on 2008-05-03
> **glennric said:**
> Unfortunately bluetooth devices can't communicate with wireless network devices.  You can get a usb bluetooth adapter for $10-$20 though.

alright thank you for all your help

---

