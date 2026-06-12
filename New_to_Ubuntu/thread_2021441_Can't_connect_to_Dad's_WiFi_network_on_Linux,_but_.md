---
title: "Can't connect to Dad's WiFi network on Linux, but I can connect on Windows7"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by js9 on 2012-07-09
Hello, everybody.

At Dad's home, I can't log into his WiFi network in Linux, but can log into his WiFi network in Windows 7. 
In Linux, when I select Dad's WiFi SSID, the icon just gets the whirly thing. It never stops and I can never log on. :-(

Can anyone tell me what's going on?

Radio Type is 802.11g.
Security is WEP.
Jenny

---

### Post by Rex Bouwense on 2012-07-09
I have had this happen to me before.  All that I had to do was delete the network and then allow the network manager to find it again.  Also ensure that you have enabled Wireless.

---

### Post by js9 on 2012-07-09
Rex,
How do you delete a network?

---

### Post by Rex Bouwense on 2012-07-09
Right click your network manager and navigate to edit connections.  What you are interested in changing is Wireless so navigate to that.  Find your Dad's network and delete it.  Back out.  Sortly the network manager will find it again and you will get a notification that there are networks available.  Choose your Dad's and connect.  You will be asked for the passphrase or password which you must enter.

---

### Post by js9 on 2012-07-09
Rex, 
Your solution (deleting network and reconnecting) was *the* solution! Thanks.

J

---

