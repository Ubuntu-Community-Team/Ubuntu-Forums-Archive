---
title: "Screen resolution and WEP?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by kjacobs on 2008-11-22
Well, after a rocky start I reinstalled Ubuntu 8.10 for a clean install. It is working great so far. Except...

1. The screen resolution only allows a max of 800X600. Ubuntu 7.10 gave me 1024 or more. How can I change that?

2. My wireless usb adapter was picked up great. My wireless router is using a 64 bit WEP. There is no option for a 64 bit WEP. I tried the 40/128 option, but that was a no go. How do I connect to the 64 bit WEP?

Thanks in advance...

---

### Post by Gone fishing on 2008-11-22
I wonder if you couldn't directly modify the /etc/network/interfaces file 

wireless-key s:aaaaaaaa 

(the s: means ascii password rather than hex)

However isn't 40 and 64 WEP the same 8 character password?

---

### Post by kjacobs on 2008-11-22
That's what I thought....40 and 64 had the same number of characters. Anyway, I tried turning off the WEP on the router and conencting without it and it still will not connect. Ubuntu sees the usb wifi adapter and is scanning for wireless networks fine, it just will not connect. It would not connect to my neighbors open network either. Both had 1/3 full signal strength.

I had Puppy Linux on that machine for a couple days and it recognized the card and would connect to both networks, as long as the WEP was off. I could not get it to connect with the WEP on.

Guess I need more help? With the screen problem, too?

---

### Post by jimmy the saint on 2008-11-22
what is your hardware?  wireless card/video card?

---

### Post by kjacobs on 2008-11-22
The Video Card is a GeForce 4 Ti4200. The WiFi USB is a Gigafast WF741. Its an older usb dongle, but still works fine.

---

### Post by Gone fishing on 2008-11-22
I'm just wondering if you've got a wired LAN interface thats getting in the way? Can you disable the other interfaces? What happens if you try and ping the router?

if you ifconfig what's the readout?

---

### Post by kjacobs on 2008-11-22
Here is what I get with the ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:b2:b1:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:47:07:69:a9  
          inet6 addr: fe80::290:47ff:fe07:69a9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:698 (698.0 B

I have tried pinging the router but get an "unable to connect to network" message. With 2 wireless routers in range (mine with WEP and one without) I can try both and get the same results.

---

### Post by Gone fishing on 2008-11-22
Well the wireless isn't getting an IP address

Whats the readout from sudo iwconfig?

From the applet on the top bar can you see any networks?

I set my wireless network by modifying /etc/network/interfaces I'm using 128 WEP and it looks like:

```
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:aaaaaaaaaaaaa
wireless-essid fish

auto wlan0
```

note I'm using a fixed IP maybe you could try that

---

### Post by Kosimo on 2008-11-22
Just a word of advice...
If you can, please set your access point to WPA2. WEP is senseless nowadays

---

### Post by roger_1960 on 2008-11-22
Hi

Re video, see this post:

[http://ubuntuforums.org/showthread.php?t=970237&highlight=GeForce4](http://ubuntuforums.org/showthread.php?t=970237&highlight=GeForce4)

It may point you in the right direction.

---

### Post by kjacobs on 2008-11-22
Here is my sudo iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  Nickname:"zd1201"
          Mode:Managed  Frequency:21.982 kHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   
          Retry   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have 2 wireless networks showing in the network applet in the top bar. I have tried connecting to both. My wired network is grayed out because it is not connected to anything. By the way, thanks so far for helping out with this....

---

### Post by Gone fishing on 2008-11-22
Looks to me like its almost there - I'd try editing the interfaces file and possibly using a fixed IP and rebooting.

Obviously WPA is better than but lets get it working first :) 

(I have to use WEP as WDS doesn't work with WPA at least on my access points, I, however, don't feel too vulnerable as a quick scan of Maseru West show about 10 networks and several that are unsecured)

---

### Post by kjacobs on 2008-11-22
Many thanks to all for the help...

It looks like I need to start be dropping back to Ubuntu 8.04 before I do anything else to solve the nvidia driver problem for now. Then I will deal we getting the wireless networking going again. Thanks again.

---

