---
title: "Sony Vaio SVE15113ENB brightness slider issue -Ubuntu 14.04 LTS"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by deepupn on 2014-07-30
Hi,

I am using a Sony Vaio SVE15113EN laptop. Recently I installed Ubuntu 14.04 and found out that I am unable to adjust my display brightness slider. The brightness is so high that I am unable to use the laptop while using Ubuntu. I request the experts here to guide me to resolve this issue. Thanking you all in advance for your time and replies.

---

### Post by Toz on 2014-07-31
Hi. Lets start with getting some basic information. Can you open a terminal window (sorry, but its just the simplest way to get this information), enter the following commands and post back the results within **[noparse]```
 
```[/noparse]** tags:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card(s) and drivers:
```
lspci -k | grep -iA2 VGA
```

3. You current backlight interfaces and their values:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

4. A listing of your loaded kernel modules:
```
lsmod
```

5. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and paste back the link thats generated.

---

### Post by deepupn on 2014-08-01
Hi Toz,

Thank you so much for your reply. I wasn't getting any reply from any other source so I searched online and found this link "http://ubuntuguide.net/add-brightness-control-to-unity-panel" and somehow the brightness issue is resolved for now. Could you kindly tell me if this is a permanent solution? or whether we should go forward and try the commands that told me to do? Kindly reply. 

Once again , Thank you.

---

