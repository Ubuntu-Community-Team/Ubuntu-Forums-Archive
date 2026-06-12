---
title: "Thinkpad Modem"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Niloc on 2008-08-27
I have an IBM Thinkpad T21 which has been an excellent laptop.
When I was using Windows, the laptop made available its internal modem for dialup. Then I moved and went to ADSL which is excellent. I am now moving again to a place where ADSL is not available so I want to use dialup again but Linux does not seem to know about modems etc...

How can I connect or do I have to re-install Windows XP to get on the internet??

---

### Post by stmiller on 2008-08-27
Dial-up internet works fine in Linux. Check out this guide:

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by lswb on 2008-08-27
Most likely you can find a driver that will enable your laptop modem to operate with linux. In a terminal try the command lspci|grep -i modem and see if you get the name and model for your modem. Then google for something like "linux driver modem "your make and model number" You can also take a look at the website [http://linmodems.org](http://linmodems.org) for help in identifying your modem and the drivers.

---

### Post by phidia on 2008-08-27
There is also the Ubuntu dial up modem wiki [here]("https://help.ubuntu.com/community/DialupModemHowto").

---

