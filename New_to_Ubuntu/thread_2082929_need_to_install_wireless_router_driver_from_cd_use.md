---
title: "need to install wireless router driver from cd useing wine for ubuntu 12.4"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by vegas89 on 2012-11-10
I have the driver install cd for my wireless router. I have the latest version of wine already installed on this new computer.  How do I use the cd along with wine to get it to play and install, This is a router I was using with my old computer running windows xp. I now have the wireless router hooked up and running my wifes laptop, but I need to get access to the router configuration so I can change the pass code information. I need to get this installation cd to run on this new desktop computer. The cd is probably only readable in a windows format.  I have not been able to find any tutorials to help me accomplish this.  Can someone  please help me with this issue?  :confused:

---

### Post by uclugLee on 2012-11-10
Can you bring up the GUI of the router in a browser?  Normally the IP address of a home router is 192.168.1.1 or 192.168.0.1.  You shouldn't need to install anything if all you want to do is log into the GUI of the router.

---

### Post by NikTh on 2012-11-10
> **vegas89 said:**
>  I need to get access to the router configuration so I can change the pass code information.

Hi,
If this is what you want to achieve , then plugin an Ethernet cable , click on network-manager and click "Connection Information" , at the opened window you will see "Default route" . 

Open Firefox and write these numbers at address line and normally will redirect you to router's configuration page. 

Thanks

---

### Post by newb85 on 2012-11-11
If you don't have Windows, the CDs of Windows drivers you get with devices make good coasters, and not much else.  Windows drivers on Wine may sound like a good idea, but it won't get the job done.

---

### Post by squakie on 2012-11-11
+1  Many people confuse setting up a driver in Wine so that Linux can access things.  Doesn't work that way - anything you install in Wine is known to Wine only.

Also, +1 on NikTh and others who have pointed out going to the web address for the router configuration page.  You can do that from any other computer/device that has net access.

---

### Post by Mark Phelps on 2012-11-11
You can not use Wine to install drivers.  Even if the driver install program ran, it would do no good, because Linux doesn't use Windows drivers.

Also, Routers don't use drivers.

---

### Post by vegas89 on 2012-11-11
Alright beanheads, I now understand all that. I just plugged the router straight into my wifes laptop, she has windows 7 on it, haven't been able to convert her to our side yet. Then I just ran the router set up disk and reconfigured the router as we wanted.  I guess it is a good idea to keep a working version of windows somewhere to use for certain things.  As always I am learning!!  ):P

---

### Post by newb85 on 2012-11-11
Glad you got that working.  For the record, though, the router setup disk is really an unnecessary extra.  Simply typing the router's IP into the address bar of a machine connected to the router (by either ethernet or wlan) would bring up the configuration options for the router.  This could be done from either Windows or Ubuntu/Linux.

---

