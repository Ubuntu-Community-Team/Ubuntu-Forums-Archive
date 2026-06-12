---
title: "Ubuntu 15.10 won't recognize iphone 4S"
date: 2016-04-10
forum: New to Ubuntu
---

### Post by scott60 on 2016-04-10
Hello,

I recently installed Xubuntu 15.10 on a netbook (ASUS Eee 1011px) and am having difficulty getting my machine to recognize my iPhone (iOS 9.1) I compiled and installed libimobiledevice using the guide here [http://askubuntu.com/questions/78535/how-to-install-libimobiledevice](http://askubuntu.com/questions/78535/how-to-install-libimobiledevice), but this doesn't seem to have helped. Other troubleshooting methods that I've searched for seem to be intended for older versions of Ubuntu, so I'm wondering if 15.10 doesn't support such an old device. I'm not at all linux savvy, so you'll forgive me for having overlooked any seemingly obvious remedies. Any help is appreciated.

Thanks in advance

---

### Post by tripp98 on 2016-04-10
unplug iphone.
open terminal 
type tail -f /var/log/syslog
this will show you what is going on when you plug the iphone in.
plug in iphone.  
see what it says.

also make sure on the phone you allow the computer.

---

### Post by scott60 on 2016-04-10
```
Apr 11 01:19:07 esco-1011PX kernel: [  255.243110] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243119] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243127] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243133] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243141] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243149] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243156] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243162] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Apr 11 01:19:07 esco-1011PX kernel: [  255.243169] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Apr 11 01:19:07 esco-1011PX wpa_supplicant[665]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Apr 11 01:19:53 esco-1011PX kernel: [  301.008302] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by 78:31:2b:db:d7:a4
Apr 11 01:20:17 esco-1011PX anacron[576]: Job `cron.daily' started
Apr 11 01:20:18 esco-1011PX anacron[1654]: Updated timestamp for job `cron.daily' to 2016-04-11
Apr 11 01:20:44 esco-1011PX wpa_supplicant[665]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN


```

---

### Post by tripp98 on 2016-04-10
looks like it doesnt see the usb connection to the iphone.  
leave the terminal window up and try a different usb port with the iphone.

---

### Post by scott60 on 2016-04-10
```
Apr 11 01:25:58 esco-1011PX kernel: [  665.523117] perf interrupt took too long (5018 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
^[Apr 11 01:20:44 esco-1011PX wpa_supplicant[665]: wlp2s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
Apr 11 01:28:47 esco-1011PX kernel: [  835.331105] Bluetooth: Core ver 2.20
Apr 11 01:28:47 esco-1011PX kernel: [  835.331182] NET: Registered protocol family 31
Apr 11 01:28:47 esco-1011PX kernel: [  835.331190] Bluetooth: HCI device and connection manager initialized
Apr 11 01:28:47 esco-1011PX kernel: [  835.331205] Bluetooth: HCI socket layer initialized
Apr 11 01:28:47 esco-1011PX kernel: [  835.331215] Bluetooth: L2CAP socket layer initialized
Apr 11 01:28:47 esco-1011PX kernel: [  835.331238] Bluetooth: SCO socket layer initialized
Apr 11 01:29:53 esco-1011PX systemd[1]: Starting Cleanup of Temporary Directories...
Apr 11 01:29:53 esco-1011PX systemd-tmpfiles[1777]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Apr 11 01:29:54 esco-1011PX systemd[1]: Started Cleanup of Temporary Directories.
^TApr 11 01:39:14 esco-1011PX systemd[1]: Stopping CUPS Scheduler...
Apr 11 01:39:15 esco-1011PX systemd[1]: Stopped CUPS Scheduler.
Apr 11 01:39:15 esco-1011PX systemd[1]: Started CUPS Scheduler.

```

All of the above seems unrelated
I think the problem may be that I'm using a 5&#8364; off-brand cable instead of the official Apple brand. It just occurred to me that I had the same problem when trying to connect to iTunes in Windows :redface: Sorry for the trouble! Thanks for your help

---

