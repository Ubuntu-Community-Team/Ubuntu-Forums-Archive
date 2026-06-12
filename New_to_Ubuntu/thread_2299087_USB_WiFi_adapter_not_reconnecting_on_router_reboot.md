---
title: "USB WiFi adapter not reconnecting on router reboot"
date: 2015-10-15
forum: New to Ubuntu
---

### Post by shaun20 on 2015-10-15
Hello,

Just as a background note, I am new to Ubuntu.  I am currently running Ubuntu Mate 15.04 amd64 on an older Dell Optiplex being used as an HTPC with Kodi.  I am using a TP-Link TL-WN722N USB WiFi adapter.  My wireless network consists of two Linksys WRT54G routers running DD-WRT in WDS mode, with WPA2 Personal AES.  Everything connects and works fine, but the DD-WRT routers are old and frequently have problems.  To correct the issues, I set them to automatically reboot every morning at different times, which works great.

My problem is that when the "gateway" router reboots, Ubuntu loses the WiFi connection, and it appears that that it loses connection with the adapter itself.  I can attempt to reconnect manually (which fails every time) and I noticed that the green light on the adapter turns off.  It seems as though once the signal is down, the adapter just shuts itself off.  The only way I have found to correct this is to reboot the computer.

Being that I know very little about Linux in general, I have no idea where to start to fix this.  I was thinking of setting up some sort of watchdog to restart the adapter when the signal is lost, but I have no idea where to begin, or if this would even be the correct fix.

There is one other problem I am having, and I am not sure if it should be on its own thread or not.  I am trying to live-stream A&E through Chrome ([http://www.aetv.com/live-stream](http://www.aetv.com/live-stream), linked to my Direct TV account), which works awesome on my Windows 8.1 pc, but under Ubuntu it loads the page but not the stream, and it doesn't remember my login...

Any help will be greatly appreciated!!!

---

### Post by shaun20 on 2015-10-15
***UPDATE***

I had just recently switched to WPA2 AES because I read that there was problems with using WPA2 MIXED AES+TKIP.  Everything had worked fine until the units rebooted today, and the WDS failed.  So currently the WDS is now on WEP.  Still having the same disconnect issue.

---

### Post by Geoffrey_Arndt on 2015-10-15
One thing you can do as temp workaround is to unplug & then replug the usb adapter.    I have the same exact TP Link model, and my uptime is about 99.995% so I've seldom had to do this, but it did auto reactivate the device.

Edit:  sounds like one or both of the network devices ready for replacement.   Below is top rated ConsumerReports router.
[h=1]Linksys AC2600 (EA8500)[/h]

---

