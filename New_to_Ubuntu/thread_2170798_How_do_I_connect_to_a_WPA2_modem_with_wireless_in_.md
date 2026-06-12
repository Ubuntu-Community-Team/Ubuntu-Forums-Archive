---
title: "How do I connect to a WPA2 modem with wireless in Ubuntu Server"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by Niall_Dawson on 2013-08-27
Hi! :D

I posted a thread before about an ethernet issue which was a complete noob mistake but now I genuinely need help!

Ive installed a RaLink wireless pci card. Its being detected in the iwconfig and ifconfig commands as up and running (I think, sorry I'm still completley new to this) I also have the desktop GUI installed if that helps me out about more.

Thanks in advance and I look forward to this fun learning experience :D

---

### Post by GwL3eNC on 2013-08-27
Hello, 

the easy and little unsafe way is to edit your /etc/network/interfaces. The lines should
look like this if wlan0 is your internet interface.

iface wlan0 inet dhcp
    wpa-ssid YOURSSID
    wpa-psk YOURKEY

PS. If you go this way you have to completely remove Network Manager GUI.

---

### Post by Niall_Dawson on 2013-08-27
Hi,

I tried all that. Still doesnt work, currently I'm using an ethernet connection

---

### Post by GwL3eNC on 2013-08-27
ok,

post the result of ifconfig and iwconfig.

---

### Post by Niall_Dawson on 2013-08-27
iwconfig

```
niall@Niall:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

virbr0    no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

ifconfig

```
niall@Niall:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d3:18:5a:c8  
          inet addr:192.168.137.228  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe18:5ac8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:156846450 (156.8 MB)  TX bytes:6017155 (6.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1056315 (1.0 MB)  TX bytes:1056315 (1.0 MB)

virbr0    Link encap:Ethernet  HWaddr ca:15:cd:91:9e:69  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:37:34:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by GwL3eNC on 2013-08-27
Hmm, the only problem is the connection. Are you shure networkmanager is removed? In my first post a

auto wlan0 is missing. sorry for that.

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid YOURSSID
    wpa-psk YOURKEY

have yout tried

sudo ifup wlan0

to start wlan0 manualy

---

### Post by Niall_Dawson on 2013-08-27
the interfaces file looks like this my friend

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

I tried sudo ifup wlan0 and there was still no joy :(

EDIT: I tried adding 

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid YOURSSID
    wpa-psk YOURKEY

to the file to see if that would help and sadly it didnt

---

### Post by GwL3eNC on 2013-08-27
why dont you copy the lines i gave you in your interfaces file (as sudo). You must only 
change the uppercase letters to your wlan settings ESSID and WPA Key. Then
try again sudo ifup wlan0.

PS. Sorry, dont saw your edit.

---

### Post by Niall_Dawson on 2013-08-27
still isn't working, BUT, we have some progress me thinks

```
wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:37:34:7f  
        **  inet6 addr: fe80::2a1:b0ff:fe37:347f/64 Scope:Link**
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:282 (282.0 B)  TX bytes:2388 (2.3 KB)
```

if you notice we have inet6 now but no IP address. Is that any progess do you know?

---

### Post by GwL3eNC on 2013-08-27
thats like the output of my ifconfic. because i'am connected there is also an ipv4 address. I'm dont know
further. if you want to do a successful sudo ifup wlan0, i know shure, the interface wlan0 must be in the interfaces file,
else ifup dont know the interface. your wlan interface is wlan0, if you get automatic ip from your
router the above lines must work. Sorry, that i cant solve your probem.

---

### Post by Niall_Dawson on 2013-08-27
Hopefully someone else will discover the thread. Thank you very much for what help you gave me :) kudos

---

### Post by Werne on 2013-08-28
Have you tried using wpa_supplicant? I didn't have much luck using it on an Atheros card (likely due to not having madwifi/bsd drivers compiled for Atheros) but you may have some luck using it on a Ralink card. Make sure that you have the required firmware first, I had an issue on Debian with a Ralink dongle where it appeared to work fine but was missing rt2870 firmware. You can check in dmesg or you can run "update-initramfs -u" which will yap if you're missing any firmware (at least it yaps to me).

Anyway, if you want to try, first you have to generate a wpa_supplicant.conf file using wpa_passphrase, that's simple, the commad is:
```
wpa_passphrase ssid password > /etc/wpa_supplicant.conf
```
You have to be root (either through sudo -i or su) to export the result to /etc/wpa_supplicant.conf, sudo wpa_passphrase blah blah > /blah/blah.conf won't work. Then you can run wpa_supplicant to debug and see if it works. Or you can write wpa_supplicant.conf yourself:
```
network={
    ssid="modem_name"
    psk="modem_password"
}
```
I recommend the wpa_pasphrase path though. Either way, run wpa_supplicant afterwards in debug to see if it works:
```
wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -d
```
If it doesn't work, try changing the driver with the -D option, like so:
```
wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf -d
```
Change wext to preferred driver, or use wext if it works for you. See the list of drivers with the following:
```
wpa_supplicant -h
```
If it works right, you can run wpa_supplicant in the background with this:
```
wpa_supplicant -B -iwlan0 -c/etc/wpa_supplicant.conf
```
The thing is, if it works, it works. If it doesn't, well, it doesn't. Will it work? I have no idea.:|

As I said, I never had luck with it on an Atheros card, I did have some half-arsed results using nl80211 driver though. All in all, I think it might be worth a shot in your case, there's no harm in trying.;)

---

### Post by Niall_Dawson on 2013-08-28
Nope it didnt work, thank you though. The wifi card is working because in the debug its showing the name of another wifi network in the BSSID

EDIT:

Ill play around with it and if i can find a solution Ill post it here.

---

### Post by Niall_Dawson on 2013-08-28
UPDATE:

I found a solution for the problem, with the help of people here I was able to make the wpa_supplicant.conf file.
From here I was still in issue but I done some research of different network managers.

If youre using ubuntu server install ubuntu desktop with the "apt-get install ubuntu-desktop" command.
Once thats installed download **wicd **in the software centre. It worked for me and I hope it works for anyone else that had my issue

---

