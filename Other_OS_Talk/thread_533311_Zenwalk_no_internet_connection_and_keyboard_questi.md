---
title: "Zenwalk: no internet connection and keyboard question"
date: 2007-08-23
forum: Other OS Talk
---

### Post by tico on 2007-08-23
I've installed Zenwalk in a virtual machine (VirtualBox). It didn't set up my internet connection automaticaly (ADSL - router modem). I tried to set up it, the network config says sometimes "down" sometimes "up", but theres no connection. If I ping I get a network not reachable.
Any idea on how to solve that?
Another question: I'd like to have two keyboard layouts, but the keyboard config tool let me have just one. Is there a way to bypass this limitation?

Thanks.

---

### Post by tommcd on 2007-08-24
How do you connect in ubuntu? Does your ADSL require a username and password? Do you use pppoeconf? If you connect automatically with DHCP you should be able to launch xnetconf (zenpanel > xnetconf) and highlight eth0, check all the DHCP boxes, and click apply and you should be good.

---

### Post by b0ng0 on 2007-08-24
Without meaning to sound nasty, I think your best bet is posting in the Zenwalk forums.

(I just burnt a live cd of it, cant wait to try it :KS )

---

### Post by tico on 2007-08-24
> **tommcd said:**
> How do you connect in ubuntu? Does your ADSL require a username and password? Do you use pppoeconf? If you connect automatically with DHCP you should be able to launch xnetconf (zenpanel > xnetconf) and highlight eth0, check all the DHCP boxes, and click apply and you should be good.

My ADSL connection doesn't ADSL require a username or password (the router modem stores them). In Ubuntu, I use a static IP, but can use DHCP too. I've tried to check all the DHCP boxes, but still no connection.

Thanks.

---

### Post by tommcd on 2007-08-25
Perhaps installing in a virtual machine is causing a problem? Get the Zenwalk live CD and boot that up and see if you can get online. That way you can still try out zenwalk without installing it. If you get online run as root "lspci -v" to find you ethernet card, and run lsmod to find the driver used. Then if you install zenwalk on the hard drive run lsmod to make sure the driver is loaded. The root password on zenlive is "ZenLive". Here is the zenlive manual:
[http://www.zenwalk.org/modules/tinycontent/index.php?id=20](http://www.zenwalk.org/modules/tinycontent/index.php?id=20)

---

### Post by Tux Aubrey on 2007-08-25
I have Zenwalk running in Virtualbox and it appears it does not connect to the internet by default.

I raised the inbuilt eth0 interface with (as root)
```

ifconfig eth0 up
```

then I opened Zenpanel (System>Zenpanel)

The Network Settings utility is on the panel.

I selected DHCP for everything and Viola! I'm on-line.

---

### Post by tico on 2007-08-25
Tux Aubrey,

Thanks! It seems to work.

---

