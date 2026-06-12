---
title: "wireless help!! was working but not anymore"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by etheralthougt on 2008-08-04
I have an hp pavilion dv 6000 notebook with an Atheros wireless card. I was able to get the wireless working perfectly using madwifi tutorials. However, I may have accidentally unchecked the enable wireless in the network drop down (in the upper right hand corner). 
I cannot connect/find any wireless networks.
Under network manager, I can see the wireless networks around me (I do have roaming wireless enabled). But when I look at the network short cut up top, I do not have an option for any wireless connections. 

When I run the command to check for connections, my wireless is there. But when I try to scan (under ```
sudo iwlist ...
```), I get an error.  

What do I do?? Do I need to reinstall things?
Any help would be awesome!!!

---

### Post by beanhead on 2008-08-04
right click the wireless icon and click enable wireless.

---

### Post by etheralthougt on 2008-08-04
I do not even have that option available to me. the only connection option I can see is one for wired (and that is currently grayed out since I do not have any Ethernet connection at this time)
And am still baffled about this.



And to fix my previous post, I meant ifconfig not iwlist.
Sorry.

---

### Post by beanhead on 2008-08-04
ok an easy fix would be to restart and uncheck the "save session for next log in, so if you havent restarted the computer sence you changed the wireless options when you click on the log out and it gives you the options like restart and shut down etc.. uncheck the box and restart, so it will go back to your previous settings. of that doesnt work you will have to go to system settings and make some changes for your network settings just make them default so they are set to auto dchp :D that should do it

---

### Post by etheralthougt on 2008-08-05
I did not see any options for saving sessions for next log in, but I already had restarted my computer so I do not think it would have helped anyways. 
Also, I've tried connecting to specific networks using the auto dchp, and my network interface is updated, but under the network shortcut up top, I still do not have the option to connect to any wireless networks. 
I still want to keep my wireless on roaming since I live in an area where there are multiple networks I can connect to. 
I'm still confused as to why wireless connections isn't an option in the shortcut when it is listed in the network manager. :confused:
thanks for your help!!

---

