---
title: "[SOLVED] Atheros AR242 on ubuntu 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Karilex on 2008-11-02
I have recently updated to ubuntu 8.10 everything went fine except for my atheros wireless card which ubuntu still doesn't detect(actually it does detect it but the wireless just doesn't work) I had previously tried installing madwifi on ubuntu 8.04 but with being an ubuntu newb and all I failed but by searching around I have seen that I just need to enable ath5k with ubuntu 8.10 unfortunately I have no idea what that is and even less of an idea on how to enable it also if this isn't the way to make my wireless card work could you point me to some alternative instructions to get my wireless card to finally work thanks for taking the time to read this.

_____
oh and by the way I have a compaq c700(c793VU) not sure if that would help but you never know.

_____
here are some infos:


uname -a
```
Linux krauth-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux

```


lspci | grep -i net
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:a3:2b:7c  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fea3:2b7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5384 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5147983 (5.1 MB)  TX bytes:898951 (898.9 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16604 (16.6 KB)  TX bytes:16604 (16.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:03:47:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-03-47-D9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

________
Edit: Wireless works after the install it's just that the led does not turn blue and there is no alert message saying the wireless has been turned off so I guess this is solved.

---

### Post by ugm6hr on 2008-11-02
You can try this: [https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan)

It is for the AspireOne, but I believe you have the same wifi card.

No promises though - perhaps do some googling to double-check.

---

### Post by hictio on 2008-11-02
Hi there Karilex,

I have the same WiFi card, on a Compaq F700, which I think is how they called the same model over here,
I have just tested the, let's call it, "method" :D of:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

On my fresh -less than 24 hrs old install- of Intrepid. It worked perfectly.

Here are the steps:

1- Disable the "*Support for Atheros 802.11 wireless LAN cards*" on **Hardware Drivers**, and reboot your box.
2- Once it is back on, open a Terminal, and type:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

It will ask your password, this is what it prints on screen, that is, what it will do:
```

esteban@tango:~/Desktop$ sudo aptitude install linux-backports-modules-intrepid-generic
[sudo] password for esteban: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic{a} 
  linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?] 

```

When that is over (you'll get your prompt back), reboot, and enjoy the WiFi connection.
Personally, I can't still believe it, I have spent hours on Hardy with this... The WiFi card used to work, I was able to set an IP address to ip, etc, but it was impossible to connect to any type of network.

But that was Hardy, on Intrepid, after the backports installation, I had no problem connecting to my WPA2 DLink AP (after autenticating me of course).
Good luck, I hope this is useful.

This is my WiFi card, according to 'lspci':

```

esteban@tango:~/Desktop$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
esteban@tango:~/Desktop$ 

```

Other links on this:
[Instalando WiFi Atheros AR242X Ubuntu intrepid Ibex 8.10](http://elteclado.wordpress.com/2008/11/02/instalando-wifi-atheros-ar242x-ubuntu-intrepid-ibex-810/) - in Spanish
[Atheros Wireless in Ubuntu 8.10 Intrepid Ibex](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/) - Recommends installing the backports *before* disabling the Atheros 802.11 card. I haven't done that.

---

### Post by Karilex on 2008-11-03
Thanks a lot for your help but unfortunately i tried the installation the "Support for 5xxx series of Atheros 802.11 wireless LAN cards" does appear in my list of hardware drivers but my wireless still doesn't work it may be just the led and the button that don't work if it is is there some kind of command to turn my wireless on?

---

### Post by bumanie on 2008-11-03
I used ndiswrapper to get that card going. [Look here]("http://ubuntuforums.org/archive/index.php/t-766169.html").

---

### Post by hictio on 2008-11-03
> **Karilex said:**
> Thanks a lot for your help but unfortunately i tried the installation the "Support for 5xxx series of Atheros 802.11 wireless LAN cards" does appear in my list of hardware drivers but my wireless still doesn't work it may be just the led and the button that don't work if it is is there some kind of command to turn my wireless on?

Too bad it didn't work, the led is still red, it didn't change.

---

### Post by Karilex on 2008-11-03
With the ndiswrapper I install the net 5211 file and it says the hardware is present but the wireless still doesn't startafter i reboot what do i do next?

---

### Post by macogw on 2008-11-03
Get rid of ndiswrapper and disable whatever drivers are currently attempting to handle it. Install linux-backports-modules-intrepid and reboot.

---

### Post by Karilex on 2008-11-03
Should I enable the"support for 5xxx series atheros 802.11?"

---

### Post by igknighted on 2008-11-03
> **Karilex said:**
> Should I enable the"support for 5xxx series atheros 802.11?"

NO.

Install the package suggested in the post above instead.

---

### Post by Karilex on 2008-11-03
ah a bit of a development when i type iwconfig 

I get 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

and i don't get a wlan0 how do i activate it? Or maybe my situation is hopeless:confused:

---

### Post by Karilex on 2008-11-03
Sorry i forgot to post some infos:

uname -a
```
Linux krauth-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux

```


lspci | grep -i net
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:a3:2b:7c  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fea3:2b7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5384 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5147983 (5.1 MB)  TX bytes:898951 (898.9 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16604 (16.6 KB)  TX bytes:16604 (16.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:03:47:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-03-47-D9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by Karilex on 2008-11-03
The wireless seems to be working on the xfce desktop so i guess it should be my fault the led doesn't turn blue but the wireless is constantly on so i guess this is solved but if you know how i could make it work in gnome please tell me it's probably me just making a stupid mistake anyway

____
edit: I got it to work on gnome so I guess this is completely solved =) thanks for all your help

---

### Post by IndyGunFreak on 2008-11-03
> **hictio said:**
> Hi there Karilex,

I have the same WiFi card, on a Compaq F700, which I think is how they called the same model over here,
I have just tested the, let's call it, "method" :D of:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

On my fresh -less than 24 hrs old install- of Intrepid. It worked perfectly.

Here are the steps:

1- Disable the "*Support for Atheros 802.11 wireless LAN cards*" on **Hardware Drivers**, and reboot your box.
2- Once it is back on, open a Terminal, and type:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

It will ask your password, this is what it prints on screen, that is, what it will do:
```

esteban@tango:~/Desktop$ sudo aptitude install linux-backports-modules-intrepid-generic
[sudo] password for esteban: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic{a} 
  linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?] 

```

When that is over (you'll get your prompt back), reboot, and enjoy the WiFi connection.
Personally, I can't still believe it, I have spent hours on Hardy with this... The WiFi card used to work, I was able to set an IP address to ip, etc, but it was impossible to connect to any type of network.

But that was Hardy, on Intrepid, after the backports installation, I had no problem connecting to my WPA2 DLink AP (after autenticating me of course).
Good luck, I hope this is useful.

This is my WiFi card, according to 'lspci':

```

esteban@tango:~/Desktop$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
esteban@tango:~/Desktop$ 

```

Other links on this:
[Instalando WiFi Atheros AR242X Ubuntu intrepid Ibex 8.10](http://elteclado.wordpress.com/2008/11/02/instalando-wifi-atheros-ar242x-ubuntu-intrepid-ibex-810/) - in Spanish
[Atheros Wireless in Ubuntu 8.10 Intrepid Ibex](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/) - Recommends installing the backports *before* disabling the Atheros 802.11 card. I haven't done that.

This worked perfectly for me on a new install.  Acer 2315-2153

Thanks..

IGF

---

### Post by valqk on 2008-11-03
It worked for my ASUS X51Lseries.
Thanks a lot!
:guitar: ):P

---

### Post by BoyBlunder on 2008-11-04
I have tried all of these steps above, and still have no wireless connectivity.

Is it possible to remove linux-backports-modules-intrepid-generic and try to re-install or will that mess something up?

---

### Post by hictio on 2008-11-04
> **BoyBlunder said:**
> I have tried all of these steps above, and still have no wireless connectivity.

Is it possible to remove linux-backports-modules-intrepid-generic and try to re-install or will that mess something up?

I really wouldn't tell why it didn't work... The only thing I can think of:
- Are you running a 64 bits Ubuntu?
- How did you installed Intrepid, did you upgrade from Hardy, or made a fresh install?

You mean reinstall what? The whole OS to have a "fresh start"?

---

### Post by BoyBlunder on 2008-11-04
> **hictio said:**
> I really wouldn't tell why it didn't work... The only thing I can think of:
- Are you running a 64 bits Ubuntu?
- How did you installed Intrepid, did you upgrade from Hardy, or made a fresh install?

You mean reinstall what? The whole OS to have a "fresh start"?

No 64-bit. I installed Intrepid from a USB key, fresh install.

When I mean "reinstall", I mean just the package linux-backports-modules-intrepid-generic (apt-get remove/install).

---

### Post by hictio on 2008-11-04
Yeah, you might de-install the package, haven't done it myself, but it shouldn't do any harm.
But then again, have you checked the logs for any error or hint?
Do you get any error message when you try to connect?
Does the WiFi card "show up" at all?
Can you see any AP on the drop down list?

---

### Post by BoyBlunder on 2008-11-04
> **hictio said:**
> Yeah, you might de-install the package, haven't done it myself, but it shouldn't do any harm.
But then again, have you checked the logs for any error or hint?
Do you get any error message when you try to connect?
Does the WiFi card "show up" at all?
Can you see any AP on the drop down list?

I'm going to try re-installing the package right now.

I can see the WiFi card, just no APs. Where are the logs located?

---

### Post by BoyBlunder on 2008-11-04
> **BoyBlunder said:**
> I'm going to try re-installing the package right now.

I can see the WiFi card, just no APs. Where are the logs located?

removed the package, but still no dice.

I removed > rebooted > reinstalled > rebooted.

I think if I can't get this working tonight, I'll be reinstalling Windows tomorrow. I'm just so frustrated when it comes to this.

---

### Post by hictio on 2008-11-04
The logs are located on the directory: '/var/log/' on your filesystem.
You should check 'messages', 'syslog', 'debug'.

---

### Post by IndyGunFreak on 2008-11-05
> **hictio said:**
> Hi there Karilex,

I have the same WiFi card, on a Compaq F700, which I think is how they called the same model over here,
I have just tested the, let's call it, "method" :D of:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

On my fresh -less than 24 hrs old install- of Intrepid. It worked perfectly.

Here are the steps:

1- Disable the "*Support for Atheros 802.11 wireless LAN cards*" on **Hardware Drivers**, and reboot your box.
2- Once it is back on, open a Terminal, and type:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

It will ask your password, this is what it prints on screen, that is, what it will do:
```

esteban@tango:~/Desktop$ sudo aptitude install linux-backports-modules-intrepid-generic
[sudo] password for esteban: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic{a} 
  linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?] 

```

When that is over (you'll get your prompt back), reboot, and enjoy the WiFi connection.
Personally, I can't still believe it, I have spent hours on Hardy with this... The WiFi card used to work, I was able to set an IP address to ip, etc, but it was impossible to connect to any type of network.

But that was Hardy, on Intrepid, after the backports installation, I had no problem connecting to my WPA2 DLink AP (after autenticating me of course).
Good luck, I hope this is useful.

This is my WiFi card, according to 'lspci':

```

esteban@tango:~/Desktop$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
esteban@tango:~/Desktop$ 

```

Other links on this:
[Instalando WiFi Atheros AR242X Ubuntu intrepid Ibex 8.10](http://elteclado.wordpress.com/2008/11/02/instalando-wifi-atheros-ar242x-ubuntu-intrepid-ibex-810/) - in Spanish
[Atheros Wireless in Ubuntu 8.10 Intrepid Ibex](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/) - Recommends installing the backports *before* disabling the Atheros 802.11 card. I haven't done that.

In addition to my Acer 5315-2153, this also worked on my Asus eee 900

IGF

---

### Post by bonesdds on 2008-11-05
This worked on my acer aspire 5610z with atheros ar2413.  Thank you so much.

Jonah

---

### Post by hictio on 2008-11-06
A little update on this.
Just made an install of all of this updates, and the Atheros on my Compaq F700 is still working like a champ.

```

2008-11-07 00:52:12 upgrade linux-image-2.6.27-7-generic 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:31 upgrade gdm-guest-session 0.6 0.6.1
2008-11-07 00:52:32 upgrade human-theme 0.28.5 0.28.6
2008-11-07 00:52:32 upgrade libgphoto2-port0 2.4.2-0ubuntu2 2.4.2-0ubuntu3
2008-11-07 00:52:32 upgrade libgphoto2-2 2.4.2-0ubuntu2 2.4.2-0ubuntu3
2008-11-07 00:52:33 upgrade libtotem-plparser12 2.24.1-0ubuntu2 2.24.2-0ubuntu1
2008-11-07 00:52:33 upgrade linux-headers-2.6.27-7 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:41 upgrade linux-headers-2.6.27-7-generic 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:47 upgrade linux-libc-dev 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:48 upgrade python-software-properties 0.68 0.68.1
2008-11-07 00:52:49 upgrade software-properties-gtk 0.68 0.68.1
2008-11-07 00:52:50 upgrade system-tools-backends 2.6.0-1ubuntu1 2.6.0-1ubuntu1.1
2008-11-07 00:52:51 upgrade totem-common 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:07 upgrade totem-plugins 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:07 upgrade totem-gstreamer 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:08 upgrade totem 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:08 upgrade totem-mozilla 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:09 upgrade transmission-gtk 1.34-0ubuntu2 1.34-0ubuntu2.1
2008-11-07 00:53:09 upgrade transmission-common 1.34-0ubuntu2 1.34-0ubuntu2.1
2008-11-07 01:09:20 upgrade command-not-found-data 0.2.26ubuntu1 0.2.26ubuntu1.1
2008-11-07 01:09:20 upgrade command-not-found 0.2.26ubuntu1 0.2.26ubuntu1.1
2008-11-07 01:09:21 upgrade libdecoration0 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:21 upgrade compiz-gnome 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:32 upgrade compiz-plugins 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:32 upgrade compiz-wrapper 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:32 upgrade compiz-core 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:33 upgrade compiz 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:33 upgrade nvidia-96-modaliases 96.43.05-0ubuntu10 96.43.09-0ubuntu1
2008-11-07 01:09:33 upgrade rhythmbox 0.11.6svn20081008-0ubuntu4 0.11.6svn20081008-0ubuntu4.1

```

---

### Post by Karilex on 2008-11-07
Mine too but as I have recently discovered the led stays red Oo and each time i restart my computer i have to disable and enable the restricted software for it to work how bizzare :lolflag: anywho happy it works thanks for the help guys

---

### Post by hictio on 2008-11-07
> **Karilex said:**
> Mine too but as I have recently discovered the led stays red Oo

Yes, the LED on my Compaq F700 has been on the red all the time (even before the install of the package and that it started to working).

> **Karilex said:**
> 
each time i restart my computer i have to disable and enable the restricted software for it to work how bizzare :lolflag: anywho happy it works thanks for the help guys

Mhhhmmm... I don't have to do this, not even before installing yesterday's updates.

---

### Post by Karilex on 2008-11-07
Well guess it means I'm alone on this but I'm pretty sure it will be solved on ubuntu 9.04 or 9.10

---

### Post by IndyGunFreak on 2008-11-08
> **Karilex said:**
> Mine too but as I have recently discovered the led stays red Oo and each time i restart my computer i have to disable and enable the restricted software for it to work how bizzare :lolflag: anywho happy it works thanks for the help guys

As for the light, mine isn't even on.. :)  I'm not overly concerned w/ the light, as my wireless works flawlessly.

Thats strange on enabling/disabling the driver.. I've not had to do that on either of my laptops, and my friend hasn't done it on his either..

---

### Post by zenithdave on 2008-11-08
Hey this was a great fix thanks :popcorn:

Fresh install 8:10 on eee 900. Installed the backport stuff above and i had a load more options to use,  i could actually see the wireless.

Im curious, when asked for my passkey which is a random collection of characters they were converted to ASCII string and wouldn't connect so i entered this data into the router and all was well. Now i assumed i would have to go and change the girlfriend's laptop passkey but it was up and running no problems!!:confused:

So did it convert my usual passkey to ascii but still accept the ordinary one on the other laptop?

Thanks again for the great fix, so good to have wireless wrking again :D:KS

---

### Post by debernardis on 2008-11-09
I have my intrepid on an usb stick and use it on several machines. 
On one (Compaq nc4200) I have an "Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)" (lspci output) - this works out of the box.
But on the laptop at work (a Fujitsu Siemens Lifebook something, it's not here to get the exact model), there is the Atheros AR242. Installing the linux-backports-modules-intrepid-generic package solved the problem...

[CENTER]...but...[/CENTER]

...when back home, the Intel network card isn't recognized and to make it work I have to remove the above package.

Looking at the lsmodem output with and without the backport modules package, I can see that when the package is not loaded, my laptop loads the ipw2200 module and several related modules (ieee80211, ieee80211_crypt, ieee80211_crypt_tkip) - while when the backports modules package is loaded, I get instead of them lbm_cw_ieee80211 and lbm_cw_ieee80211_crypt.

So, thinking I was smart, I rmmodded the latter two modules and modprob'd the ieee80211_something modules (which were loaded) and finally the ipw2200 module... but there's no ipw2200 module at all when the backport modules package is loaded!

So I resorted to toggling the package and rebooting. But it's inelegant.

Any hint? :D Might be related to [http://ubuntuforums.org/showthread.php?t=971872](http://ubuntuforums.org/showthread.php?t=971872) ?

---

### Post by ilbuonme on 2008-11-10
> **debernardis said:**
> 
...when back home, the Intel network card isn't recognized and to make it work I have to remove the above package.


I have a similar problem: the wireless works when I'm on campus (DHCP, and WPA2 encryption), but doesn't when I'm home (static IPs, WEP).
When I'm home, my wireless card is still recognized, but it can't see any networks: neither my own one (WEP), or my neighbours' ones, that also use WEP.

[UPDATE:]
Sorry everybody: the trick was as easy as it gets... For some mysterious reason, any time I'm home I have to go out to the balcony, and either boot the computer there, or disable/re-enable the wireless on the balcony, to get it working.
No idea why it works that way, but the point is that the problem is fixed for me.

---

### Post by schibros on 2008-11-19
> **Karilex said:**
> I have recently updated to ubuntu 8.10 everything went fine except for my atheros wireless card which ubuntu still doesn't detect(actually it does detect it but the wireless just doesn't work) I had previously tried installing madwifi on ubuntu 8.04 but with being an ubuntu newb and all I failed but by searching around I have seen that I just need to enable ath5k with ubuntu 8.10 unfortunately I have no idea what that is and even less of an idea on how to enable it also if this isn't the way to make my wireless card work could you point me to some alternative instructions to get my wireless card to finally work thanks for taking the time to read this.

_____
oh and by the way I have a compaq c700(c793VU) not sure if that would help but you never know.

_____
here are some infos:


uname -a
```
Linux krauth-laptop 2.6.27-7-generic #1 SMP Thu Oct 30 04:18:38 UTC 2008 i686 GNU/Linux

```


lspci | grep -i net
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:a3:2b:7c  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fea3:2b7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5384 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5147983 (5.1 MB)  TX bytes:898951 (898.9 KB)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16604 (16.6 KB)  TX bytes:16604 (16.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:03:47:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-03-47-D9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

________
Edit: Wireless works after the install it's just that the led does not turn blue and there is no alert message saying the wireless has been turned off so I guess this is solved.




I have been having the same problem with my Atheros WLAN Card on Compaq F700. I have a good feeling that this will work out, since its the same driver that worked out the box on my Hardy Install. I wonder why it was not left as default on Intripid, well i guess there were reason for that.

Ill try this now and i hope it works.

Thanks a million for this.

---

### Post by Karilex on 2008-11-26
Weird I've just reinstalled ubuntu and I don't have to go through togling the wireless on and off weird :confused:

---

### Post by schnutz122 on 2008-11-26
Rock solid.  Worked like a champ for me.  Thanks for the tip - I was pulling my hair out trying to get the MadWifi solution to work.

---

### Post by trubshac on 2008-11-27
Just wanted to add my thanks to hictio - post number 3 in this thread - this has just solved a new incarnation of the same problem.

I have a Sony Vaio VGN-NR38E that has an Atheros AR232x wireless card (lspci -n = 168c:001c) which was sort of working, although not very reliably under Intrepid.  I then did a normal synaptic update of the kernel from 2.6.27.7.11 to 2.6.27.9.13 and the wifi stopped working all together!

I followed the steps in post #3, and hey-presto - I have good reliable wifi again.  :)

Thanks.

---

### Post by hictio on 2008-11-28
Just installed this updates:

```

2008-11-28 13:25:26 status installed man-db 2.5.2-2
2008-11-28 13:25:27 status installed doc-base 0.8.16
2008-11-28 13:25:28 status installed ufw 0.23.2
2008-11-28 13:25:29 status installed initramfs-tools 0.92bubuntu16
2008-11-28 13:26:22 status installed linux-image-2.6.27-9-generic 2.6.27-9.19
2008-11-28 13:26:34 status installed linux-backports-modules-2.6.27-9-generic 2.6.27-9.5
2008-11-28 13:26:34 status installed linux-restricted-modules-common 2.6.27-9.13
2008-11-28 13:26:47 status installed linux-restricted-modules-2.6.27-9-generic 2.6.27-9.13
2008-11-28 13:26:47 status installed xkb-data 1.3-2ubuntu4.2
2008-11-28 13:26:47 status installed libcups2 1.3.9-2ubuntu3
2008-11-28 13:26:47 status installed libcupsimage2 1.3.9-2ubuntu3
2008-11-28 13:26:47 status installed cups-common 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups-client 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups-bsd 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed libgtkhtml-editor-common 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libgtkhtml3.14-19 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libgtkhtml-editor0 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libwbclient0 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:50 status installed libsmbclient 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:50 status installed linux-backports-modules-intrepid-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-image-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-restricted-modules-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-headers-2.6.27-9 2.6.27-9.19
2008-11-28 13:26:52 status installed linux-headers-2.6.27-9-generic 2.6.27-9.19
2008-11-28 13:26:52 status installed linux-headers-generic 2.6.27.9.13
2008-11-28 13:26:52 status installed linux-libc-dev 2.6.27-9.19
2008-11-28 13:26:53 status installed samba-common 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:53 status installed smbclient 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:53 status installed language-pack-gnome-en 1:8.10+20081107
2008-11-28 13:26:53 status installed language-pack-gnome-en-base 1:8.10+20081107
2008-11-28 13:27:05 status installed initramfs-tools 0.92bubuntu16
2008-11-28 13:27:05 status installed libc6 2.8~20080505-0ubuntu7

```

Reboot, and everything seems to be working A Ok with the Atheros.

---

### Post by HuaiDan on 2009-01-01
Oh. My. God.

I have spent *days* trying to getthis thing to work, reading every misleading post on this board and others. Just one wrong path after another. For days. 


This was simple, and it worked! THANK YOU! I went to bed last night thinking this thing was never going to work.

Board mods: this thread should be PINNED, always on top, with flashing red lights and stars, and special search tags for google. THIS IS THE FIX to the problem so many are seeking the solution to.

---

### Post by HuaiDan on 2009-01-01
Upon rebooting, all my AP's disappeared! I think I need to toggle the wireless on, but doing that in System/Hardware was no dice. Is there elsewhere I can do this?
iwconfig shows access point not asscoiated
lshw shows *-network DISABLED etc logicalname: wmaster0 etc etc

Proper drivers seem to be installed, but I see "Support for 5xxx series of Atheros....." as Activated in System/hardware. Should this be so, and how do I enable the interface?

---

### Post by mikaPELL on 2009-01-02
In the Hardware Drivers window:
The "Support for 5xxx series of Atheros 802.11 wireless LAN cards" driver should be [COLOR="Lime"]**activated**[/COLOR], but if you have a driver named "Support for Atheros 802.11 wireless LAN cards", this one should be [COLOR="Red"]**deactivated**[/COLOR].

However, I have the same problem as someone earlier; having to manually deactivate and activate the "...5xxx series ..." driver.

---

### Post by HuaiDan on 2009-01-02
Thanks. I got it back up after some non-specific tweaking and rebooting, can't remember what I did exactly and probably wouldn't be of any help to anybody if I did.

The point is Hictio's suggestion rocks, it's a huge step forward in rendering this little issue. If it doesn't work after that, it's probably just a matter of cleaning up everything that was done *before* this fix was stumbled upon.

---

### Post by pangard on 2009-01-14
*Beware of the kernel!!*

All this stuff was not working, until I booted with the older kernel.

newer kernel: 2.6.27-9
older kernel: 2.6.24-21

I don't really know if this is an issue with the new kernel, or simply a matter of installing things in the proper order, but you should definitely try this if everything else fails.

---

### Post by bluntknife on 2009-01-22
Thank you very much for the fix (post 3) it worked for me although I too have the problem where I have to disable and re-enable the restricted driver every time I reboot..! :confused:

---

### Post by ugm6hr on 2009-01-22
> **bluntknife said:**
> Thank you very much for the fix (post 3) it worked for me although I too have the problem where I have to disable and re-enable the restricted driver every time I reboot..! :confused:

The following ensures ath5k is loaded at boot, ath_hal is NOT loaded at boot.

```
gksudo gedit /etc/modules
```

Add the following line at the bottom:

> ath5k

Then:

Quoted: [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

To blacklist the old modules, do this:

    ```
gksudo gedit /etc/modprobe.d/blacklist
```

And add the following lines At the bottom of the file save and exit

>     blacklist ath_hal
    blacklist ath_pci



Now you need to reboot your system.

IF after this steps you still cannot make it work, you probably have something left still blacklisting ath5k, thus making it not to load. You should search all the files on /etc/modprobe.d for all lines that had:

> blacklist ath5k

And add a # before the start of the line, thus making it into a comment so the above one becomes

> # blacklist ath5k

Save and exit the file.

---

### Post by Hachi-Roku on 2009-02-15
Hey guys. forgive the posting in a solved thread.... pretty please.

Im on a new toshiba l300 and have this same problem.


Ive done everything stated in this thread, and here;

[http://ubuntuforums.org/showthread.php?t=1070029&highlight=wireless&page=2](http://ubuntuforums.org/showthread.php?t=1070029&highlight=wireless&page=2)

[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)

[https://help.ubuntu.com/community/AspireOne110L#WLan](https://help.ubuntu.com/community/AspireOne110L#WLan)


Its mostly the same thing. 
 

ive disabled the standard driver in the main menu "Support for Atheros 802.11 wireless LAN cards", and installed the backport generic drivers with all the rebooting in between. 

Ive also blacklisted the stated lines, and added the ath5k to the modules file.

This new driver with 'ath 5xxx' in the title that people seem to be getting from the backport generic terminal code  doesnt even show up in the main menu.

have i missed something?

Anyone else on a toshiba have a worked soln... i believe this one was for a compaq.... unusual, same card though.

cheers

---

### Post by ugm6hr on 2009-02-15
> **Hachi-Roku said:**
> This new driver with 'ath 5xxx' in the title that people seem to be getting from the backport generic terminal code  doesnt even show up in the main menu.

It doesn't show up in any menu.

It should appear in:
```
lsmod
```

---

### Post by Hachi-Roku on 2009-02-16
> **mikaPELL said:**
> In the Hardware Drivers window:
The "Support for 5xxx series of Atheros 802.11 wireless LAN cards" driver should be [COLOR="Lime"]**activated**[/COLOR], but if you have a driver named "Support for Atheros 802.11 wireless LAN cards", this one should be [COLOR="Red"]**deactivated**[/COLOR].



Thanks for replying. It doesnt show up in my lsmod.

How does one activate it if its not in the driver menu, is there a command line code to do so?

Ive already done the generic backport code. Is there a way to single out the wireless driver within that backport code? As in, download and install only the wireless driver.

After doing the restricted driver code, what command can i use to check if it is there?

thanks!

---

### Post by ugm6hr on 2009-02-16
> **Hachi-Roku said:**
> It doesnt show up in my lsmod.
Then it is not being used.

> How does one activate it if its not in the driver menu, is there a command line code to do so?
Yes - see post 44 above.  Adding **ath5k** to /etc/modules does this.  You can also use modprobe to do it manually.

> Ive already done the generic backport code. Is there a way to single out the wireless driver within that backport code? As in, download and install only the wireless driver.
Yes - but not from the backports-module.  You can download the driver and compile it - but it is harder work and requires recompilation at every kernel update.

> After doing the restricted driver code, what command can i use to check if it is there?
[Click here]("apt:linux-backports-modules-intrepid-generic") - if it tells you it is already installed, then it is.

---

### Post by Hachi-Roku on 2009-02-19
Thanks for the posts!

Ok.. so i traced my steps back and  checked everything ive done;

ive amended the /etc/modules,
added the blacklist lines,
checked every text file in modprobe.d for blacklisted ath5k entries,
Checked the link provided by "ugm6hr" , confirmed that the package IS installed. Thanks ugm6hr.. thats cool.
rebooted, still not in lsmod.

The line: "blacklist ath_pci" is in both /etc/modprobe.d/blacklist-local and /etc/modprobe.d/blacklist. Is that a problem?

tried to load ath5k manually

```
jon@jon-linux:/etc/modprobe.d$ modprobe ath5k
FATAL: Module ath5k not found.
```

So it seems ive got the package but not the ath5k module??? weird!


Im not sure where to go from here.... help please!

---

### Post by binbash on 2009-02-19
This also fixed my atheros wireless : 

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by edbash on 2009-02-21
Gracias, hictio!
After 8 months I have wireless on my presario c700.

---

### Post by hictio on 2009-02-23
De nada, edbash! :D :D

The best thing is, I don't know on what hardware you are running Intrepid, but on my Compaq F700, the thing keeps going just like day one, even tho I have installed every single update that Ubuntu has released for this version.

At first I was a bit scared, but so far every single update has worked like a charm on the laptop, not a thing broken (not only WiFi, but also suspend/ sleep, USB after those, etc.)

---

### Post by jonny2vests on 2009-05-10
Thanks hictio, your method worked.  But only once.

I rebooted and was able to setup a wireless connection, but it hasn't worked since.  And no matter what I do (uninstalling backports and re-installing etc) I cant get it to work again.  iwconfig outputs "no wireless extensions".  I'm a bit stumped.  Anyone?

---

### Post by Hachi-Roku on 2009-05-10
Im in the same stumped boat! except i didnt get it to work even once.

Please pm me your solution if you get it working!!!

---

### Post by jonny2vests on 2009-05-11
Turns out I was loading the wrong kernel in the grub menu.  Sorted now.

---

### Post by Hachi-Roku on 2009-05-16
What are the details?? ie what kernel are and were you booting?
are you on a toshiba?

cheers.
J

---

### Post by hictio on 2009-05-16
Just a heads up, don't know if someone would care, but, on 9.04, using the same laptop with the same WiFi chip/ card (doh! ;) ) everything works just golden, w/o the need for anything.
And Ubuntu 9.04 does boot faster, yes :)

---

### Post by Hachi-Roku on 2009-05-21
Thanks for the heads up... someone does care, and thats me!

just upgraded to 9.04 and nothings changed. still doesnt work, 
ath5k still doesnt show up in lsmod.
ive checked all the blacklist and module text files and they are unchanged.
i.e. still have the modified entries described in this thread.

i notice ive now got a madwifi alternate driver in the 'hardware drivers' menu. Been playing with that, but if i activate it then reboot... its deactivated again.

not really sure what to do now. gonna mess around for another little while.

any help appreciated!

---

### Post by wintermute000 on 2009-05-26
This is for a 5212 on Jaunty but hope it helps

a.) Install backports (sudo apt-get install linux-backports-modules-jaunty)
b.) Blacklist ath5k in /etc/modprobe.d/blacklist.conf
c.) add ath_pci into /etc/modules

Fixed it right up. Wifi interface name has changed to ath0 from wlan0 but that's not a concern for lol

---

### Post by Hachi-Roku on 2009-05-26
hmmm. so after a reboot i seem to have the wireless icon in the system tray!

one small success! great.

however, my laptop is sitting next to my router and doesnt see the wireless point. other computers are on this access point so i know it works.

still getting no love from lsmod re: ath5k.
Also iwconfig/ifconfig shows no wireless entries.

more fiddling....

---

### Post by Hachi-Roku on 2009-08-11
Ok.... so after a very long time, I did a fresh install of Jaunty (rather than my previous upgrade), and wireless now works!

I think network manager even remembers my wireless key. Astonishing. That was a massive problem in Hardy.

Smooth sailing in Troublesome Toshiba land now.

Cheers

---

