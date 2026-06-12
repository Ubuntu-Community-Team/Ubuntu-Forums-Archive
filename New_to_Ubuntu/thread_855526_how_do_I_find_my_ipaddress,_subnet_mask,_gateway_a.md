---
title: "how do I find my ipaddress, subnet mask, gateway address?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-10
yes those three things so that I can finally get my aircard running.  Prefer to use the CLI when possible.  thankyou.

---

### Post by sisco311 on 2008-07-10
```
ifconfig
```

---

### Post by DGortze380 on 2008-07-10
I assume you're using a broadband isp with a modem and router? (correct me if thats a wrong assumption).

Are you using DHCP?
If so, and you have already installed the drivers for you're wireless card. Just use the network tray applet to selet your home network, enter encryption key as need, make sure you're in roaming mode (DHCP).

If not, use ifconfig to set up your connection.
man ifconfig
for more info.

If you're asking about you're routers ip, subnet and gateway, that's a little differnet. You need to connect to your router to get those. the gateway is what you type to access the router (usually something like 192.168.0.1) subnet for that gateway would be 255.255.255.0 and your routers ip is your external ip address which you don't need to do anything with unless you're trying to access your home network from the internet.

---

### Post by adamogardner on 2008-07-10
no   you are incorrect about a modem and router.  I have an air card and a 60 dollar verizon bill every month.  do you know what I mean?  just an air card.

---

### Post by DGortze380 on 2008-07-10
Sorry, a quick google search didn't turn up anything useful, I have no experience with the verizon aircard myself, maybe someone else is using it?

bump for ya.

---

### Post by stchman on 2008-07-10
```
ifconfig -a
```

---

### Post by sdennie on 2008-07-10
This might help you set things up: [http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

---

### Post by adamogardner on 2008-07-10
im seeing multiple addresses under lo and wlan there inet bcas and mask  which is mine?

---

