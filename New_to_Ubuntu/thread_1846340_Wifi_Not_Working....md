---
title: "Wifi Not Working..."
date: 2011-09-18
forum: New to Ubuntu
---

### Post by Decrypt 360 on 2011-09-18
my wifi is not working properly, i have a Broadcom 43xx driver
when i go to the hardware drivers i get 2 (proprietary) drivers and both not active ive try'd the Broadcom STA and dose not work as for the Broadcom 43 i get signal everything except it wont connect to any network
help please1....

---

### Post by Lisiano on 2011-09-18
Please define "do not work". You mean you don't even see it under Network Manager or somehow else?
Also please open a terminal (Ctrl+Alt+T) and type ```
iwconfig
``` before connecting and while connecting. Then post it here.
To copy that, select the text and Right-Click -> Copy or Ctrl+Shift+C then paste it here using the CODE tag ```
[ CODE ] Text from iwconfig Here [ /CODE ]
``` No spaces between the brackets ([ and ]) and the word CODE.

---

### Post by philipballew on 2011-09-18
paste the ouyput of lspci here. also what type of computer do you have?

---

### Post by philipballew on 2011-09-18
maybe this works [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by Decrypt 360 on 2011-09-18
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by Decrypt 360 on 2011-09-18
[ CODE ]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
[ CODE]

---

### Post by Decrypt 360 on 2011-09-18
see its weir it detetcts networks but when i try to connect it wont.....
i know its a Broadcom 4312 im trying to use the br43 driver but that problem consists

---

### Post by Lisiano on 2011-09-18
I see that is before connecting. What about while you are connecting? Just click on the Network Manager icon and your WiFi network, then run the command while the icon looks like it is connecting. Also check out what philipballew found [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)
```
sudo apt-get install firmware-b43-lpphy-installer
```
It will ask for your password (The password will not be shown while you type it, even ****), wait a bit, press Y and Enter.

---

### Post by wildmanne39 on 2011-09-18
Hi, if you still have trouble post the results of these commands please:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

Those commands are important if you still have problems because not all 4312 use the same firmware.
Thank you

---

### Post by anewguy on 2011-09-18
+1 for what wildmanne39 is saying.  I would suspect the reason it "sort of" works but doesn't completely work is driver related, and that includes the firmware.  In the end run, the firmware cutter and/or the "all" firmware package (wildmanne39 knows what I'm saying here, and I'm going let you work with him on it so it doesn't get confusing trying to follow multiple suggestions).

Don't worry - it will work, it will just take a little bit of effort.

Dave ;)

---

