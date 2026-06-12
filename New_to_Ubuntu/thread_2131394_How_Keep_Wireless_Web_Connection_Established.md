---
title: "How Keep Wireless Web Connection Established?"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by TomBrooklyn on 2013-04-01
How Keep Wireless Web Connection Established?


How can I keep a wireless internet connection established with CAELinux on a laptop computer on my home WiFi LAN?


Currently, I am frequently and repeatedly being asked to enter either my login password or the wireless WEP code.

I have configured the laptop to not require a password on startup (login.)

---

### Post by wildmanne39 on 2013-04-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by erikstrawn on 2013-11-17
I saw there's been no follow up on this, but I'm having a similar issue with my desktop computer. When I boot up, I always have to enter my wireless password. Some days I can stay on for hours with no issues, and others I have to put in my wireless password every couple of minutes. It coincides with a drop in wireless reception, but I'm only 20 feet from the router. My laptop has no issues if it's on the same desk or even three rooms away. I've also noticed that when I tried to play Urban Terror, I lost connection about every 1:55 for ten seconds or so (it's been a few months, so pardon if I'm a little off on the time). Any ideas?

---

