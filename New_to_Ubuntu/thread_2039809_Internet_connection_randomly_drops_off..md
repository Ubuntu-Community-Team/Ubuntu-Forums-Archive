---
title: "Internet connection randomly drops off."
date: 2012-08-09
forum: New to Ubuntu
---

### Post by asmith2306 on 2012-08-09
Hi all,

first post on this forum, first of many I presume!  I'm brand new to Linux and am using wubi to trial out Ubuntu.  As the title bar says, my internet connection keeps dropping off at random.  It's so frustrating.  Its not Firefox because I installed Chromium as well and that was the same.  Its not my router either because I am watching youtube on my Vita which isn't dropping when it happens.

The connection seems to me a bit slow anyway but it drops and times out randomly even though the wireless is on.  I also have an IP address I can see using ifconfig when the connection drops.  I kept having to go back onto windows to look for help but help in the Linux world seems so specific to each individual case.

I have deleted the wireless connection and manually added it and so far (20mins) it hasn't dropped.  I'm on ubuntu right now :D  is there anything I can do / check if it keeps happening?

Thanks,
Alan

---

### Post by acimi66 on 2012-08-09
This may be more info than you need but it may help, when asking for help.

[http://www.cyberciti.biz/faq/check-network-connection-linux/](http://www.cyberciti.biz/faq/check-network-connection-linux/)

Good luck

---

### Post by wildmanne39 on 2012-08-09
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by asmith2306 on 2012-08-13
> **wildmanne39 said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

Hi, I did what you asked, the file is attached.  I had to compress it as it was too big to upload.

---

### Post by asmith2306 on 2012-08-13
> **acimi66 said:**
> This may be more info than you need but it may help, when asking for help.

[http://www.cyberciti.biz/faq/check-network-connection-linux/](http://www.cyberciti.biz/faq/check-network-connection-linux/)

Good luck

Thanks, will be useful for troubleshooting.

---

### Post by wildmanne39 on 2012-08-13
Hi, change your wireless settings in network manager to match the screenshots, then do:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```

A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```

Proofread, save and close gedit.

Also go into your router settings and change 802.11bgn to 802.11bg.
Reboot
Thanks

---

### Post by asmith2306 on 2012-08-14
> **wildmanne39 said:**
> Hi, change your wireless settings in network manager to match the screenshots, then do:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```Proofread, save and close gedit.

Also go into your router settings and change 802.11bgn to 802.11bg.
Reboot
Thanks

Thanks, I will try that.

ps. my wireless card is 'Realtek RTL8188CE Wireless LAN 802.11n PCI-E NIC', I see you put the option in the conf file as rtl8192ce.  Don't know if that is important or not.

Cheers,
Alan

---

### Post by wildmanne39 on 2012-08-14
Hi, this is the driver that is loaded for your wireless card rtl8192ce.
Thanks

---

### Post by asmith2306 on 2012-08-14
> **wildmanne39 said:**
> Hi, this is the driver that is loaded for your wireless card rtl8192ce.
Thanks

I see.  I have been on FireFox all day with no timeouts so i guess its working now.  Thanks very much, your a hero!

Cheers,
Alan

---

### Post by wildmanne39 on 2012-08-14
Your welcome!
Enjoy

---

### Post by bparaj on 2012-08-22
@ Wild Man:

I tried doing as you described [here]("http://ubuntuforums.org/showpost.php?p=12170200&postcount=6"). But the problem of frequent disconnects still persists. The router I have is Linksys E1200. Thanks.

---

### Post by tbc on 2013-04-07
@bparaj try disabling IPv6. See [Wireless connection is lost periodically and without apparent reason and is quickly reestablished on a BCM4312]("http://askubuntu.com/questions/128024/wireless-connection-is-lost-periodically-and-without-apparent-reason-and-is-quic") (askubuntu.com).

---

### Post by ymahmood on 2013-05-25
Hi Every body. 

I am having the same problem with 12.04. can anybody help me? My wifi connection continuously disconnects.

---

### Post by premispezia on 2013-12-12
Hi Wild M.,

with wifi usb-adap- tplink wn822n I had same problems,

I did  what you suggest on step6 

now working like it´s supposed ,

thanks

---

### Post by scholzilla on 2014-01-02
I have the same issue but with the rtl8187 chipset. Will the same solution work for me? Thanks.

---

### Post by wildmanne39 on 2014-01-03
Hi scholzilla, no this will not work for your wifi issue because you are using a different driver.

Please start your own thread so you can get the help you need.
Thanks

---

### Post by SideShowFry on 2014-12-04
Thanks Wild Man!

I had major problems with my built-in rtl8188ce. Tried various switches in modprobe.d/rtl8192ce.conf, tried using FreedomBen driver, gave up and started using a usb rtl8187 instead.  It wasn't great, either, so, after a couple/few months, I started googling around again. That's when I came across another Wild Man response in another forum: [http://askubuntu.com/questions/482564/realtek-rtl8188ce-desconects-randomly-and-features-slow-connections](http://askubuntu.com/questions/482564/realtek-rtl8188ce-desconects-randomly-and-features-slow-connections)

I didn't immediately act on anything in it. Then, fate intervened.  My router was reset to defaults somehow.  When I reconfigured it, I tried to set it up the same as it was, to the best of my recollection, except for 3 things:

AES instead of TKIP
Broadcast the ESSID (previously hidden)
Channel 1 (not really sure if this was a change)

Both the 8188 and the 8187 have been stable in the few days since.  My gut says that AES was the difference maker. 

FWIW, I'm using whatever the current standard driver is on 14.04, and with these options:


options rtl8192ce swenc=1
options rtl8192ce ips=0
options rtl8192ce fwlps=0
options rtl8192ce swlps=1

---

