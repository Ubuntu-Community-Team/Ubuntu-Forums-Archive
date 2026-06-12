---
title: "wireless state &quot;connecting (configuring)&quot; ubuntu 10.04"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by paulmagarey on 2012-03-24
Hi all,

I have an ongoing problem at home with my wireless Broadcom hardware and driver.  I have had it working once, but now whenver I try to log-on to my wireless network at home, just tries to connect (configure) but never makes it.  the output from nm-tool is:

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:14:22:BC:1E:33

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.15.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.15.1

    DNS:             203.10.76.15
    DNS:             203.10.76.16


- Device: wlan0  [Auto Rupert] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:14:A5:39:E6:69

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Rupert:          Infra, 00:13:10:7E:48:51, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    3rd from the sun:Infra, 74:44:01:81:5A:FD, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA2
    Desktop-PC-Wireless: Infra, 00:26:F2:DF:2D:30, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    delphikw:        Infra, E0:91:F5:E4:64:6A, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA2
    Home:            Infra, 00:1F:33:4D:03:76, Freq 2412 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2

Output from sudo lspci -nn | grep 0280

[sudo] password for paul: 
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

I have a dual boot with Win XP and Ubuntu 10.04. Wireless works fine on XP. Also, the other day, I managed to log on to someone else's wireless at someone else's house. What the hell is going on with mine. Would be very grateful for any advice, please be explicit with instructions as am beginner.

Warm regards,

Paul

---

### Post by Bucky Ball on 2012-03-24
Are you sure you have the correct details in Network Manager to match your router's? Access point name, security type and key, etc? Right click the network icon and 'edit connections'.

You have the correct driver installed, incidentally, but are maybe missing firmware:

```
Driver: b43
```Open 'additional drivers' and confirm it is enabled. Also, go into Software Centre and confirm you have:

firmware-b43-installer
b43-fwcutter 

