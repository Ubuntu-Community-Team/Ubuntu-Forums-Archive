---
title: "Playing around with Live CD, how do I connect to a wireless network??"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by andybob on 2008-04-29
Hey all:

Finally got a Hardy image burnt to a CD and I have been playing around with it for a bit but I have a problem.  I cannot figure out how to connect to my wireless network.  I used the help features and did the -C network code in the terminal and the wireless card is working but I don't know how to connect to the network.  What do I have to do??

Thanks,


Andybob

P.S. Other than the network problem I found it to be nice and easy to run, it will take some time to get used to but it is pretty cool...

---

### Post by superprash2003 on 2008-04-29
you should see an internet symbol(a monitor kinda box) at the top right corner. .if you click on it.. it should show the available networks.. then choose your network there.. or you can go to system->administration->network and go to your wirleess card properties and then choose the network in the ESSID option

---

### Post by andybob on 2008-04-30
Thanks for the help but I did try that.  It doesn't even show there is a network in range.  It is sounding like I need to update the driver.


Andybob

---

### Post by jatiesch on 2008-04-30
whats ur *iwconfig* output

---

### Post by andybob on 2008-04-30
> **jatiesch said:**
> whats ur *iwconfig* output

I will post it later on today.  I will have to connect using an ethernet cable so I can post it on here.  Right now I am on Windows ding some Excel Work but I will give it a try later.

Thanks...


Andybob

---

### Post by master5o1 on 2008-04-30
Firstly, what wireless card? Because it may not have the driver in the LiveCD session (meaning no chance to wifi in LiveCD).

Else...I need to think :P

---

### Post by andybob on 2008-04-30
Here is a screen shot of the device manager.  Looks like the one on the right is the wireless and the one on the left is the ethernet.  They are both a Broadcom chip though.

[IMG]http://i51.photobucket.com/albums/f391/andybob1001/Wireless.jpg[/IMG]


Andybob

---

### Post by master5o1 on 2008-04-30
Hmm.. Broadcom. I can't remember what to do with them. I know there is a broadcom 43XX driver by default...

But if it requires proprietary drivers then you should connect the liveCD to the ethernet and check the Restricted Drivers Manager.

Might have it in there...

Although, you said that there was a 0% reading on the SSID right? I remember having that a while ago on my RealTek based wlan card...

---

### Post by andybob on 2008-04-30
> **master5o1 said:**
> 

Restricted Drivers Manager.

Although, you said that there was a 0% reading on the SSID right? I remember having that a while ago on my RealTek based wlan card...

What is the Restricted Driver Manager under in Ubuntu?

As for the SSID I will post the *iwconfig* when I can get to it.


Andybob

P.S. Thanks for the help.

---

### Post by master5o1 on 2008-04-30
The Restricted Driver Manager is for enabling the use of proprietary/non-free drivers, such as Nvidia's 3D drivers and many wireless drivers.

System > Administration > Hardware Drivers


*It used to be called teh Restricted Driver Manager but now renamed to Hardware Drivers.

---

### Post by andybob on 2008-04-30
Thanks Man, you da bomb.


Andybob

---

### Post by master5o1 on 2008-04-30
> **I cannot figure out how to connect to my wireless network.** I used the help features and did the -C network code in the terminal and _the wireless card is working_ but **I don't know how to connect to the network.** What do I have to do??



Wait a minute: I click on the network monitor applet (top gnome panel to the right) and select which Wifi I want to connect to... add the wpa/wpa2/wep key and I'm done!

You can also do static IPs by going into System > Administration > Network and firstly clicking 'unlock' and then editing the wireless settings so it has not got 'roaming mode enabled' and is Static (or DHCP).

---

### Post by master5o1 on 2008-04-30
> **andybob said:**
> Thanks Man, you da bomb.

Andybob


After two years of using Linux/Ubuntu I now feel ~confident giving advice back.

---

### Post by andybob on 2008-04-30
[QUOTE=master5o1;4843598]Wait a minute: I click on the network monitor applet (top gnome panel to the right) and select which Wifi I want to connect to... add the wpa/wpa2/wep key and I'm done!
[QUOTE]

There enlies the problem.  There isn't a network listed to connect to.


Andybob

---

### Post by lswest on 2008-04-30
well, you can install the firmware for the card via this site: [http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)  or else you can install Ubuntu and use ndiswrapper to install the windows drivers.  Reason it "seems" to work is because Hardy recognizes the card, but can't install the driver without the firmware.

---

### Post by andybob on 2008-04-30
Where do you get the ndiswrapper?

---

### Post by master5o1 on 2008-04-30
ndiswrapper:

System > Administration > Synaptic Package Manager : search "ndiswrapper" -> mark all three (ndiswrapper-common, ndiswrapper-utils, ndisgtk) and apply... enjoy. Internets required.

---

### Post by andybob on 2008-04-30
> **master5o1 said:**
> ndiswrapper:

