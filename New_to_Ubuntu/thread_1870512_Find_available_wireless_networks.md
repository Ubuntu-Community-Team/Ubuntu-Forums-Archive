---
title: "Find available wireless networks"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by peterson43 on 2011-10-27
I can't seem to get my wireless working on my laptop. I'm running Ubuntu 10.04. The wireless has worked in the past (as recently as 2 weeks ago), but I can't get it to work anymore. 

When I click on the network manager icon in the panel, the wireless networks don't even show up. The wireless should be turned on since the light indicating the wireless network is on; I've even pressed Fn+F5 to toggle the wireless on and off and it still doesn't appear in the network manager. 

The only network that shows up when I click on the network manager icon is called 'lo'. There used to be 'wlan0' and 'eth0', but for some reason they're gone and I can't figure out how to get them back. (I don't have an ethernet connection where I am right now so I can't check to see if the eth0 connection would show up if there was a connection). 

There doesn't seem to be a hardware issue since if I boot up in Windows instead of Ubuntu then the wifi recognizes several available networks, and I can connect to the internet without any problems. 

How do I get Ubuntu to enable 'wlan0' again and search for available wireless networks.

---

### Post by Rex Bouwense on 2011-10-27
Ensure that "Enable Wireless" is checked when you right click Network icon in the top panel.  It happened to me once when I was screwing around and somehow it ended up getting unchecked.

---

### Post by peterson43 on 2011-10-27
> **Rex Bouwense said:**
> Ensure that "Enable Wireless" is checked when you right click Network icon in the top panel.  It happened to me once when I was screwing around and somehow it ended up getting unchecked.

Actually, part of what is confusing me is that when I right-click on the Network icon I don't have the option to click "enable wireless." I can click on properties which gives me the Connection Properties dialog box. 

In this there usually is an option to choose wlan0 for the wireless network, but this was missing for some reason. I finally was able to get it back by just clicking in the dropdown menu and typing in wlan0. Now the wireless network appears in the Connection Properties and it also appears on the panel, but it shows that it is disconnected. See the attached picture.

The status says that it is disconnected, but I don't see how to make it connected. When I click on "configure" there doesn't seem to be any options that I can find to enable wireless. 

Any help?

---

### Post by gandaran on 2011-10-28
did you have to install wireless card drivers when you first installed Ubuntu 10.04?
and have you recently updated to a new kernel? 
if you did install drivers then you will probably need to install again for the new kernel.

---

