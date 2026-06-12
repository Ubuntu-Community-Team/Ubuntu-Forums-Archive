---
title: "hcitool and BlueCove bluetooth detection of Android device"
date: 2015-10-10
forum: Programming Talk
---

### Post by gmseed on 2015-10-10
Initially I thought the problem I've been having was restricted to my Raspberry Pi unit but I can replicate it on Ubuntu 14.04 also and was wondering if anyone knows the answer.

1) I have an Android tablet sat next to my Ubuntu laptop. The Android tablet is on and the screen is active but it is NOT in discoverable mode. When I do a device scan:

~$ hcitool scan
Scanning ...
~$ 

I get no results.

2) Now, I go into Settings|Bluetooth on the Android tablet and make the tablet discoverable for 2 minutes and run scan again:

~$ hcitool scan
Scanning ...
	20:D3:90:C7:10:D2	Graham
~$

and this time you'll see that the Android tablet [named Graham] is detected.

So, my question is why is the device only detected when in discoverable mode?

3) Repeat the above steps 1) and 2) from my Win7 laptop and the Android tablet will be detected in both cases!

4) Next, I use BlueCove and run their example DeviceDiscovery example:

[http://bluecove.org/bluecove/apidocs/overview-summary.html#DeviceDiscovery](http://bluecove.org/bluecove/apidocs/overview-summary.html#DeviceDiscovery)

On RPi and Ubuntu I get the same as using "hcitool scan" in that the Android device is only detected when in temporary discoverable mode.

Whereas, running DeviceDiscovery on Win7 the Android is detected in both cases.

To summarise:

RPi and Ubuntu give the same results.
hcitool scan and BlueCove DeviceDiscovery give the same results on Linux.
BlueCove DeviceDiscovery on Win7 detects the Android tablet irrespective of whether in discoverable mode.

There is something on Linux that is blocking an Android device from being detected unless it is in discoverable mode. But what?

Thanks
Graham

---

