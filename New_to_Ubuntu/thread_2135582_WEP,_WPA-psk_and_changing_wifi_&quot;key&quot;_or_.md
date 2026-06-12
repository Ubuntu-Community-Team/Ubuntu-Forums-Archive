---
title: "WEP, WPA-psk and changing wifi &quot;key&quot; or password"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-04-14
As the AT&T staff knows nothing of Linux and as I must change my 2Wire wifi-modem-router password as someone has started using it w/o permission, I tried to change the "key" as AT&T calls it. (Everyone else calls it a password). 

I opened the 2Wire page at: 192.168.1.254 and entered my "System Password" and changed Authentication from WEP-Open to WPA-PSK. I clicked the "Use Custom Pass Phrase", entered (for example) dalealan8933. That's 12 elements. I then clicked "Save" and the modem page went to blank and a moment later, Ubuntu went offline. I then tried to edit "Network Connections" and change "Wireless Security" from WEP 40/128-bit Key (Hex or ASCII) to WPA and WPA2 Personal. I added the new "key" or password and could not get back online.

---

### Post by sammiev on 2013-04-14
Delete your connection on your computer and try a fresh boot. Select your Wireless and hit connect, it will ask you for the new password or phrase under WPA/WPA2.

---

