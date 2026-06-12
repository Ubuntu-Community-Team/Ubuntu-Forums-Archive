---
title: "Wireless internet going slow"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by skaldicpoet9 on 2011-11-21
I just installed Ubuntu 11.04 on my Acer Aspire laptop and I am having the slowest speeds ever on my wifi. Any webpage that I go to takes at least 4-5 seconds to load. This never happened on my Windows 7 install on this same computer. I have a pretty fast connection to (24mbps down, 12mpbs up), so I know that my internet speed isn't to blame. Is there any solution to this? I've experienced wireless issues in the past with Ubuntu, so perhaps maybe it is a driver issue? Any help would be greatly appreciated, this slow rendering is killing me.

---

### Post by carverj on 2011-11-22
This wifi troubleshooting guide might be useful in figuring it out:-
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Step 4 lists commands that you can post us the output to see what is going on.

---

### Post by elecleoalune on 2011-11-22
I had the similar problem. I found many different solution and one ended up actually working. I honestly don't know which one it was, but hopefully one of these works!

```
 sudo ifconfig wlan0 down 
sudo rmmod -f ath9k 
sudo modprobe ath9k nohwcrypt=1 
sudo ifconfig wlan0 up 
```
run this. If it doesn't work when you restart then DON'T restart after you run this. This seems to be temp I believe (I could be wrong).

This was another one that I found.
```
 root@ubuntu:~# ifconfig wlan0 down root@ubuntu:~# rmmod -f ath9k root@ubuntu:~# sudo modprobe ath9k nohwcrypt=1 WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release. root@ubuntu:~# ifconfig wlan0 up root@ubuntu:~# 
```

Here's another one just to make sure

```
echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf

```Hopefully one of these work. GL

---

### Post by skaldicpoet9 on 2011-11-22
Thanks for the replies everyone. However, I just didn't have the time to keep Ubuntu installed and work through the issues. I have a bunch of homework I need to do. I didn't think that I would encounter that many issues trying get Ubuntu up and running, I haven't had many issues the last few versions wifi or otherwise. Unfortunately I have too much homework to fiddle around with things and had to revert back to Windows for the time being. I'll try again after school is finished but for now I just don't have the time.

---

