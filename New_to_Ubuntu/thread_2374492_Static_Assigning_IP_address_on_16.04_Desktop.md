---
title: "Static Assigning IP address on 16.04 Desktop"
date: 2017-10-16
forum: New to Ubuntu
---

### Post by anickless on 2017-10-16
Trying to assign a static IP address however the GUI side when I create a static IP doesn't seem to work. 

Trying to edit the etc/interfaces but when I added the entry in for eth0 the interface became unresponsive. Not sure if I am doing the entry correctly.

Yes I am being a total Newbie with this basic question but can't seem to get it going. When everything is on auto things work, but I need to assign a static ip.

---

### Post by Kirboosy on 2017-10-16
Let me be the first to welcome you to the forums!

Why not just use the GUI tool built into Ubuntu to manage the interface? If you click on up and down arrows on the top right you can edit the connections. From there you can quickly and easily setup static IPs.

If you insist on using the command line way you need to post the configuration you are trying to use on /etc/interfaces.

---

### Post by anickless on 2017-10-16
I have tried via the gui tool and command line and neither are successful so I am doing something wrong for sure.[ATTACH=CONFIG]277141[/ATTACH]

Here is the /etc/network/interfaces screenshot.

---

### Post by ubname on 2017-10-16
you have a missing dot (10.254) in gateway

also the dns looks weird you cant try to use 8.8.8.8 8.8.4.4

but you surely can use the network setup interface in ubuntu

---

### Post by anickless on 2017-10-16
thanks for the input, the gui was not working for me but I corrected my error on the addressing and dns server. I was also running it on a VM so I had to change the settings to make sure on VMware fusion it had its own ethernet connection and my hyper-v one I had to cycle the refresh a couple of times to make sure the mac address was picking up.

---

### Post by HermanAB on 2017-10-16
Howdy,

The best place to set a static address is in the DHCP server.

---

### Post by leunam12 on 2017-10-17
Try the DNS suggested, it may work, but I noticed that your computer's ip address is on a different subnet, are you trying to do that intentionally? If your gateway is 10.150.1.254 then your IP address should be 10.150.1.xxx
At least that is how I understand it should be.

---

### Post by HermanAB on 2017-10-17
There is a dot missing in your gateway address.

---