... both installed. Did you plug in with a cable and get updates before attempting to get wireless working, incidentally? This is a must but not very clearly pointed out unfortunately. This will get a lot of cards working 'automagically' nowadays. I suggest doing that (if you haven't already) before anything else then checking 'Additional Drivers'. ;)

PS: Please put terminal output between [code] tags. [code] at the beginning and add a '/' before 'code' in the end tag or 'Go Advanced', mark out the code and click the hash (#) symbol.

---

### Post by paulmagarey on 2012-03-24
Thanks very much Bucky for your help.

Re "Are you sure you have the correct details in Network Manager to match  your router's? Access point name, security type and key, etc? Right  click the network icon and 'edit connections'." 

I'm not sure what you want me to compare here. I've tried comparing the edit connections data for the wireless network (mine is rupert) with the output from nm-tool, but the only thing that comes to mind is that the HW address is actually a MAC address - I copied the HW address from the nm-tool output and put it in the MAC address field for the Rupert network, but it didn't seem to make much difference - created two Rupert networks in the edit connections Wireless tab. 

Glad to know I've got the right driver, not sure how to tell if I'm missing firmware and not sure where you want me to "Open 'additional drivers'" - I've looked in System - Admin - Hardware Drivers (that always looks for additional drivers, but the B43 one is already installed and the only one that comes up).  Also looked all through the System Admin and Preferences submenus and also in the Ubuntu Software Centre - is there something missing from my system?  Remember I'm on 10.04 

Can confirm that 

firmware-b43-installer
b43-fwcutter 

are both installed. And I've recenntly got all update with cable plugged in.

Thanks for tip re putting terminal output b/w [code] tags. - will do so in future.

And remember, that recently, on the same computer, with 10.04 running, I got wireless working at someone else's house  - so what am I doing wrong at home, or what the other house experience just a fluke...

More help would obviously be great.

Cheers,

Paul

---

### Post by Bucky Ball on 2012-03-24
Okay, drivers and firmware are all installed and fine so that's not an issue. (Additional Drivers = Hardware Drivers btw; just all depends on the release cos it was renamed.) Is the b43 stuff enabled in Additional Drivers? I would think so.

Forget the MAC address. Delete from wherever you inserted it.

Right click on the network icon then 'Edit Connections'. Check the security type your router is using (WEP, WPA etc) and make sure you are using the same type in Network Manager (the window that comes up when you are editing connections).

Make sure you have 'Available to all users' and 'Connect Automatically' ticked.

Make sure you have the IPV6 tab set to 'Ignore'. 

Reboot once if you change anything and see if the machine attempts to connect to the correct network.

Are you getting the IP address for your local machine served by your router or are you using a static IP address (which should be set on the local machine)?

---

### Post by paulmagarey on 2012-03-24
Thanks again Bucky.


On the Linksys Router I have, Wireless Security is given as "WPA Pre-shared key". I deleted the old Rupert network connections and have just tried again to connect from scratch - the security option that comes up automatically (the only one available when first making a connection) is listed as "WPA and WPA2 Personal". When I right click on the network icon, then 'Edit Connections' another type of security option comes up "WPA and WPA2 Enterprise" but I can't get this to work on through Edit Connections.


I have found that 'Available to all users' was unticked but on checking the connection of the house where recently I was at and where wireless worked, it too is unticked. Anyway, following your advice, I've ticked 'Available to all users' and 'Connect Automatically' was already ticked. IPV6 tab set was already set to 'Ignore'. Have rebooted, but am still experiencing the same problem and the nm-tool output still shows "Connecting (configuring") (was getting excited for a while there.) 

I think I'm getting my IP address for your local machine served by my router - not sure how exactly to tell this, but any laptop can connect to the cable and get onto the internet.


Thanks again. Hope I haven't expired you thoughts on how to get this working for me!



Cheers,


Paul

---

### Post by paulmagarey on 2012-03-24
some additional info that might help: what happens is that I connect to Rupert (my network) and then the nm-tool shows
```
  State:             connecting (configuring)

```

and it stays like that for a while, but I don't have internet connectivity via wireless. Then eventually it drops out and asks me to log in again and at that point the nm-tool shows

```
 State:             disconnected

```

and it asks me to log in again. So Frustrating!

---

### Post by paulmagarey on 2012-04-12
thanks to Bucky Ball for first reply, which did in fact contain the solution to the problem. Was looking through the router Gui interface to see if I could turn off encryption and found an old password in the WPA shared key!  How that was still there even though I thought I'd reset the thing a dozen times, I'm not sure, but anyway, am now using wireless after making sure the WPA shared key matched my password that I was inputing through the Network interface on the laptop!  How simple. Wasted a lot of time on this - key is to look for the simplest solution. Ockham's razor. 

Not sure how I can mark this thread as solved, but it is solved.

Cheers,

Paul

---

### Post by Bucky Ball on 2012-04-12
Hey, Paul ... rockin' good news. You can mark as solved by hitting 'Thread Tools' at the top right of this page above the first post and clicking 'Solved'. ;)

Don't forget to post about other issues (if you have any).

---

### Post by paulmagarey on 2012-05-12
> **Bucky Ball said:**
> Hey, Paul ... rockin' good news. You can mark as solved by hitting 'Thread Tools' at the top right of this page above the first post and clicking 'Solved'. ;)

Don't forget to post about other issues (if you have any).

thanks.

---

### Post by paulmagarey on 2012-05-12
actually, I marked this as solved but have now marked it as unsolved. For various reasons I've had to re-install 10.04 after moving to 11.10 Lubuntu. Can now not even get the B43 driver to install!  GRRR! When I try to activate, I just get a message (see attached) saying the installation failed and that I should see the log file /var/log/jockey.log (also attached).

Any advice would be appreciated.

Cheers,

Paul

---

### Post by Bucky Ball on 2012-05-12
Hmm, odd. I take it you are online with an ethernet cable at the time?

You might like to try installing them manually with Synaptic. Look for:

b43-fwcutter
firmware-b43-installer

Install and reboot. Now see if you can install with 'Additional Drivers'. 

PS: Could you also post the output of:

```
iwconfig
```

---