System > Administration > Synaptic Package Manager : search "ndiswrapper" -> mark all three (ndiswrapper-common, ndiswrapper-utils, ndisgtk) and apply... enjoy. Internets required.

Thanks a lot, when I get the chance I will connect via ethernet and give that a shot.  If it works and I can use the wireless I am going to install Ubuntu.

---

### Post by master5o1 on 2008-04-30
Remember you still have two options: The 'native' Broadcom 43xx driver from that site that lswest suggested, or Ndiswrapper.

Personally I would always go for the Linux based driver as Ndiswrapper is wrapping the windows driver.

---

### Post by Stefanie on 2008-04-30
> There enlies the problem.  There isn't a network listed to connect to.


Andybob

can't you select "connect to other wireless network" and type the exact name of your network? this is what i did when my wireless network disappeared from the list.

---

### Post by andybob on 2008-04-30
> **master5o1 said:**
> Remember you still have two options: The 'native' Broadcom 43xx driver from that site that lswest suggested, or Ndiswrapper.

Personally I would always go for the Linux based driver as Ndiswrapper is wrapping the windows driver.

The problem is installing the Linux based driver might be a little too advanced for me to start with.  If I could do it I wure would.

Again, thanks for all your help...



Andybob

---

### Post by master5o1 on 2008-04-30
[QUOTE=http://www.linuxwireless.org/en/users/Drivers/b43#fw-b43-old]*You are using the b43 driver from linux-2.6.24*

If you are using the b43 driver from linux-2.6.24, follow these instructions.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
```

Use version 4.80.53.0 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place.[/QUOTE]

The following is the driver to be released with the 2.6.25 Linux kernel. If you want it, do this instead.

[QUOTE=http://www.linuxwireless.org/en/users/Drivers/b43#fw-b43-new]You are using the b43 driver from linux-2.6.25 or newer

Follow these instructions if you are using the b43 driver from linux-2.6.25 or compat-wireless-2.6, or from any current GIT tree.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
```

Use version 4.150.10.5 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. [/QUOTE]

I think there is a package for this somewhere because otherwise it doesn't get updated easily.

---

### Post by master5o1 on 2008-04-30
Vendor Product	Broadcom Chip	PCI Product	PCI Subvendor	PCI Subsystem

Dell	TrueMobile 1370 Mini-PCI Card	4318	0x4318	0x1028	0x0005

[http://www.linuxwireless.org/en/users/Drivers/b43/devices](http://www.linuxwireless.org/en/users/Drivers/b43/devices)
(select 4318 from the 'broadcom chip' drop down...)

---

### Post by andybob on 2008-04-30
iwconfig output:

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Andybob

P.S. What do I do? lol

---

### Post by andybob on 2008-04-30
Ok, did the ndiswrapper thing now and in the Gnome there is an icon saying new drivers to update, I am guessing I click on that and say update.

Andybob

---

### Post by andybob on 2008-04-30
Well, I updated the drivers and it froze on me so I had to shut it down.  I am back on Windows now.  It said it was installing the b34-fwcutter and when it got done and when I closed the install window it crashed.  What should I do?


Andybob

P.S.  After I did the ndis wrapper it still didn't show there was a network in range.

---

### Post by fraser_m on 2008-04-30
```
sudo apt-get install b43-fwcutter
```
into the terminal. (Apps>Accessories>Terminal)

I had to do this this morning...

Follow the instructys to the end then try connecting to the WiFi. It should be all right without a restart.

Oh, and you'll need to be connected to the Ethernet...

---

### Post by andybob on 2008-04-30
> **fraser_m said:**
> ```
sudo apt-get install b43-fwcutter
```
into the terminal. (Apps>Accessories>Terminal)

I had to do this this morning...

Follow the instructys to the end then try connecting to the WiFi. It should be all right without a restart.

Oh, and you'll need to be connected to the Ethernet...

Alright, thanks...I will give that a try when I get home, I'm in class right now and I don't have my Hardy Heron copy with me.


Andybob

---

### Post by andybob on 2008-04-30
> **fraser_m said:**
> ```
sudo apt-get install b43-fwcutter
```
into the terminal. (Apps>Accessories>Terminal)

I had to do this this morning...

Follow the instructys to the end then try connecting to the WiFi. It should be all right without a restart.

Oh, and you'll need to be connected to the Ethernet...

Alright, I did that and this is the output it gave me.

> ubuntu@ubuntu:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/15.8kB of archives.
After this operation, 102kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 98223 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...
--16:20:03--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652,866 (638K) [application/x-object]

100%[====================================>] 652,866       23.80K/s    ETA 00:00

16:20:22 (33.53 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--16:20:22--  [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
           => `broadcom-wl-4.80.53.0.tar.bz2'
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904,072 (883K) [application/x-tar]

100%[====================================>] 904,072       37.93K/s    ETA 00:00

16:20:49 (41.77 KB/s) - `broadcom-wl-4.80.53.0.tar.bz2' saved [904072/904072]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
broadcom-wl-4.80.53.0/
broadcom-wl-4.80.53.0/kmod/
broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
broadcom-wl-4.80.53.0/kmod/wl_apsta.o
broadcom-wl-4.80.53.0/nas
broadcom-wl-4.80.53.0/wl
broadcom-wl-4.80.53.0/WHERE_FROM
broadcom-wl-4.80.53.0/libbcmcrypto.so
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta_mimo.o
  version    :  351.126
  MD5        :  722e2e0d8cc04b8f118bb5afe6829ff9
Extracting b43/ucode4.fw
Extracting b43/ucode5.fw
Extracting b43/ucode11.fw
Extracting b43/ucode13.fw
Extracting b43/pcm4.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/lp0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/a0g1bsinitvals13.fw

Now what should I do?


Andybob

---

### Post by andybob on 2008-04-30
Here is the lspci output:

> lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

It looks like at the bottom it sees that there is a controller, should be able to connect now?  It still shows no wireless extension under iwconfig.


Andybob

---

### Post by master5o1 on 2008-04-30
> wlan0 IEEE 802.11g ESSID:""
Mode:Managed Channel:0 Access Point: Not-Associated
Tx-Power=0 dBm
Retry min limit:7 RTS thrff Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

wlan0 = has wireless extensions.

Hmm... I don't know whether that finished or not but I suppose it has.
However if you tried it and it isn't working then I don't know.

---

### Post by andybob on 2008-04-30
I don't know either, I tried for about an hour an 45 minutes and I couldn't get it to connect.  I'd really like to run Ubuntu but if I can't figure out the wireless I'm not sure if I will do it.  The things I have tried are ndiswrapper and the sudo apt-get install b43-fwcutter.  If I try to connect to the network I type in the name, and then try the network key and it gos for a while and then by the little monitor in the Gnome panel it shows a little exclamation point in a orange triangle.

Any more help is appreciated.


Andybob

---

### Post by doorknob60 on 2008-04-30
Did you set up ndiswrapper to use a Windows driver? I think there should be a entry In System>Administration called Windows Wireless Drivers or something like that. Give it a Windows driver to use and try that. I'll try to find a driver.

EDIT: THIs driver should work, sorry for the crappy host: [http://rapidshare.com/files/111649684/BCM4318.tar.gz.html](http://rapidshare.com/files/111649684/BCM4318.tar.gz.html)

---

### Post by andybob on 2008-04-30
> **doorknob60 said:**
> Did you set up ndiswrapper to use a Windows driver? I think there should be a entry In System>Administration called Windows Wireless Drivers or something like that. Give it a Windows driver to use and try that. I'll try to find a driver.

EDIT: THIs driver should work, sorry for the crappy host: [http://rapidshare.com/files/111649684/BCM4318.tar.gz.html](http://rapidshare.com/files/111649684/BCM4318.tar.gz.html)

If I do the ndiswrapper and I find the Windows driver that is for my Broadcom card should that work?  I am pretty sure I cna get the driver from Dell.com.  How would I install it?

Thanks,


Andybob

---

### Post by andybob on 2008-05-01
**T**o
**T**he
**T**op

---

### Post by serfcx on 2008-05-01
Have a look at wicd.
You will need to be connected to the internet to get to the repos, use synaptic to search for "wicd" and then install. Launch and it should be able to connect to your wireless - It worked for me when I had problems, but I wasn't using the same chip as you.
Maybe will work.

---

### Post by Adbru on 2008-05-01
*I click on the network monitor applet (top gnome panel to the right) and select which Wifi I want to connect to... add the wpa/wpa2/wep key and I'm done!*

Hi Guys,
Quick question....
Does 8.04 support WPA by default ??
I am going nuts trying to get it to work for me under 7.10 (been through most of the posts already....)

Thanks
Adbru

---

### Post by sam_delta on 2008-05-01
hello andybob, 

if your using a live cd:
the procedure on installing b43-fwcutter on your post 29 went alright, but if your running as live cd session, the possible problem here is that as far as i know, after installing/updating b43-fwcutter you have to restart your computer, but if your running as live cd session, when you restart pc, you reset to live cd defaults.
id recomend to install into hard drive, double boot or something and try to get it working

sam

---

### Post by andybob on 2008-05-02
> **sam_delta said:**
> hello andybob, 

if your using a live cd:
the procedure on installing b43-fwcutter on your post 29 went alright, but if your running as live cd session, the possible problem here is that as far as i know, after installing/updating b43-fwcutter you have to restart your computer, but if your running as live cd session, when you restart pc, you reset to live cd defaults.
id recomend to install into hard drive, double boot or something and try to get it working

sam

Thanks Sam, thats what I am going to do.  I just got a external HD last night so I have been backing up stuff just in case.  I will install it whenever I get the chance.

Thanks for the reply,


Andybob

---

### Post by sam_delta on 2008-05-02
alright, if you have any questions while the installation or after it, we'll be here 

sam

---

