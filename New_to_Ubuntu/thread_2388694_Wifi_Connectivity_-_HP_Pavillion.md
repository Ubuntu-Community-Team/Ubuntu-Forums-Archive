---
title: "Wifi Connectivity - HP Pavillion"
date: 2018-04-06
forum: New to Ubuntu
---

### Post by mark425 on 2018-04-06
I experience several problems (in particular the connection is very slow) with my wifi connection on Ubuntu, but on Windows everything works fine 

Here is the script with info: 

[https://pastebin.com/vCaKGygs](https://pastebin.com/vCaKGygs)

---

### Post by kerry_s on 2018-04-06
i got the hp-pavilion-g6

i think in ubuntu 16 you need to disable/ignore the ipv6 in wifi settings.
[ATTACH=CONFIG]279188[/ATTACH]

newer ubuntu wifi is much better, than it was in 16.

---

### Post by praseodym on 2018-04-06
Lets try
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
sudo iwconfig wlo1 power off
```
Change the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2. Which country do you live?

---

### Post by mark425 on 2018-04-06
@[**[COLOR=#000000]praseodym[/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497")
The problem is that I experience problems in all wifi-connections. Also in eduroam for instance

---

### Post by praseodym on 2018-04-06
Tried those commands/settings?

---

### Post by Geoffrey_Arndt on 2018-04-07
As a backup, a second network adaptor is never a bad idea . . if after providing requested info, solution still not successful, perhaps the following devices will work better:

[http://www.pandawireless.com/](http://www.pandawireless.com/)

---

