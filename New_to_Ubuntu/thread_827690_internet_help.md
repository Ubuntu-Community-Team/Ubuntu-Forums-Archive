---
title: "internet help"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Roeyfreak10 on 2008-06-13
somebody please help me set up my internet ive been stuck trying to do it for the past three days i just got linux and really dont know what im doing and i really would appreciate it if someone could help.

---

### Post by iaculallad on 2008-06-13
Try to give some specific informations regarding your connection problem. What mode of connection are you using? Wireless or Wired? DSL or Dial-up? What errors are you getting if any?

---

### Post by Roeyfreak10 on 2008-06-13
ok so i have the main router downstairs and then a linksys wirless network adapter in my room via usb and i took the wep off the internet so that i wouldnt have to enter it upstairs i click it the two computers in the top riht corner i find my ssid i click it it shows that its connecting it keeps showing it then it stops and im not conneceted to anything

---

### Post by iaculallad on 2008-06-13
Try to post the output of this commands:

```
ifconfig
```

```
lshw -C network
```

---

### Post by AndThenWhat on 2008-06-13
plugin your usb internet adapter and then open a terminal and type

```
lsusb
```
and
```
iwconfig
```
and
```
ifconfig
```

and paste the output here so we can hopefully be of more assistance

---

### Post by Roeyfreak10 on 2008-06-13
roey15@Roeys-Computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:89:e9:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115200 (112.5 KB)  TX bytes:115200 (112.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:41:0f:6b:d6  
          inet6 addr: fe80::20c:41ff:fe0f:6bd6/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:231 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:119163 (116.3 KB)  TX bytes:1600 (1.5 KB)

---

### Post by Roeyfreak10 on 2008-06-13
roey15@Roeys-Computer:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by iaculallad on 2008-06-13
> **Roeyfreak10 said:**
> roey15@Roeys-Computer:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

That would be big "C", Linux in general is case-sensitive.

```
lshw -C network
```

---

### Post by Roeyfreak10 on 2008-06-13
roey15@Roeys-Computer:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:89:e9:8a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0c:41:0f:6b:d6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.101.4-84 wireless=IEEE 802.11b

---

### Post by vivekrocks on 2008-06-13
What is the network type? Is it automatic or manual?
If u dont know check with your network administrator!
After that try following code

```
ifconfig
```

Then check whether you are behind a proxy. Most of the networks are! Then put the proxy-server address and port number in the system proxy or your internet browser. I think then you your prob will be solved!

---

### Post by Roeyfreak10 on 2008-06-13
how do i check if i am behind a proxy?

---

### Post by iaculallad on 2008-06-13
When you say "took WEP off the Internet", would mean that you're using an unencrypted connection.

Try the commands below if you could get an IP address from your Router.

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo dhclient wlan0
```

---

### Post by Roeyfreak10 on 2008-06-13
ok i did all that but now what?

---

### Post by iaculallad on 2008-06-13
> **Roeyfreak10 said:**
> ok i did all that but now what?

Try to re-connect.

---

### Post by Roeyfreak10 on 2008-06-13
still aint workin. i go and click on my ssid it starts to connect then nothing happens...

---

### Post by iaculallad on 2008-06-13
To straighten things up: where exactly did you "took WEP off the Internet", from the router or from your USB wireless adapter? If you did remove the WEP key off your router, try to remove it too on your wireless adapter. Try to reconnect afterwards.

---

### Post by Foghornleghorn on 2008-06-13
> **Roeyfreak10 said:**
> still aint workin. i go and click on my ssid it starts to connect then nothing happens...

Have you correctly defined your ISP and the Telephone number?

---

### Post by Roeyfreak10 on 2008-06-13
from the router. i connected to it removed the encryption saved settings. restarted router.

---

### Post by iaculallad on 2008-06-13
> **Roeyfreak10 said:**
> from the router. i connected to it removed the encryption saved settings. restarted router.

No, you'll be breaking your security. Just re-place the WEP keys both on your wireless router and your PC like the old setting you had before. Then try to reconnect.

---

