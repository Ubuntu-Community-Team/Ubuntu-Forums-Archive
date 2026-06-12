---
title: "Wireless problems with Samsung netbook"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by Joseph_Diaco on 2014-01-27
Hi,

I'm new to the forum. I just installed Ubuntu 12.04 LTS on my girlfriend's Samsung NF210 netbook (came with Windows 7). Everything seems to be running great, but I can't connect to my wireless internet. I assume the problem is with the WIFI card driver, but I wasn't able to find any helpful advice through my Googling research. The annoying thing is that the wireless worked fine when I "tried Ubuntu" off the bootable USB stick I used to install it, but now that the OS is permanently installed I'm having this problem. Any advice?

---

### Post by chili555 on 2014-01-27
Welcome to the forum! The first step is to identify your wireless device. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
```That funny pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Joseph_Diaco on 2014-01-27
My problem has changed: I managed to get the OS recognizing the wifi key. Now I'm just having trouble actually connecting to my network. I enter the authentication key and it just loads forever and then sometimes the authentication screen re-appears. It doesn't connect to the network. This might be a simple fix, any thoughts?

---

### Post by chili555 on 2014-01-27
> any thoughts? Yes. Please identify your wireless device as above.

---

### Post by Joseph_Diaco on 2014-01-27
This was the response: 
Broadcom Corporation BCM4313 802.11b/g/n wire LAN Controller 14e4:4727

---

### Post by chili555 on 2014-01-27
Ahhhh! A very tricky device to get going correctly! Lucky you!!

Let's see which driver you are running:```
lsmod | grep -e wl -e brcm 
```

---

### Post by Joseph_Diaco on 2014-01-27
The response:

brcmsmac              534541  0 
mac80211              541819  1 brcmsmac
brcmutil               14355  1 brcmsmac
cfg80211              453853  2 brcmsmac,mac80211
cordic                 12518  1 brcmsmac
bcma                   39810  1 brcmsmac

---

### Post by chili555 on 2014-01-27
I believe that is correct for your device, although I get surprised sometimes. Let's see if there are informative messages in the log:```
cat /var/log/syslog | grep -e etwork -e brcm | tail -n20
```Ideally run with no ethernet cable and as you are trying to connect.

---

### Post by Joseph_Diaco on 2014-01-27
It worked! Thank you so much! All the great things I've heard about Ubuntuforums are true after all ;)

---

### Post by chili555 on 2014-01-27
Glad to hear it's working. Post back if we can help you again.

---

### Post by Kirby_Acumann on 2014-06-05
Thank you so much! I had the same problem today with my ubuntu 14.04 lts and after i read this forum it already solved my problem! Thanks a lot! :)

---

