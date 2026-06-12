---
title: "Weird wireless issue"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Homeroast on 2012-07-02
I've recently installed Ubuntu 12.04 on a basic notebook with an i3 intel processor with  500 GB hard drive and 4 GB ram.  

It seems like the installation went fine except for one weird issue.  When I launch Firefox, it loads the Google start page (that's not the weird part.)

The odd thing is, it won't load any page other than the Google start page.  If I navigate to another site it simply won't load.  

Is there a way to correct this issue so other sites I go to will load? 

I've never seen this phenomenon before.  This might be a problem with my modem/router but I'm not running any firewalls. (I think there might be a chance my modem has gone bad, but I'm not sure.)

Any suggestions?

Thanks!

---

### Post by wildmanne39 on 2012-07-02
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by robtygart on 2012-07-02
> **Homeroast said:**
> I've recently installed Ubuntu 12.04 on a basic notebook with an i3 intel processor with  500 GB hard drive and 4 GB ram.  

It seems like the installation went fine except for one weird issue.  When I launch Firefox, it loads the Google start page (that's not the weird part.)

The odd thing is, it won't load any page other than the Google start page.  If I navigate to another site it simply won't load.  

Is there a way to correct this issue so other sites I go to will load? 

I've never seen this phenomenon before.  This might be a problem with my modem/router but I'm not running any firewalls. (I think there might be a chance my modem has gone bad, but I'm not sure.)

Any suggestions?

Thanks!

That page you see is just an Html document that loads at the start up of Firefox, your not connected to the internet. 

Please go to your launcher and look in Applications>System>Additional Drivers, look to see if your wireless driver has been activated.

Or just type "Additional Drivers" in the launcher search menu.

---

