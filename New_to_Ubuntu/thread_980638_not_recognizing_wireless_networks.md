---
title: "not recognizing wireless networks"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by aiBRETTy on 2008-11-13
I installed 8.10 two days ago and everything worked smoothly, except for my wireless wasn't working.  I have a Dell Inspiron 8600 and my wireless card is a BCM4306.  After trying to install the .inf file with ndisgtk, it turns out that the computer recognizes the modem (iwconfig and ifconfig both confirm), but the wireless networks still are not showing.  

I have rebooted.  I have checked to make sure that the Network and Wireless are both enabled.  I have read dozens of forum posts and I am just tired of messing with this. 

Can anyone please help me?

---

### Post by porchrat on 2008-11-13
check the ouput of 

```
lshw -C network
```

I know you've probably done that a thousand times by now, but at least it will tell you for sure whether or not your wireless module is CLAIMED or not.  If you see "UNCLAIMED" then the drivers are not actually using the wireless module.

If it shows up in "ifconfig" it does not necessarily mean that the thing is functioning, chances are this isn't the problem, but it is always good to be sure.

Also are you sure your wireless network is actually broadcasting it's SSID?  If it isn't then the network won't show up in a scan, you'd need to setup your wireless network connection to use that specific SSID when connecting.

Also do you use DHCP or a static IP?

---

### Post by aiBRETTy on 2008-11-13
ok, so I'm an idiot.  It says DISABLED.  How do I enable it?

---

### Post by Peter09 on 2008-11-13
Just as a basic check, make sure that the hardware wireless on/off switch is on.

---

### Post by aiBRETTy on 2008-11-13
Fn+F2 does not work after the install.  I can't seem to find a way to turn it on otherwise.

---

### Post by Peter09 on 2008-11-13
I was really checking for the hardware switch. Some laptops have a hardware switch on the front to turn the wireless on/off. This sometimes can get inadvertently switched off.

---

### Post by porchrat on 2008-11-13
> **aiBRETTy said:**
> ok, so I'm an idiot.  It says DISABLED.  How do I enable it?

Does it say "UNCLAIMED" anywhere?

---

### Post by aiBRETTy on 2008-11-13
nope.  Nothing was labeled unclaimed, but it did say disabled by the wlan0 section.

Anyone else have ideas or can direct me to a forum with a possible answer for my problem.

---

### Post by aiBRETTy on 2008-11-13
When I get back to my house, I'm going to try [THIS]("http://linuxwireless.org/en/users/Drivers/b43").  I have no clue if it will work, but it seems like it might address my problem.

Does anyone have any knowledge about or previous experience with this program (b43-fwcutter)?

---

