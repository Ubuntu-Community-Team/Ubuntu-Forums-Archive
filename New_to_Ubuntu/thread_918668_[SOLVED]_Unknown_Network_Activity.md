---
title: "[SOLVED] Unknown Network Activity"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by expatCM on 2008-09-13
How do I find out what process is causing network activity?

I have netspeed installed and it used to show zero activity if there were no programs accessing the Internet.  Now even with there being no active programs there is still download and upload activity.  Not huge amounts, like 50-100KiB/s in both directions.

I have blocked the firewall and the activity stops so I know it is real.  I have looked at the System Monitor and the only process running is gnome-system-monitor.  

So how do I work out which process is active with network activity?

---

### Post by jw5801 on 2008-09-13
Try `nethogs'.

```
sudo apt-get install nethogs
sudo nethogs <interface>
```

Where <interface> is the name of the network interface you're using to connect to the internet (eth0, wlan0, etc).

---

### Post by expatCM on 2008-09-13
Nethogs is a nice program ...  easy to use and delivers the information needed.  Perfect.  I am so lucky that ubuntuforums is here ...  I would never have found this in a month of Sundays ... 

Thanks for your help.

---

