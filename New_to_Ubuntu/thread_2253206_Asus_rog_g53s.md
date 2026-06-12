---
title: "Asus rog g53s"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by PxApollo on 2014-11-18
hi 

i am new to Ubuntu obviously ,1st OS  was introduce  by my uncle , i am  using windows since 2000 , so totally no idea Ubuntu is , i got tired of windows having all registry problems and multiple virus , so i decided to use Linux , now for my machine problem i am using asus ROG G53S , 
1st battery is not charging when i plug out the power source the machine turn off totally , ( battery works for 4hrs in windows os )
2nd i notice my HDD is hot never encounter in windows even playing 
3rd my keyboard back-lit  lights  not automatically on i need to switch it on time to time
4th wifi having weak signal 
last problem i love the  OS it amaze it made me feel like pro in movie like CIA typing on terminal etc , 
thanks 

please move my thread if this is not the right place for my question

---

### Post by DarkSapphire on 2014-11-22
Battery-  Ubuntu seems to not be detecting your drivers to well, this may cause the horrible battery life
HDD-  Ubuntu is known for having horrible temperature management.  Enter this in the terminal   
[COLOR=#000000]sudo add-apt-repository ppa:webupd8team/jupiter[/COLOR]
[COLOR=#000000]$ sudo apt-get update[/COLOR]
[COLOR=#000000]$ sudo apt-get install jupiter[/COLOR]
Keyboard- Driver related issue, find your keyboards drivers and see if you can get it in linux
Wifi-  Driver related issue, find your wi-fi chipsets driver.

Sorry I wasn't as descriptive as before, I was new to the forum.

To get proper drivers, click on the launcher icon in the top left corner.  Then search additional drivers, and wait for Ubuntu to get the drivers.  

If you need any help installing or using jupiter, look at this link: [http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

Remember to be careful whenever you use sudo in your commands.

---

