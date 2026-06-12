---
title: "Can't get wifi to be seen on laptop..."
date: 2013-10-23
forum: New to Ubuntu
---

### Post by Ade_Snow on 2013-10-23
Hi all...

I have a HP 2133 laptop, I have just installed Ubuntu 12.04 over 10.4, and now can't see my wifi selection in the top right hand corner...
How do I get 12.04 to see the available wifi networks so I can connect to the internet?
Is it something to do with it not seeing/activating the hardware required?

Please help, it's driving me mad now...

Snowmonster

---

### Post by david98 on 2013-10-23
Can you see your wireless card when you type [COLOR=#000000][FONT=Consolas]ifconfig [/FONT][/COLOR]

---

### Post by david98 on 2013-10-23
If you can type this( [COLOR=#000000][FONT=Ubuntu Mono]sudo iwlist wlan0 scan) this will show available wifi connections.then type  ([/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]iwconfig wlan0 essid NETWORK_ID key s:WIRELESS_KEY) where network id type the network you want to connect to wireless key is your password. then type this [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo dhclient wlan0 it's a old basic way but will get the job don e simpley[/FONT][/COLOR]

---

### Post by Ade_Snow on 2013-10-23
Hi David98...

That didn't work, First one (Scan) = Interface doesn't support scanning
second one = Error for wireless request "Set ESSID" (8B1A) : SET failed on device wlan0 ; operation not permitted.

Any ideas?

Cheers for your time...

---

### Post by Ade_Snow on 2013-10-23
Hi David98...
Just done an update, and it's now showing up... sorry for wasting your time...

---

### Post by david98 on 2013-10-23
Not a problem glad to help if problem's solved click solved on thread tool's top right hand corner.

---

