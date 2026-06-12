---
title: "Specify the wifi for autoconnection"
date: 2014-11-23
forum: New to Ubuntu
---

### Post by Hellboy256 on 2014-11-23
I have different wifi's available (lets call them 'wifi1' and  'wifi2'), when starting Ubuntu it automatically connects to 'wifi1'. Is it  possible to set a configuration so it first tries to connect to 'wifi2'  (and if not possible then to `wifi1')?

---

### Post by pfeiffep on 2014-11-23
Perhaps remove wifi1  last character  of password ... I have 3 wireless networks visible to me (2 of which are next door neighbors - I don't have login credentials)

---

### Post by Hellboy256 on 2014-11-23
I have access to both wifi's. The problem is when connecting to 'wifi1' it also needs a basic browser authentificaton and 'wifi2' not. But I don't want to loose the configuration for 'wifi1' by simply removing it since I am not always able to connect to 'wifi2'...

---

### Post by grahammechanical on 2014-11-23
Set WiFi2 to automatically connect when it is available but do not set WiFi1 to automatically connect. When WiFi2 fails to connect, Network Manager will offer altenatives. One of which will be (may be) WiFi1. The connection settings should already be in Network manager. So, it would then be only a matter of clicking WiFi1. I have not tested this.

Regards.

---

### Post by sandyd on 2014-11-23
Choose 'Edit Connections' in the network manager applet, and choose wifi1.

Uncheck the box indicated in the below screenshot.

Wifi1 should no longer automatically connect :)
[ATTACH=CONFIG]258167[/ATTACH]

---

