---
title: "question before install"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by mannylinu on 2012-10-19
Hi-I have an IBM thinkcentre desktop running windows 7 ultimate.
My internet, wireless internet router, hp printer all run on this and my wife needs these to work ok.
Right now her laptop is connected to our "home group" with our desktop pc-is there something similar in Ubuntu?
I want to try Ubuntu but wanted to know if there is any type of hardware compatibility program I can run first before trying/ installing it?
Thanks

---

### Post by albandy on 2012-10-19
You can run it in live mode, without installing anything. Simply boot your computer with the Ubuntu CD. A boot menu will appear allowing you to test or install ubuntu.

---

### Post by mannylinu on 2012-10-19
Does the live cd allow you to test your wifi home network or printer connection?

---

### Post by Cheesemill on 2012-10-19
Yes, it lets you test everything.

AFAIK the only OS that supports Windows homegroups is Windows 7 (and 8 when it is released), even XP can't connect to a homegroup.

You can easily remedy this by setting up normal Windows shares on your other machines instead of using your homegroup.

---

### Post by mannylinu on 2012-10-19
So could I have my wife print something from her windows 7 laptop wireless to a printer connected by usb to my ubuntu desktop ?

---

### Post by mikewhatever on 2012-10-19
> **mannylinu said:**
> Does the live cd allow you to test your wifi home network or printer connection?

It depends. Some wireless cards won't work in the Live CD/USB environment (Broadcom, Atheros), because they'd require firmware or driver activation, which can only be done post-install.
There is a System Testing utility preinstalled, but, it will obviously be able to test only the hardware that works properly.
For thorough testing, I'd recommend installing Ubuntu to a small partition as dual boot or the Windows installer.

---

### Post by Wim Sturkenboom on 2012-10-19
I suggest that you make it a dual boot and try it all out. If it does not work, you can restore the MBR and (using Windows) clainm the lost disk space back. Whatever you do, do not delete the Ubuntu partition(s) from Windows before you have restored the MBR.

> 
So could I have my wife print something from her windows 7 laptop wireless to a printer connected by usb to my ubuntu desktop ?

I have a HP laserjet connected to a desktop via USB. The desktop is connect via cable to my router. I have 3 laptops running various flavours of Linux and Windows connected via wifi to the router and they can all print (as long as the printer and the desktop are switched on).

---

### Post by pqwoerituytrueiwoq on 2012-10-19
> **mikewhatever said:**
> Some wireless cards won't work in the Live CD/USB environment (Broadcom, Atheros), because they'd require firmware or driver activation, which can only be done post-install.
my Atheros chip has worked flawlessly since 10.10, i think 10.04 needed a driver cause of a lossy connection
```
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
```

anyway you can connect a windows system to a usb printer on linux, you just need the address
i would use this url for a network printer on windows here
[http://10.0.0.50:631/printers/Deskjet-F4400-series](http://10.0.0.50:631/printers/Deskjet-F4400-series)

you can get this from system-config-printer right click the printer and click properties, windows does not know what ipp is so you use http
the ipp url does not need the :631 but if you use http it does

---

