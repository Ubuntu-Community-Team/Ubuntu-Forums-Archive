---
title: "wifi problem"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by brian_stokes0 on 2008-09-30
I have a toshiba satellite A75 series laptop with an atheros 5212 wifi built in. After the upgrade to 8.04 I started having problems with my wifi. I tried resolving these problems by asking for help on the forums but no solution worked. So I did a complete reinstall. Now things are better but my wifi is still not working properly.

I don't have any kind of signal strength indicator on my bar anymore and even more frustrating every time I start up my laptop I have to open the wireless settings and renter my WPA password. If I restart my laptop the internet wont work and when I open the setting the password seems to be obscenely long series of dots which is way more characters than my password.

How can I fix this? why did I not have this problem with earlier versions of Ubuntu?

PLEASE HELP!

---

### Post by hyper_ch on 2008-09-30
what does

```

iwconfig

```
return?

---

### Post by wilsong on 2008-09-30
You might want to research and try to a program called 

Wifi-radar 

it seemed to work better for me than the Network manager that ubuntu 8.04 had, now im using the Alpha 6 of Ubuntu 8.10, and its a lot nicer, sort of like the KDE4 manager that shows all the area wireless networks. 

of course ifconfig you could probably do everything from console but it would be very difficult i really liked wifi-radar though it was nice.

---

### Post by brian_stokes0 on 2008-09-30
Alright I started up my laptop opened a terminal and typed IWCONFIG and heres what I got:
brian@brian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Home"  Nickname:"Home"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-62 dBm  Noise level=-86 dBm
          Rx invalid nwid:1250  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

After going into the network settings yet again and put in my password I did the IWCONFIG thing again and heres what i got this time: 

brian@brian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Home"  Nickname:"Home"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:33:03:76   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-54 dBm  Noise level=-95 dBm
          Rx invalid nwid:7613  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by hyper_ch on 2008-09-30
when posting output of a file or a command use [noparse]```

```[/noparse] brackets around it to make it easier to read.

---

### Post by brian_stokes0 on 2008-09-30
So use [code] [code] like quotations marks. Got it. Do you need me to repost the data?

---

### Post by brian_stokes0 on 2008-09-30
Alright i did another Iwconfig and here is what I got.


```
brian@brian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Home"  Nickname:"Home"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:33:03:76   
          Bit Rate:5 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-67 dBm  Noise level=-95 dBm
          Rx invalid nwid:114877  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

BTW, thanks for your help.

---

### Post by rybaxs on 2008-09-30
I've got a problem on my Wifi it doesn't activate. I've got a problem like brian_stokes0. how did u solve the problem brian_stokes0? 


Wifi-radar -> hope this works. thanks!

---

### Post by hyper_ch on 2008-09-30
one problem I see is this here:
```

Bit Rate:5 Mb/s 
```

How far are you away?

---

### Post by brian_stokes0 on 2008-09-30
i have wifi radar installed but it says no wpa. so open the the tab arrow and it driver but i have no idea what to put in the box for the driver.

My wifi problem is still unresolved.

---

### Post by brian_stokes0 on 2008-09-30
not far, the time before i got 54mb. Im on a network with 5 other pcs my wife might be hogging the bandwith when I ran the iwconfig.

I think now that it is a driver problem. But I still dont know how to fix it.

---

### Post by brian_stokes0 on 2008-09-30
hey Im gonna try this [HTML]http://ubuntuforums.org/showthread.php?t=816780 [/HTML] I will let you guys know if it works.

---

### Post by brian_stokes0 on 2008-09-30
No dice.... I hit a snag on step four.

```
brian@brian-laptop:~$ svn co https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6 
svn: PROPFIND request failed on '/madwifi/branches/madwifi-hal-0.10.5.6' 
svn: PROPFIND of '/madwifi/branches/madwifi-hal-0.10.5.6': Could not resolve hostname `svn.madwifi.org': Host not found (https://svn.madwifi.org) 
brian@brian-laptop:~$ cd ~/madwifi-hal-0.10.5.6 
bash: cd: /home/brian/madwifi-hal-0.10.5.6: No such file or directory 
brian@brian-laptop:~$ make 
make: *** No targets specified and no makefile found.  Stop. 
brian@brian-laptop:~$ sudo make install 
[sudo] password for brian: 
make: *** No rule to make target `install'.  Stop. 
brian@brian-laptop:~$ 

```

I am begining to get desparate here. Help me please. I am this close to dropping 2 Gs on a laptop.

---

### Post by nothingspecial on 2008-09-30
ok madwifi should work for your card hang on and I`ll help

---

### Post by nothingspecial on 2008-09-30
Sorry I`m in the middle of something else here, have you got or can you get a wired connection.

---

### Post by brian_stokes0 on 2008-09-30
Thanks so much.

---

### Post by brian_stokes0 on 2008-09-30
okay i am plugged in

---

### Post by nothingspecial on 2008-09-30
Go to this url

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)

and download the latest snapshot

Thats the one at the bottom.

Extract it to your desktop.

More instructions on the way, like I said, busy.

---

### Post by nothingspecial on 2008-09-30
Open a terminal and navigate to the extracted file

```
cd Desktop/madwifi-hal-0.10.5.6-r3861-20080903
```

If you`ve not got this package necessary for compiling get it

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then try compiling it again

```
sudo make
```

```
sudo make install
```

Unless I`ve made any typos this should work.

Appologies but I`m trying to do 2 things at once.

---

### Post by brian_stokes0 on 2008-09-30
Well, 
     no problems running the commands in the terminal but my wifi problem still exists. :(

---

### Post by nothingspecial on 2008-09-30
Ok lets see if your card is recognised properly can you post the out put of
```

sudo lshw -C network
```

---

### Post by brian_stokes0 on 2008-09-30
```
 *-network:0             
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:90:96:c1:e6:28
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.102 latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:d5:59:1e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
brian@brian-laptop:~$ 

```

---

### Post by Alldan on 2008-09-30
look here:
[http://ubuntuforums.org/showthread.php?t=773016](http://ubuntuforums.org/showthread.php?t=773016)
good luck

---

### Post by brian_stokes0 on 2008-09-30
All dan I will try  wicd tommorow i have been at this all night and I have to get some sleep. Thanks to everyone who has offered me assistance.

---

### Post by brian_stokes0 on 2008-10-01
I followed the directions and I hit a snag installing wicd.
> 
W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A

---

