---
title: "I installed the wrong version of Ubuntu and cannot get my wireless working"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by kc2045 on 2008-09-15
Hi

This is my first linux experience that I am aware of.. exciting!

I installed the 64 bit version of Ubuntu Hardy Heron yesterday on my new Toshiba Satellite A205. I should have installed the 32bit.

I am not able to see any wireless networks with my realtek rtl8187b card. 

This is on the list of supported cards.

After googling I have found a few different possible solutions for the Wireless card and I'm having trouble installing the various drivers and wrappers and using commands. How do I know which one to continue investing hours of time with and should I uninstall the 64 bit version and reinstall the 32 bit? 

I can't get the make and install commands to work.

Am I condemned to a life of Vista?

Please help.

:guitar:

---

### Post by Tatty on 2008-09-15
I would suggest sticking with 64bit for now.  I have been using x64 on two of my machines for a long time now with no problems.

If you could post a link to the guide you are following, that could help speed up the resolution of this.

---

### Post by Tatty on 2008-09-15
Firstly, have you checked in the System->Administration->Hardware Drivers manager?

Second, have you tried following this?

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

---

### Post by phidia on 2008-09-15
To get make to work you need to install build-essential > sudo apt-get install build-essential 
You didn't say but if your card needs ndiswrapper to work you would likely have the same steps with 32 bit. 
I am a user and proponent of 64 bit.

There is a guide for your wireless card [here]("http://ubuntuforums.org/showthread.php?t=792092&highlight=realtek+rtl8187b"). I'm not sure though if you need the 64 bit driver for your card.
OK I found a [thread]("http://ubuntuforums.org/showthread.php?t=848591&highlight=realtek+rtl8187b") that lists the driver & howto for the 64 bit driver-hope that helps.

---

### Post by kc2045 on 2008-09-15
Ok!

I am trying out the advice of a post I found that said

There is a native install for the rtl8187 driver.... rtl-wifi.sourceforge.net
Do the mac80211 install.

From this thread
[http://ubuntuforums.org/showthread.php?t=546663](http://ubuntuforums.org/showthread.php?t=546663)

---

### Post by kc2045 on 2008-09-15
> **Tatty said:**
> Firstly, have you checked in the System->Administration->Hardware Drivers manager?

Second, have you tried following this?

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

Yes, when I view the Hardware Drivers wireless does not come up as an option. I am able to connect to the internet if I am wired though.

I did see that wifi doc, but I was hoping to be able to use WPA if possible.

Thank you for all responses and I will visit the other solutions now!

---

### Post by kc2045 on 2008-09-15
> **Tatty said:**
> Firstly, have you checked in the System->Administration->Hardware Drivers manager?

Second, have you tried following this?

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

I have decided to try this but am getting a message that E: Couldn't find package patch.

I have been messing around with commands that I do not understand.. perhaps this could be a problem?

---

### Post by panhandle on 2008-09-15
I have not heard of native support for this chipset. As far as I know, it is blacklisted.

Though you have not posted the tutorial you followed (did I miss it?), consider the following:

[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

The 8187b can be a pain, but persevere and it will get going!

---

### Post by Tatty on 2008-09-15
> **kc2045 said:**
> I have decided to try this but am getting a message that E: Couldn't find package patch.

I have been messing around with commands that I do not understand.. perhaps this could be a problem?

Where are you getting this message?  After which commands?

---

### Post by kc2045 on 2008-09-16
I have tried three different methods and it seems that I get an error every time i try to sudo apt-get anything.  

For example when i follow this
[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

I get an error after
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

When I try to get make to work I get this:

kendra@SparkyII:~$ sudo apt-get build-essential
E: Invalid operation build-essential

---

### Post by MegaJim on 2008-09-16
> **kc2045 said:**
> 
kendra@SparkyII:~$ sudo apt-get build-essential
E: Invalid operation build-essential

you missed out the install operation: sudo apt-get *install* build-essential

---

### Post by kc2045 on 2008-09-16
ok!! i am moving forward! i tried sudo apt-get install build-essential instead of apt-get build-essential and also checked my spelling with sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

YES!

---

### Post by kc2045 on 2008-09-16
I am having difficulty at the last step after installing the driver. I am receiving the message in the Wireless Network Driver

Hardware present:Now

Following this guide:
[http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

I have confirmed that I have the 8197 card:
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.

I have installed ndiswrapper using:
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk

I have downloaded the Realtek driver and edited the inf file in the Windows98 directory from: 
[http://drivers.softpedia.com/get/NETWORK-CARD/REALTEK/Realtek-RTL8187B-Driver-6106302082007-WHQL.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/REALTEK/Realtek-RTL8187B-Driver-6106302082007-WHQL.shtml)

The part I edited in the inf file looks like this:
;;****************************************************************************

;; IDs for 98SE/ME/2K/XP

;;****************************************************************************

[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

Under system > admin > Windows Wireless Drivers I have clicked the Install Driver button, found net8187b.inf in the Windows98 directory and am now getting the message that the hardware is not found.

Perhaps something I have previously installed is conflicting?

Thanks to everyone here for help with this!

---

### Post by panhandle on 2008-09-17
post the results of the following commands:

```
lshw -C network
```

```
iwconfig
```

```
ifconfig
```

---

### Post by kc2045 on 2008-09-18
> **panhandle said:**
> post the results of the following commands:

```
lshw -C network
```

```
iwconfig
```

```
ifconfig
```



Ok, here are the results. Thank you so much, and thanks everyone for all of your help with this! I really appreciate it.

lshw -C
---------------------------------------------
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
-------------------------------------------------------
iwconfig
-------------------------------------------------------
lo        no wireless extensions.

eth0      no wireless extensions.



-------------------------------------------------------
ifconfig
-------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:91:a0:9d  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe91:a09d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:518569 (506.4 KB)  TX bytes:48347 (47.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1726 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86300 (84.2 KB)  TX bytes:86300 (84.2 KB)

---

### Post by phidia on 2008-09-18
If the driver was installed correctly then the command "ndiswrapper -l" would return the driver for example from my system: 
> phidia@neverland:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)


Did you insert the windows inf file with "sudo ndiswrapper -i (name-of-windows-driver)"?

---

### Post by kc2045 on 2008-09-18
Oh gosh I am really close!

I am using ndiswrapper and I have installed the wifi radar. I can see all of the wireless networks in my area!!!

Usually I will use open networks but today at my office I am trying to connect to their secured network. 

It is my understanding that this is possible with WiFi radar.

I have found my office wireless internet network, clicked edit, set mode and channel to "auto", entered they key, and set security to be restricted.

I click connect.

It will not connect.

Also, does WiFi Radar indicate which networks are open and which are not? It is hard to tell now because there aren't any open networks in this area.

Thanks again for helping with my first ubuntu experience everyone... very very much.

---

### Post by kc2045 on 2008-09-18
I restarted and now EVERYTHING WORKS.

hallelujah hallelujah hallelujah hallelujah hallelujah hallelujah hallelujah hallelujah hallelujah hallelujah hallelujah hallelujah  thanks for your help and patience!!!!!!

---

### Post by billgoldberg on 2008-09-18
Mark your thread as solved please.

It will help people like me who read the whole thread to try to assist only to found out its already been solved.

---

