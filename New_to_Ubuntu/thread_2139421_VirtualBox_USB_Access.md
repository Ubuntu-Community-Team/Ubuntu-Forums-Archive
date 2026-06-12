---
title: "VirtualBox USB Access"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Habanero101 on 2013-04-26
Hello, 

I'm having troubles accessing USB on VirtualBox.

I keep getting this message:

"Failed to access the USB subsystem.

VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. Please see the user manual for a detailed explanation."

I googled it and found [this old thread]("http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml"), but it's no longer applicable since Users and Groups have been changed to just users.

please help.

---

### Post by haqking on 2013-04-26
> **Habanero101 said:**
> Hello, 

I'm having troubles accessing USB on VirtualBox.

I keep getting this message:

"Failed to access the USB subsystem.

VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. Please see the user manual for a detailed explanation."

I googled it and found [this old thread]("http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml"), but it's no longer applicable since Users and Groups have been changed to just users.

please help.

you need to install the extensions pack [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by Habanero101 on 2013-04-26
I found the answer here:
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Basically:
[COLOR=#333333][FONT=Ubuntu]Open Software Centre, Search "Gnome-System-Tools" and install.

[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Tap Super Key to get the Dash, Type "user" and click the Users and Groups icon to start up the Groups Manager. [FONT=inherit][/FONT]Click "Manage Groups", find vboxusers, click properties, add your own and any other desired users to the vboxusers group.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Click OK.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Now log out and back in[/FONT][/COLOR]

---

### Post by Habanero101 on 2013-04-26
> **haqking said:**
> you need to install the extensions pack [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

I did install the extension pack.

---

### Post by gscratch on 2013-05-03
If you're no longer having trouble, you may ignore this

I had a similar problem with my VirtualBox guest (in my case, Windows XP, but I don't think it matters) seeing USB devices.  In addition to installing the extensions pack, 
You must also create a Filter in the VB Admin console 'Filters' section, either build one manually, or create one from the add Filter icon; it should list the device if it's plugged in, and allow you to create a specific filter.
Then, with the guest in focus (ie, NOT the VB Admin window, which is where I stumbled), there is a Devices menu choice.  Click it and select the USB device from the list; Windows makes that little "I just found a USB device" noise.  To unmount the device, click Devices and uncheck the device; WXP makes that little "a USB device was removed" noise and the host Ubuntu sees the device immediately.

I got confused because the guest saw my USB mouse without me doing anything.

---

