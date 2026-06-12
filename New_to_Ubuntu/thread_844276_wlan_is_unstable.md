---
title: "wlan is unstable"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by cje on 2008-06-29
I have a netgear (WG111) usb wlan adapter. 
My wlan router is dhcp server, using hidden ssid, 128 wep. 

First, the internet connection is working

But, 
1. when I start the computer I need to use the network manager to unlock the wlan connection. why?
2. after every re-boot the system doesn't find the the wlan adapter. To solve this I need to unplug it and plug it in again. Why?
3. Finally, after surfing internet for some minutes the wlan adapter shuts down and disappear from the network manager window. Again I need to unplug and plug it in again. Why?

Thanks for any comments and/or suggestions.

---

### Post by cje on 2008-06-30
update; I found that wlan is "turned off" when I load/view heavy internet pages.

---

### Post by unutbu on 2008-06-30
Sorry I don't have a true fix for you, but next time your connection is broken, would you please try running the command
```

sudo /etc/init.d/networking restart
```

Let's see if that gets your connection back without you having to unplug/replug.

---

### Post by cje on 2008-06-30
unfortunately it didn't help .... I still need to unplug and plug the usb wlan device to get internet access :-(

I get some error messages, as;
"wlan0: ERROR while getting interface flags: No such device"
"Failed to read or parse configuration 'etc/wpa_supplicant.conf'."
"wpa_supplicant: /sbin/wpa_supplicant daemon failed to start"
"no DHCPOFFERS received."
"no working leases in persistent database - sleeping."

---

### Post by unutbu on 2008-06-30
> "wlan0: ERROR while getting interface flags: No such device"
"Failed to read or parse configuration **'etc/wpa_supplicant.conf'**."
"wpa_supplicant: /sbin/wpa_supplicant daemon failed to start"
"no DHCPOFFERS received."
"no working leases in persistent database - sleeping."


The bold line should have had a forward-slash in front of the "etc". In other words, it should have read 
```
'/etc/wpa_supplicant.conf'
```
Was this a typo on your part, or is this really what the output said? 

If this is what the output said, it sounds like there is some configuration file associated with wpa_supplicant that is referencing etc/wpa_supplicant.conf instead of /etc/wpa_supplicant.conf.

Whatever the case, please post the output of 

```
cat /etc/wpa_supplicant.conf
```

If that command returns

```
cat: /etc/wpa_supplicant.conf: No such file or directory
```

Then it means you haven't fully configured wpasupplicant. If that's your situation, go to 
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
for a good guide on setting  up WPA.

---

### Post by cje on 2008-06-30
thanks for your quick feedback, but
yes, the missing forward slash in "failed to read or ...." was just a typo ...
and,
"....No such file or directory" was not a part of the error message

---

### Post by unutbu on 2008-06-30
Okay then. Still, it is strange that `sudo /etc/init.d/networking restart` would complain that it (or /sbin/wpa_supplicant) "[f]ailed to read or parse configuration '/etc/wpa_supplicant.conf'."

Please post
```

ls -l /etc/wpa_supplicant.conf  
cat /etc/wpa_supplicant.conf
```
I doubt there can be permission problems since `sudo /etc/init.d/networking restart` is run as root, but it can't hurt to check...

XXX out any private passwords of course.

---

