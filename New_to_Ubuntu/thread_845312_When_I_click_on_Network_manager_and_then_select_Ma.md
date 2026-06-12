---
title: "When I click on Network manager and then select Manual Configuration nothing happens"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-30
Hi
Thank you for reading my post.
I have ubuntu 8.04 and I do not know for what reason following commands does not works as they worked before:

 - ```
gksudo nautilus
``` it asks me for the password but nothing happens after that.

When I right click on nm icon in the panel and then select Manual configuration, nothing happens :-(. it does not open the network configuration window.


Please let me know what is good to do and resolve the problem

Thanks

---

### Post by appi2012 on 2008-06-30
Can you make it a bit more clear? If you want to manually configure the network, then just go to "system" -> "Administration" -> "Network"

Unlock the network applet (click unlock)

Click on the network you want to set up (wireless, wired, etc.)

Click properties.

Uncheck "Roaming Mode", if it is checked, and then you should be able to configure your network.

I'm not sure why nm applets not launching the Network settings app though.

I hope that's what you needed ;)

---

