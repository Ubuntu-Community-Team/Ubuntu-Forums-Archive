---
title: "wlan not working"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by taku97 on 2012-11-06
Hi the wlan is not working on my Lenovo B560 running ubuntu 12.10.

Wlan card: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller

Tried to follow some solutions but do not get the same output some had no output at all and none of them did help. 

I do get a output in the terminal by writing: 
rfkill list all

0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no



By the way, it have been working for a long time but I have this physical bottom, which i'm pretty sure have something to to with it. Think I had a simular problem earlier. 
And it works fine when I boot windows 7 (dual-boot), the bottum-thing works fine there (on-off)

Hope you guys can help.

---

### Post by wildmanne39 on 2012-11-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by taku97 on 2012-11-07
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

SO I post what the file contains? I'll attach it for a start. It's pretty long:)

---

### Post by Hadaka on 2012-11-07
Hi,  try

```
sudo apt-get install bcmwl-kernel-source 
 sudo modprobe wl 
```and see if it comes to life.

---

### Post by wildmanne39 on 2012-11-07
Hi, please do:
```
echo "blacklist acer_wmi " | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Then reboot and if wireless does not come on then do:
```
sudo modprobe brcmsmac
```
Thanks

---

### Post by taku97 on 2012-11-07
Thanks a lot. But none of it seem to work. Any other suggestions?

---

### Post by Hadaka on 2012-11-07
Hi take a read of this thread..especially post #8
[http://ubuntuforums.org/showthread.php?t=2081537](http://ubuntuforums.org/showthread.php?t=2081537)
Wireless LAN Controller [14e4:4727]
same card as you ..

---

### Post by taku97 on 2012-11-07
> **Hadaka said:**
> Hi take a read of this thread..especially post #8
[http://ubuntuforums.org/showthread.php?t=2081537](http://ubuntuforums.org/showthread.php?t=2081537)
Wireless LAN Controller [14e4:4727]
same card as you ..

That solved it... worked like magic. Thanks a lot:D

how do I mark it as solved?

---

### Post by NikTh on 2012-11-07
> **taku97 said:**
> 

how do I mark it as solved?

See here => [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

:)

---

### Post by Hadaka on 2012-11-07
Hi, glad that worked for you, you "might" want to drop the wl
driver into your etc/modules...this will make sure it loads on boot..

```
echo 'wl' >> /etc/modules 
```

---

### Post by taku97 on 2012-11-08
Thanks, I'll do that.

---

