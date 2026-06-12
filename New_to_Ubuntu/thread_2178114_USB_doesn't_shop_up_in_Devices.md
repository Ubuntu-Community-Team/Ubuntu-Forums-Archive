---
title: "USB doesn't shop up in Devices"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by hodgesse on 2013-10-01
Hello:

I have a USB drive that works with an iButton device.  It works fine on Windows.  However, I would like to use it on Ubuntu.  I downloaded the correct software.  But the drive doesn't show up in the devices.

Here is the output from lsusb:

rin@erin-Lenovo-IdeaPad-Y480:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04fa:2490 Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter
Bus 001 Device 004: ID 0489:e042 Foxconn / Hon Hai 
Bus 002 Device 003: ID 13d3:5162 IMC Networks 
erin@erin-Lenovo-IdeaPad-Y480:~$ 


And here are the last 10 lines from dmesg:

 dmesg | tail
[   18.388692] cfg80211: Calling CRDA for country: US
[   18.391026] cfg80211: Regulatory domain changed to country: US
[   18.391028] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.391029] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   18.391030] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   18.391031] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.391032] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.391033] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.391034] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   20.681266] init: plymouth-stop pre-start process (1653) terminated with status 1
erin@erin-Lenovo-IdeaPad-Y480:~$ 


Has anyone run into this before please?

Thanks,
Erin

---

### Post by Cbjaxx on 2013-10-02
I am not sure if this link will help but but I found it in the archive... Seems related to the device/issue you are having...[http://ubuntuforums.org/archive/index.php/t-1672823.html]("http://ubuntuforums.org/archive/index.php/t-1672823.html")

Best of Luck

---

