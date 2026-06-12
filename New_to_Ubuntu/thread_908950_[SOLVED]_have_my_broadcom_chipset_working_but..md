---
title: "[SOLVED] have my broadcom chipset working but."
date: 2008-09-03
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-03
my wireless network in snot showing im trying ubuntu studio and have my broadcom wireless running with build essentials and fwcutter. i just need a walkthrough to be able to find the available wireless networks

---

### Post by falcon61102 on 2008-09-03
The wireless access points should automatically become visible once your wireless card is working.  It sounds like drivers may not have loaded correctly.

If any, what walk through did you use to install the drivers?
Did you have any problems with the walk through?
What previous attempts, if any, did you attempt but were unsuccessful?

Also, could you post the results of:
```
sudo lshw -C network
```
-l is a lower case L

---

### Post by PatrickMoore on 2008-09-03
> **falcon61102 said:**
> The wireless access points should automatically become visible once your wireless card is working.  It sounds like drivers may not have loaded correctly.

If any, what walk through did you use to install the drivers?
Did you have any problems with the walk through?
What previous attempts, if any, did you attempt but were unsuccessful?

Also, could you post the results of:
```
sudo lshw -C network
```
-l is a lower case L

i used the same tactics that worked when i originally loaded hardy back in april. i installed build essentials via live cd then downloaded  the broadcom drivers and fwcutter from the appropriate sites and loaded them via terminal and a flash drive worked with xubuntu and ubuntu 8.04. it states that my chipset is enabled and in use. i just dont have nm applet which is what im used to. my guess is that if i can get a network manager to work i will be able to log on. its showing a "lo" network that is idle. if that helps.

---

### Post by falcon61102 on 2008-09-03
Have you tried adding the Network Monitor app back to your panel?

Right Click on a clear space on one of you panels, then click Add to Panel.  Scroll through the list and you should see Network Monitor.  Is that what you were looking for?

And I don't believe "lo" is the network that you want to be using.  I think it should be "wlan".

---

### Post by oilchangeguy on 2008-09-03
> **falcon61102 said:**
> Have you tried adding the Network Monitor app back to your panel?

Right Click on a clear space on one of you panels, then click Add to Panel.  Scroll through the list and you should see Network Monitor.  Is that what you were looking for?

And I don't believe "lo" is the network that you want to be using.  I think it should be "wlan".

you are correct. the wireless network is wlan0.

---

### Post by PatrickMoore on 2008-09-03
> **falcon61102 said:**
> Have you tried adding the Network Monitor app back to your panel?

Right Click on a clear space on one of you panels, then click Add to Panel.  Scroll through the list and you should see Network Monitor.  Is that what you were looking for?

And I don't believe "lo" is the network that you want to be using.  I think it should be "wlan".

network monitor is doing nothing for me. basically i cant get that to work. i need to use wlan0 but the issue is that with network monitor it wants me to manually enter my ip address however i dont have all the info i need. plus i remomber that from when i had 8.04 originally i could never get that to work. any programs i can load onto a jump drive and install that you would reccomend. everything regarding the wirelss driver looks good if you need me to post anything that can of course be arranged

---

### Post by knattlhuber on 2008-09-03
What does

```
iwconfig
```

give you?

Have you tried [Wicd]("http://wicd.sourceforge.net/")?
You can download the Debian package here: [https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573")

---

### Post by RequinB4 on 2008-09-03
There's always not using fwcutter...

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by PatrickMoore on 2008-09-03
> **knattlhuber said:**
> What does

```
iwconfig
```

give you?

Have you tried [Wicd]("http://wicd.sourceforge.net/")?
You can download the Debian package here: [https://sourceforge.net/project/showfiles.php?group_id=194573]("https://sourceforge.net/project/showfiles.php?group_id=194573")


```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ill check it out

---

### Post by PatrickMoore on 2008-09-04
wicd works well... but i keep on getting this error message...

 "the network reuires encryption to be enabled"

---

### Post by anewguy on 2008-09-04
Sounds like the router is expecting some sort of WEP or WPA.  How is your router set, and are you specifying it when you try to connect?

---

### Post by knattlhuber on 2008-09-04
Did you enter the enter the encryption settings for your network by clicking on the triangle next to the ESSID in Wicd and then choosing 'Advanced Settings'?

Another thing that you can try is going to Preferences and changing the WPA supplicant driver from default 'wext' to 'Broadcom'

---

### Post by PatrickMoore on 2008-09-04
> **knattlhuber said:**
> Did you enter the enter the encryption settings for your network by clicking on the triangle next to the ESSID in Wicd and then choosing 'Advanced Settings'?

Another thing that you can try is going to Preferences and changing the WPA supplicant driver from default 'wext' to 'Broadcom'

yes and i have it running great

---

