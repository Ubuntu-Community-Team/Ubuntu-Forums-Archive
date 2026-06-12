---
title: "How to have a printer available for network PCs?"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by palmgrower on 2013-11-29
13.10 64 bit
Printer: Samsung SCX 4623F
Modem: Ubee 3611
Router: WD N900

1) Printer connected to router USB is not recognized by the router. (192.168.x.x doesn't show the printer.) To have the router recognize the printer, a printer driver (Windows version only) needs to be executed.
2) The printer does not have wifi or ethernet connectibility.


Q1) Is there a way to have the printer connected to a network PC and have the printer available to all network PCs?
Q2) If not, which router(s) with usb printer port works in ubuntu out of the box?
Q3) A new printer with ethernet connection costs $100-$200. Is this the best solution?
Thanks.

---

### Post by tgalati4 on 2013-11-29
If you have a PC running ubuntu all of the time (24/7), then you simply hang it off of that PC and set it up, then make sure it is "published" or "shared" then it will show up to all PC's on the local network.

Don't know about Q2.

Most (if not all) HP printers with ethernet ports work out-of-the-box.  Don't give up.  Keep searching.  There may be a work-around.

With your printer plugged into the router and online, what is the output of:  (open a terminal)

```
ping 192.168.1.14
```

Control-C to quit the ping.  Of course, use the correct IP address for the printer.

Next, what happens when you do:  [http://192.168.1.14:631](http://192.168.1.14:631)  ?  Again substitute the correct address.

Some printers respond on port 9100, try that:  [http://192.168.1.14:9100](http://192.168.1.14:9100)

Did you correctly set up the network parameters in the router?  Perhaps you need to set up a pinhole in the router's firewall to allow traffic through port 631 or 9100, or even 80.

---

### Post by palmgrower on 2013-11-29
Thanks for the tips. Yes, I have a PC that is 24/7. I will connect a printer to it and "publish" it. I will google publish and study. I will report back. Thanks.

The router is somewhat faulty. It recognizes USB hard disk automatically, but not printer. A printer driver needs to be installed in Windows. So the printer is not shown @192.168.1.1 (the router) and therefore without IP address.

---

### Post by palmgrower on 2013-11-29
Thanks. I was able to print from a newtork [COLOR=#b22222]UBUNTU[/COLOR] pc. Now I have to figure out how to do it from a network WINDOWS pc.

---

### Post by palmgrower on 2013-11-29
Now I can print from Windows pc.
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
I followed the link. One thing was missing afa I was concerned. I had to install samba first by running:
sudo apt-get update
sudo apt-get install samba

Thanks for the help.

---

### Post by tgalati4 on 2013-11-29
Glad that you got it sorted out.  You can now use the USB port on the router for doing *rsync* backups.

---

