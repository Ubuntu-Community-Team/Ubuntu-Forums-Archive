---
title: "Network Connectivity Issues"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by unetbrks9622 on 2012-02-01
Hello all, I'm fairly new to ubuntu.  I have a dual boot on my dell laptop and my acer aspire one d255 netbook is solely ubuntu.  I was able to get my wifi connections working on my netbook but lately I have been getting kicked off the network every 30 seconds or so.  The connection indicator says I am still connected but internet pages won't load.  I have to manually disconnect from the wifi and reconnect to get the internet going again, only to be kicked off 30 seconds later.  My dell laptop's wifi works fine with ubuntu, so this makes me believe it is a driver issue.  Thanks for any help!

---

### Post by wolfen69 on 2012-02-01
I've seen this numerous times, and sometimes just resetting your modem and router will fix it. Just unplug the power to them for a few seconds, plug back in, and wait a minute. Report back what happened.

---

### Post by unetbrks9622 on 2012-02-02
I'm on my schools campus wide network.  No way for me to unplug anything.  I have found that if I repeatedly hit the refresh button the pages will load, but not until I've hit the refresh button a good number of times.

---

### Post by UltimateCat on 2012-02-03
When you are able to find  out what Network Interface Card you have inside your DEll.

The command for the terminal to find that out is:
```
lspci
 
```

Once you know your card you can do research and find the driver that the manufacturer makes for your card and dowload it and then install.

Also, I recently learned that keeping my cell phone close to my laptop was effecting it and the connectivity and kept getting kicked off the net.  You may want to keep your cell away from you Dell.

Hope this helps

[http://help.ubuntu.com/](http://help.ubuntu.com/)

---

