---
title: "hp dv6000 amd64 nvidia broadcom"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by yragrelluf on 2008-06-16
I would like to start a place to share our experiences with ubuntu on our hp laptops. I knew nothing when I started using ubuntu hardy a month or so ago but I managed getting my laptop running sooooooo much better than when it still had vista (completely removed). If anybody has anything to say or ask about their hp laptops, Id like to make this the place to talk. I also have created an almost perfect liveCD/install disc for this specific platform, I just need to figure out how to make it available for download.)

---

### Post by yragrelluf on 2008-06-24
bump

---

### Post by johnnie j on 2008-08-06
HI,

I'm new to the Ubuntu and I have a dv6000 series, dv6824ca,. How did you get wireless and webcam to work?

And congrats on your success.

John

---

### Post by Friccy on 2008-08-06
Hi there!
I'm glad that I found you and hope that you can help me to run Ubuntu on my HP Pavilion dv6645 laptop (AMD64, Broadcom, NVidia).
I have a fresh install of Hardy and have a problem with the display.
It is so "dim", dark like it is on a power saving mode. 
I have tried to adjust it like in Vista, from the Power Management, but there is no way to do it.
I could use any other suggestion to make Ubuntu faster and much nicer than it is now and than Vista was.
Thanks!

---

### Post by johnnie j on 2008-08-06
Hi Friccy,

I've noticed mine is a bit dark, as well, but for me the trouble is with the webcam and wireless. Mines a dv6824ca.

Good luck with your trouble,

John

---

### Post by SlalomMan on 2008-08-06
Friccy and johnnie j:
Do either of your laptops have a hardware wireless control? My Toshiba has a function key (fn) that, when used with F6 or F7, increases or lowers the brightness. Maybe that will help.

johnnie j:
Do you know what wireless card you have? If you do, you can use a program called ndiswrapper that uses the windows wireless driver for the card to get it to work. Here's what I would do:

1. Find out your wireless card model: You can run lspci in the terminal to list your devices, and look for one that says "Wireless" in it. 

2. Go either to HP's site or your wireless card's manufacturer's site to look for the windows driver. (The Vista driver should work but I know Vista has problems with drivers so I would go with the XP driver)

3. Install ndiswrapper. I would also install ndisgtk which is a graphical frontend for ndiswrapper; if you're not comfortable with the terminal, you should get this.

Run ```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```

or ```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
if you don't want the graphical interface.

4. Install the drivers. If you installed ndisgtk you can find it in system->administration->windows wireless drivers. Then you just browse for the .INF file in the driver folder you downloaded. If it works, it will tell you that it installed, and say "module present" or something similar. There may be more than one .INF file; if so, you just have to try until you find the right one.
If you didn't install ndisgtk, I think the syntax is "ndiswrapper driver.inf" but I'm not sure.

5. You might have to blacklist your old drivers; To do this you would edit /etc/modprobe.d/blacklist and add "blacklist driver", replacing "driver" with your old driver's name. 

6. Run "modprobe ndiswrapper" to use the new driver; and a restart should fix the wireless.

I had this problem a few days ago; hope this helps!

---

### Post by johnnie j on 2008-08-06
Hi SlalomMan,

Everything that you said worked perfectly, but it appears that HP has Microsoft the great favour of packaging their Vista drivers as .exe. No .inf to be found.

Your help is greatly appreciated though.

Yet another reason to never buy MS or HP again. I don't think companies that behave like this realize that the general population is recognizing that we're being ripped off and will find viable alternatives.

There are lots of alternatives to HP, Microsoft definately has lock-in but HP not so much, therefore they should tread more lightly.

Thanks,

John

---

### Post by SlalomMan on 2008-08-07
John, what wireless card do you have? I'll try to find the INF drivers for it; the drivers for my Intel 4965 wireless card came with a .exe, but there were a few .INF files in the zip folder; I'm assuming the .exe was provided so that windows users could easily install it/to install a wireless manager from intel.

Another alternative would be a program called "cabextract". I believe it might be installed by default in Ubuntu. Some .exe files just extract files. Cabextract gets the files out, so if the .exe installs the drivers, and no INF files are to be found, chances are that the .inf files are packaged in there. All you have to do is run "cabextract driver.exe", where driver.exe is the file that you downloaded.

Hope that helps.

---

### Post by Friccy on 2008-08-09
Hi SlalomMan!
I have the posibility to adjust it like you have suggested. Thanks!
But I was thinking on a way to set it for good. With the Fn key I have to adjust it every time I start or restart the laptop. 
If there is no other way, that's it! I will use this method!

---

### Post by SlalomMan on 2008-08-09
Friccy, I may have found a solution for you.

Open up the configuration editor (it's in "System Tools" for me, but you can just hit Alt+F2 and run "gconf-editor") and navigate to apps->gnome-power-manager->backlight.

It seems that you can mess with the default settings for brightness here. Changing the "brightness_battery" option should work, it will probably even work after a restart. Hope this helps.

---

### Post by Ms8 on 2008-11-16
I had everything working wonderfully in Hardy.  I got my wireless to work using this:

sudo apt-get install b43-fwcutter
sudo /usr/share/b43-fwcutter/install_bcm43xx_fwcutter_firmware.sh
sudo etc/init.d/dbus restart

I had no other issues.

Liking shiny new things I decided to upgrade to Intrepid.  The upgrade failed at "checking battery status", the screen flickered and instead of going ahead and booting after several loops through "waiting for 2 mins", it just continued looping, never booting.

I tried Intrepid from the ISO and again it got caught at "checking battery status", screen flicker and eternal looping.

So, I loaded Ubuntu 8.04.  It loaded fine and works fine except I can't get the wireless to work now.

My wireless is there, it loaded the wireless drivers and firmware through the third party and proprietary drivers manager at the end of the install.

When I try to enable it using Network Manager I get:

ifconfig wlan wlan: error fetching interface information: Device not found

marmie@ubuntu:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:24:04:97:a2  
          inet addr:192.168.2.110  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe04:97a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5492407 (5.2 MB)  TX bytes:442054 (431.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:1a:73:32:13:61  
          inet6 addr: fe80::21a:73ff:fe32:1361/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:844
          TX packets:0 errors:152 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:73:32:13:61  
          inet addr:169.254.3.200  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148700 (145.2 KB)  TX bytes:148700 (145.2 KB)

marmie@ubuntu:~$ lshw -C Network

 *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:32:13:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:04:97:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.2.110 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

So my device is there but I can't get the network manager to configure it.

Why is it that an upgrade to the newest kernel, can't also include seemless wireless upgrade?!

Any help would be greatly appreciated.

---

### Post by Ms8 on 2008-11-17
Update to last post:

I reloaded Ubuntu 8.04.  I installed my wireless using

```
sudo apt-get install b43-fwcutter
sudo /usr/share/b43-fwcutter/install_bcm43xx_fwcutter_firmware.sh
sudo etc/init.d/dbus restart


```

I configured my network and connected without an issue.  I have not done any of the updates yet.  Which Kernel files and headers do I need to "lock" to allow my wireless to continue?

---

