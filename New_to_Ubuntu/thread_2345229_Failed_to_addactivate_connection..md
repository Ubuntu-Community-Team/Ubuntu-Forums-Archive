---
title: "Failed to add/activate connection."
date: 2016-12-01
forum: New to Ubuntu
---

### Post by revanthprime on 2016-12-01
[COLOR=#111111][FONT=Ubuntu]I've recently installed Ubuntu 14.04 on my laptop, the wifi is connecting to my home wifi as usual but whenever somebody uses my laptop in guest mode, it's not connecting to the wifi. It shows this error.

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Failed to add or activate connection.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu](0) Active connection could not be attached to the device.

Any ideas on how to solve this issue?[/FONT][/COLOR]

---

### Post by yetimon_64 on 2016-12-02
There is one setting you should check in Network Manager. To do so right click on the network manager icon in the notifications area of the top toolbar and choose "Edit Connections", choose your wifi network and then click "Edit". On the next window that pops up choose the "General" tab and ensure the setting "All users may connect to this network" is ticked. Save the settings and try again.

I am on an xfce desktop on ubuntu 14.04, but am still using Network Manager as does the standard install. Check the screenshot below for an image of the setting I suspect you need to change, it is the second tick box shown on the General tab (I have very roughly "smudged out" my network name for privacy reasons :)).

---

