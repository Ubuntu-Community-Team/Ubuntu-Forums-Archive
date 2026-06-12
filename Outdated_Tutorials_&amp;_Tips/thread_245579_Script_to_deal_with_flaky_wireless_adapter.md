---
title: "Script to deal with flaky wireless adapter"
date: 2006-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by peabody on 2006-08-28
Note: this probably doesn't work if use NetworkManager.  I don't use it.

I have WG111 version one and while it's working beautifully in dapper thanks to [these](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29) instructions, I've noticed that for no good reason the interface just dies on me and no amount of fiddling in the Network dialog can fix it.  What does seem to fix the problem, is bringing the interface down, removing the ndiswrapper module, removing the usb stick, reinserting the ndiswrapper module, and reinserting the usb stick.  I've written a gui script that automates this procedure.  Save this somewhere and set execute permissions on it via the nautilus properties dialog:

```

[FONT="Courier New"]
#!/bin/sh

# replace this with the network interface of your flaky device
IF=wlan0

zenity --title="Redo ndiswrapper" --question --text "Are you sure you wish to remove ndiswrapper?"
if [ $? == 0 ]; then
    gksu ifconfig $IF down
    gksu 'modprobe -r ndiswrapper'
    zenity --title="Okay to remove" --info --text "Remove the USB stick"
    gksu modprobe ndiswrapper
    zenity --title="Done" --info --text "Okay, reinsert the usb stick and reconfigure your network settings."
    gksu ifconfig $IF up
fi

[/FONT]

```

Double click to run.

On occasion I still have to deactivate and reactivate the device in the network dialog after doing this, but I've found this to work nicely on my machine.  Hopefully this is useful to someone else, or if someone knows of a way to make my USB adapter more rock solid, please let me know.

---

