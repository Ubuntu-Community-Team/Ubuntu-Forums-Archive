---
title: "wireless problems"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by jsdieorksw on 2008-04-25
I am very new to ubuntu. I dual-booted ubuntu 7.10 last week onto my new laptop along with vista. Everything seemed fine but  ubuntu won't recognize my wireless internet connection. It works fine while I'm in Vista so it's not the connection. There were a few blips while installing however. It said there was a problem while installing the security updates and another message popped up which ubuntu was running on a partition it's not meant (or something to that effect), I don't know if these have anything to do with it but i just thought it might. I want to eventually get rid of vista completely but not until I can at least access the internet through ubuntu. Can someone please help me? Thanks guys!

---

### Post by Saturn357 on 2008-04-26
You can try Network Manager. Use the Synaptic Package Manager to install this program. 

You will probably have to disable any other preconfigured networks you have. 

System--Administration--Networking
Select a network interface
Click the properties button
Deselect the radio button (It should say Enable this connection)
Click OK
Repeat this for every network that you see.

Once you've installed Network Manager and disabled any devices you want to control with it, you're ready to go. Log out and then log back into your account. Network Manager should recognize your wireless device and any other you disabled in the process.

Look in the top-right corner, and you'll see two computer screens with a red exclamation mark on it. It recognized, but nothing's happening. click this icon and a box appears showing the state of your interfaces

Select Connect to Other Wireless Network option
If you want to use a different wireless adapter than the one shown on the drop-down menu, click that menu and choose the interface you want.
Type the name of your wireless network in the Network Name box.
From the wireless security drop-down menu, select WPA2 Personal or, if unavailable, WPA personal
Type the network name you want to connect to in the Network Name box
Type your password in the WPA or WPA2 box
Click the connect button

Taken from the Ubuntu Linux for Mooks book. Hope this helps.

---

### Post by Saturn357 on 2008-04-26
Or, you could just get an ethernet and be done with it. It worked for me.

---

