---
title: "Wireless Internet In Taskbar disappeared"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Patrick Snyder on 2008-10-31
**Problem:** The icon on the top right that one can normally click to view and connect to wireless networks is gone!  How do I get it back!? (>_<)

**Details**
----------------
I installed 8.10

The wireless icon on the top right was there so I clicked on my router & put in the WPA password.

My provider (telecomitalia.it) has some weird blockage on the internet *(pages begin to load but stop)*, but I've found that "sudo pppoeconf" fixed the problem when I had a wubi 8.04 installation *(this time I partitioned with XP)*.  So I did that again for 8.10 and the internet worked just fine.

It said there were 6 updates, so I installed them.

It said a restart was needed so I restarted.

Upon restart there was no more icon.  I restarted a few more times but no luck.  I looked around the system for anything "network" or "internet"-like but everything I found wasn't helpful to me.  I can't connect to the internet (>_<)

I'm still very new to Ubuntu.  Any help would be greatly appreciated! (^_^)/

---

### Post by eolson on 2008-10-31
right click on the spot where you want the icon
click on add to panel
scoll down until you find the icon (I think it's called network monitor)
click on it
should be done

---

### Post by Patrick Snyder on 2008-11-01
Hi, thank you for the reply!

When I click on the Network Manager it doesn't give me a list of wireless networks.  Instead it opens a box:

General Tab
-----------
Connection
Name: Io  *(Drop down box with no other options)*
Status:  Idle

Activity
Received: 80 packets (3.9 Kb)
Sent: 80 packets (3.9 Kb)

Support Tab
-----------
Internet Protocol (IPv4)
Address: 127.0.0.1
Subnet Mask: 255.0.0.0

Network Device
Type: Local Loopback
Address: 00:00:00:00:00:00




I had put this Network Manager icon up there before, but because of the difference in behavior to what I'm used to I thought it was a different icon.  I'm glad to know I wasn't going crazy =P

So how do I get out of this "Local Loopback" and on to scanning for wireless routers to find mine?



**More info:**
----------
In **Network Tools**:
Loopback Interface (Io) is selected
*(Drop down box: I can also select: eth0, eth1)*

eth0  (I think this is my wired connection which I haven't tried yet)
IP Information *(nothing written below)*

Interface Information
Everything: not available

Interface Statistics
Everything is at 0


eth1 *(I think this is my wireless)*
IP Information
Protocol: IPv6
IP Address: *(stuff written here, looks kinda like a MAC address but I don't really know)*
Netmask / Prefix: 64
Broadcast: *(nothing here)*
Scope: Link

Interface Information
Hardware address: not available
Multicast:  not available
MTU:  not available
Link speed:  not available
State:  not available

Interface Statistics
Transmitted bytes: 1.1 KiB
Transmitted packets: 12
Transmision errors: 0
Received bytes: 0.0 B
Received packets: 24
Reception errors: 0
Collisions: 0


In **Network Connections**:
_Wired_
ifupdown (eth1)| Never

_Wireless_
Auto *(My router is the listed here, It's the only 1)*|12 hours ago

_Mobile Broadband_
(Nothing)

_VPN_
(Nothing)

_DSL_
DSL connection 1|never
(I may have put this in when trying to find an alternative to "sudo pppoeconf")


When I click on my router in _Wireless_:
Connect automatically is not checked, but checking it doesn't seem to do anything.

When I click on "Show password" for the WPA & WPA2 Personal, it's something completely different than what I entered.  I try to re-enter my WPA key, but every time I go back to Network Connections and click "Show password" it's back to the odd long key ("f7839d20bd001cbb... etc, etc.)



Please let me know if any of this helps (^_^)/

---

### Post by bumanie on 2008-11-01
Unfortunately, there are a number of threads like this one. I in fact used intrepid when it was beta and my atheros wifi card worked. During the RC stage, a partial kernel upgrade came out and killed my wifi - I got it going by using ndiswrapper (and its gtk frontend). Ndiswrapper and the gtk is in the repositories - it worked very well when I came across the correct .inf file to run in it. I can help is you have an AR242x atheros card. If you don't know, post the output of > lspci

---

### Post by Patrick Snyder on 2008-11-01
Thank you for your reply!

I'm not sure what to do next. 

_Here is the output of lspci_
```
patrick@patrick-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
patrick@patrick-laptop:~$ 
```

_I installed the following from my Ubuntu CD_
ndiswrapper-common_1.52-lubuntu1_all.deb
ndiswrapper-utils-1.9_1.52-lubuntu1_i386.deb
ndisgtk_0.8.4-1_i386.deb


_I searched for ndisgtk on my File System and found:_
Windows Wireless Drivers  *(Command: gksu /usr/sbin/ndisgtk)*
I ran it and it and tried:
+ Install New Driver

This is where I'm stuck.
I don't know what to put in.
I tried netwlan.inf and netwlan2.inf from my windows directory and both say "Invalid Driver!"


Please let me know what I can do from here (^_^)/

---

### Post by Patrick Snyder on 2008-11-02
Update:
I plugged an ethernet cable directly in and the Taskbar icon was back.  I clicked on it and it said something to the effect that the wireless network was unmanaged.

I can't tell you exactly what it said, because I rebooted and the Taskbar icon went away again (>_<)

The ethernet cable was still in.
I can get online with it.  But not with wireless.

The interesting thing was, I have the "Network Monitor" thing that can be added to the panel.  It looks exactly like the icon that I'm missing, but when they were both on the taskbar, they did different things.

When I left-clicked on the normal one, it has a drop down menu of connections.  When I left-click on the added one, it opens the window I described above.

Let me know if there's anything I can do.  I really want an alternative for XP and I really like the way ubuntu feels, but if I can't get it to scan for and connect to wireless networks, I can't use it :(

---

### Post by mikewhatever on 2008-11-02
Hi Patrick, the icon you are missing is not the network manager, but nm-applet. You can try adding it to the notification area by pressing alt+f2 and typing nm-applet. It's important to note that nm-applet lives in the notification area and not on the panel. You may need to add the notification area to the panel fist the same way you've added the network manager icon.

---

### Post by Patrick Snyder on 2008-11-03
> You can try adding it to the notification area by pressing alt+f2 and typing nm-applet. It important to note that nm-applet lives in the notification area and not on the panel. You may need to add the notification area to the panel fist the same way you've added the network manager icon.Thanks for the reply.

Unfortunately, when I typed nm-applet nothing happened.  I then added the "Notification area".  When I added it, 3 tiny dashed lines were added to the bar.  I tried Alt-F2 and typing nm-applet again and nothing happened.  I added a few other "Notification areas" to different panels =P  Each time I simply get 3 more tiny dashed lines, but typing nm-applet never did anything.

So I opened terminal and typed it and this is what came out:
```
patrick@patrick-laptop:~$ nm-applet

** (nm-applet:7044): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7044): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
patrick@patrick-laptop:~$ 
```

Let me know if this helps (^_^)/

---

### Post by mikewhatever on 2008-11-05
double post

---

### Post by mikewhatever on 2008-11-05
The error you get seems to be saying that nm-applet is already running. The notification area is indeed designated by tree tiny lines, and you can check if other icons appear there by starting programs like Rhythmbox or Ekiga. You probably don't need more then one notification area.
Can you please post the command below. It will will show if the nm-applet process is running or not. If you get the output like mine, try killing it with <killall nm-applet> and then starting again with alt+f2 etc.

> ps -e | grep nm-applet

ps -e | grep nm-applet
 5838 ?        00:00:04 nm-applet  <-- my output

---

### Post by Patrick Snyder on 2008-11-05
Rhythmbox and Ekiga both put their icons in the notification area.

```
patrick@patrick-laptop:~$ ps -e | grep nm-applet
 6009 ?        00:00:00 nm-applet
patrick@patrick-laptop:~$ killall nm-applet
patrick@patrick-laptop:~$ ps -e | grep nm-applet
patrick@patrick-laptop:~$ killall nm-applet
nm-applet: no process killed
```

Then I pressed Alt-F2, and typed nm-applet.  Nothing.
So I went back to terminal.

```
patrick@patrick-laptop:~$ ps -e | grep nm-applet
 6589 ?        00:00:00 nm-applet
patrick@patrick-laptop:~$ killall nm-applet
patrick@patrick-laptop:~$ nm-applet

** (nm-applet:6619): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingConnection' / 'type' invalid: 3

 

```

At this point, terminal hangs.  I pressed Ctrl-C.

```
^C** Message: Caught signal 2, shutting down...
patrick@patrick-laptop:~$
```



[B][U]
I don't know if this helps, but...[/U][/B]
I'm running a Dell Inspiron 9300.  I found [this thread]("http://backports.ubuntuforums.com/showthread.php?t=887960") that talked about the BIOS turning the card on and off.

I can get different terminal outputs if I use Fn+F2, which turns my wireless on and off in WinXP.

```
patrick@patrick-laptop:~$ sudo iwconfig eth1
eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

patrick@patrick-laptop:~$ 
```

Then I press the Fn+F2 and get this:

```
patrick@patrick-laptop:~$ sudo iwconfig eth1
eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

patrick@patrick-laptop:~$
```

Either way, typing nm-applet gives the same output as above.

The funny thing is, the 1st time I ran ubuntu it was fine.  So I know that it does work with this hardware.  But then I updated and restarted and it went away.

Also the first time I had an ethernet cord plugged in, it was there again *(although no wireless networks were listed despite about 8 around me)*, and after I restarted *(with the cord still in)* it was gone.

I keep the ethernet cord plugged in for the moment.

---

### Post by mikewhatever on 2008-11-05
Let's see if any of the interfaces are recognized at all.

> sudo lshw -C network

---

### Post by Patrick Snyder on 2008-11-05
```
patrick@patrick-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e1:b2:94
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:3a:ef:53
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
patrick@patrick-laptop:~$ 
```

---

### Post by w.kazimierczak on 2008-11-16
Check if you have still *Notification Area* applet present on your panel (right-click on the panel -> *Add to Panel* -> *Notification Area*).

I've lost several hours looking for Network Manager icon, which has disappeared after an upgrade from Hardy to Intrepid. The network was working correctly (cable connection), just no icon. Finally I found out, that I've removed by accident Notification Area, which is used also by Network Manager.

---

### Post by costre on 2008-11-16
I too had removed the notification area by "mistake", and it never get restarted by default. I added it again, and my mobile broadband icon showed up, along with the update-notification-icon.

All is well, for the moment :)

---

### Post by tedrogers on 2008-11-17
> **mikewhatever said:**
> Hi Patrick, the icon you are missing is not the network manager, but nm-applet. You can try adding it to the notification area by pressing alt+f2 and typing nm-applet. It's important to note that nm-applet lives in the notification area and not on the panel. You may need to add the notification area to the panel fist the same way you've added the network manager icon.

Thank you. That was absolutely killing me when I accidently right-clicked and removed nm-applet from the panel.

I didn't know what it was called and all I could add was that damn horrible network monitor applet instead.

This post saved me from hours of grief!! Thank you.

---

### Post by Doug77 on 2008-11-24
I have the same problem as the original post, Patrick Snyder.  After upgrading from Hardy to Intrepid, the network manager icon disappeared from the taskbar.  Adding a notification area did not work, and I had similar output as him when running nm-applet in the console - it appears to already be running, and I can connect to the internet, but I can't get a list of wireless networks near.

---

### Post by Doug77 on 2008-11-24
A bit of progress here... in my /etc/network/interfaces file, I have this: 


auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual


Now, if I comment out all but the first two lines and reboot, the network manager appears in the taskbar and I can use it!!  It appears that because I set up my wired DSL internet connection manually in Hardy before upgrading, it now doesn't show the network manager in Intrepid.  

It's described in more detail here:  

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/289466)

I'd still appreciate any comments here, particularly what each of those lines in that file I edited actually do!

---

