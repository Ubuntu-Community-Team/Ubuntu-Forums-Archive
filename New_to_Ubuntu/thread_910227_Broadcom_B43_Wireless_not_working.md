---
title: "Broadcom B43 Wireless not working"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by LeWench on 2008-09-04
I just finished reinstalling Ubuntu because I did something and it wouldn't boot (still learning linux) 


Well this is my problem, I setup Wicd (removed network-manager) I also edited the interfaces document and added a "#" to everything but auto lo, and iface lo inet loopback. Just so that you can see it here it is:

"auto lo
iface lo inet loopback


#iface wlan0 inet dhcp
#wireless-key ********** (Changed to * for security reasons)
#wireless-essid **** (Changed to * for security reasons)

#auto wlan0

#iface eth0 inet dhcp

#auto eth0



#iface eth0 inet dhcp

#auto eth0"


Once I did that, I setup the session menu so that it boots when Ubuntu is started (command: "/opt/wicd/tray.py")

Everything looks fine but I cannot get my wireless to work. I open Wicd and I get a "No wireless networks found"

When checking my Hardware Drivers for Broadcom B43 Wireless driver, under status is says In use. The box is unchecked. 

I have tried various methods but I still cannot figure this out. I bet its something dumb that I completely missed. Can anyone help me with this?

---

### Post by drs305 on 2008-09-04
> **LeWench said:**
> I have tried various methods but I still cannot figure this out. I bet its something dumb that I completely missed. Can anyone help me with this?

Sometimes I have to go back into System, Admin, Network. Unlock and recheck (and reenable if necessary) my wireless settings.

---

### Post by LeWench on 2008-09-04
> **drs305 said:**
> Sometimes I have to go back into System, Admin, Network. Unlock and recheck (and reenable if necessary) my wireless settings.

Ok, went in there unlocked it, checked the box (added the SSID that I use) it reconfigured the interface. Still nothing.

---

### Post by drs305 on 2008-09-04
After your reinstall, did you redo whatever steps you took on the previous install to enable your Broadcom wireless card in the first place?

You said you replaced network-manager. Do you know if network-manager was working before you replaced it with wicd?

Do you have the capability of returning to network-manager if you know it worked with that before or after the reinstall?

---

### Post by chadeldridge on 2008-09-04
There are also about a billion threads on the Broadcom wireless chipset and how to get it working.  Your best bet is to go with the ndiswrapper, you should find a good install guide on the forums.

---

