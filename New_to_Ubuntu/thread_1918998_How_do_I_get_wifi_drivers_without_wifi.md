---
title: "How do I get wifi drivers without wifi"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by SAIYANPRINCE on 2012-02-02
Just installed ubuntu 10.04 netbook on my netbook and I cant use wifi, it says I need a driver. How or where can I get the required driver? 

If it matters at all then I'm on a HP mini, 1gb ram 1.6 processor installed ubuntu 10.04 netbook on a 4gb stick

Sorry if this is a stupid question but yeah I have no clue any help would be great ty

---

### Post by sudodus on 2012-02-02
Often but not always, there is a built-in wifi driver in the linux kernel. So you need not download anything. In your case maybe your computer is too new for Ubuntu 10.04 LTS. Try the current version, but on a netbook I would recommend the lightweight versions of Ubuntu: Lubuntu or Xubuntu.

Download the iso files and test them running live sessions from the USB drive.

So, the best method is to use the built-in drivers in the kernel, and new  kernels have drivers for new cards or chips. An alternative is to use  windows drivers via ndiswrapper, but you 'must be lucky' to get a stable  connection that way.

There is a lot of information about wifi on the internet for example

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/](http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/)

---

### Post by SAIYANPRINCE on 2012-02-02
> **sudodus said:**
> Often but not always, there is a built-in wifi driver in the linux kernel. So you need not download anything. In your case maybe your computer is too new for Ubuntu 10.04 LTS. Try the current version, but on a netbook I would recommend the lightweight versions of Ubuntu: Lubuntu or Xubuntu.

Download the iso files and test them running live sessions from the USB drive.

So, the best method is to use the built-in drivers in the kernel, and new  kernels have drivers for new cards or chips. An alternative is to use  windows drivers via ndiswrapper, but you 'must be lucky' to get a stable  connection that way.

There is a lot of information about wifi on the internet for example

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/](http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/)

How do I enable the drivers in the kernel??

---

### Post by TheFu on 2012-02-02
That is a really good question.  You can:
a) try a different distro that is known to support your specific netbook model
or
b) specify the details of the wifi network adapter, go find a driver using a different  PC, download the driver to a USB drive, plug the USB drive into the netbook, build the driver for your kernel, then load the driver
or 
c) plug the netbook into a router and restart the networking service(s) to get on the network, then do "b".

[http://www.hpminiguide.com](http://www.hpminiguide.com) may be helpful, if the account isn't suspended.
[http://liliputing.com/2010/06/roundup-of-linux-distributions-that-play-mostly-well-with-the-hp-2133.html](http://liliputing.com/2010/06/roundup-of-linux-distributions-that-play-mostly-well-with-the-hp-2133.html)

If you google the exact model of your HP mini and Linux distro, you may find recommended distros. Seems there are lots of different HP-Mini models.  I wish I could help more.   Finding a specific distro known to work with your hardware is the easiest for someone new to Linux.

---

### Post by sudodus on 2012-02-02
> **SAIYANPRINCE said:**
> How do I enable the drivers in the kernel??

The appropriate driver will be enabled automatically (if there is one for your particular card or chip). Otherwise I refer to the links in my previous post.

---

### Post by mastablasta on 2012-02-02
use a cable to connect to internet or get a deb or source package of drivers in an internet cafe or similar.

---

### Post by 3rdalbum on 2012-02-02
Ubuntu 10.04 is quite old now - nearly two years old. It's like trying to run Windows 98 on your netbook.

I'd recommend you try the latest version, 11.10. It may be able to run your wireless card out-of-the-box. Even if it can't and you need to plug your computer into your modem via Ethernet cable (to get the driver), you will benefit from having more up-to-date software and a more modern user interface.

---

