---
title: "Wireless network connection problem"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by SteveHill on 2008-07-22
Is the D-Link Air-Plus Extreme G DWL-G520 supported by Heron?  If so how do I get it up and running?  This Wireless connector worked fine in the previous version of Ubuntu and in Heron I can see my wireless network but have no way to get to it. Thank you for any help.

Steve

---

### Post by northern lights on 2008-07-22
What exactly do you mean by "get to it"? I.e. at what point of the connecting process does what happen?

Can you also post the output of ```
ifconfig
```
and ```
route -n
```

---

### Post by SteveHill on 2008-07-23
by "get to it" I mean that when I right click the network icon and edit wireless networks I can see my wireless network name in the pop up window but for some reason I still have no network connection.  When I click manual configuration I have a Wired connection and a pont to point connection but no wireless to choose from.

my ifconfig is:
eth0  Link encap:Ethernet     HWaddr 00:0b:db:29:cl:30
      UP BROADCAST MULTICAST MTU:1500  Mertic:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo    Link encap: Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:570 errors:0 dropped:0 overruns:0 frame:0
      TX packets:570 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:28500 (27.8 KB)  TX bytes:28500  (27.8 KB)
route -n:
Kernal IP routing table
Destination   Gateway   Genmask   Flags Metric Ref   Use Iface

(I manually typed the ifcong and route -n)

Thanks,
Steve

---

### Post by northern lights on 2008-07-23
> **SteveHill said:**
> (I manually typed the ifcong and route -n)Jesus Murphy! You can copy from the terminal. Mark with the mouse or cursor keys while holding "Shift", then press "Shift+Ctrl+C" to copy or selct "Copy" from the "Edit" menu.

When you navigate to "System > Administration > Network", what do you see?
Is there a "wireless connection"?
And can you check its properties?

Can you also post the output of ```
sudo lshw -C network
```--> your "ifconfig" showed no wireless either, wanna see whether the device is up and what it is.

---

### Post by SteveHill on 2008-08-02
Since I can not get on the internet with Heron I am using my Mac to get on this forum site. That's why I am typing it out.

There is no wireless connection in the Network Settings.  Just Wired Connection and Point to point connection.  What is confusing is that if I right click what looks like a monitor icon at the top of the screen that says "no network connection" (when my mouse arrow hovers over it) and then click on "edit wireless networks" I can see my wireless network in the window that pops up.  Anyway, when I typed in what you asked here is what the terminal showed:

steve@Ubuntu:~$ sudo lshw -c network
[sudo] password for steve: 
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

This time I copied the info to a thumb drive. Much better.
I hope this is helpful. 

Steve

---

### Post by northern lights on 2008-08-02
> **SteveHill said:**
> Since I can not get on the internet with Heron I am using my Mac to get on this forum site. That's why I am typing it out.

Don't you have a USB flashdrive (stick) or something? External HDD or a CD burner in the comp you can transfer with? Copy the output to a text file.

As for the output that you typed - I'm sorry to tell you this given you typed it - that's an error message...

> **SteveHill said:**
> 
options can be
	-class CLASS    only show a certain class of hardware
	-[COLOR="Red"]C[/COLOR] CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information 


The shell is case-sensitive. It should have been > **northern lights said:**
> ```
sudo lshw -C network
```
This```
sudo lshw -class network
```
would have worked also.

---

### Post by SteveHill on 2008-08-03
I got a USB thumb drive.  It is much easier than typing.
Here is what I have for your request:

steve@Ubuntu:~$ sudo lshw -class network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: C.P. Technology Co. Ltd
       vendor: C.P. Technology Co. Ltd
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:29:c1:30
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
steve@Ubuntu:~$ 

By the way, is there someplace that lists the wireless cards that are compatible with Heron?  Maybe I should just get one of those.
Steve

---

### Post by ingeva on 2008-08-03
> **SteveHill said:**
> Is the D-Link Air-Plus Extreme G DWL-G520 supported by Heron?  If so how do I get it up and running?  This Wireless connector worked fine in the previous version of Ubuntu and in Heron I can see my wireless network but have no way to get to it. Thank you for any help.

Steve

I have the G510. Worked right out of the box.

---

### Post by northern lights on 2008-08-03
> **SteveHill said:**
> By the way, is there someplace that lists the wireless cards that are compatible with Heron?  Maybe I should just get one of those.
Steve
[Linux WLAN support]("http://linux-wless.passys.nl/query_alles.php")

It might also be good to know [http://linux-drivers.org]("http://linux-drivers.org")

Your 'lshw' output suggests your WLAN device is physically not correctly installed. There is a number of devices that are tough to get to work, but if it worked in previous Ubuntu releases, it should do so now also.

Plus, according to the above document, the DWL-G520 is supported. You'd need the madwifi driver, but, ideally it should have worked oob.

Run ```
sudo apt-get install madwifi
```but it should have appeared in the output (run again to verify, maybe) and have worked...

---

### Post by lisati on 2008-08-03
> **SteveHill said:**
> by "get to it" I mean that when I right click the network icon and edit wireless networks I can see my wireless network name in the pop up window but for some reason I still have no network connection.  When I click manual configuration I have a Wired connection and a pont to point connection but no wireless to choose from.

my ifconfig is:
eth0  Link encap:Ethernet     HWaddr 00:0b:db:29:cl:30
      UP BROADCAST MULTICAST MTU:1500  Mertic:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo    Link encap: Local Loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:570 errors:0 dropped:0 overruns:0 frame:0
      TX packets:570 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:28500 (27.8 KB)  TX bytes:28500  (27.8 KB)
route -n:
Kernal IP routing table
Destination   Gateway   Genmask   Flags Metric Ref   Use Iface

(I manually typed the ifcong and route -n)

Thanks,
Steve
You mentioned right-click on the icon. Are you able to connect when you left-click on the icon and then on the name of your network?

---

### Post by northern lights on 2008-08-03
This reminds me, even 'ifconfig' only shows the loopback adapter and an ethernet device...

---

### Post by SteveHill on 2008-08-03
Here is what I get with trying to install madwifi:


steve@Ubuntu:~$ sudo apt-get install madwifi
[sudo] password for steve: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package madwifi
steve@Ubuntu:~$ 

As to the question: "Are you able to connect when you left-click on the icon and then on the name of your network"? All I get is is a grayed out wired network and manual configuration. This takes me to the network settings that I have mentioned in previous posts.  

Steve

---

### Post by northern lights on 2008-08-03
Navigate to "System > Administration > Software Sources" and select every repository but 'backports' and 'proposed'. Run again. Do an update first.

```
sudo apt-get update
sudo apt-get install madwifi
```

---

### Post by SteveHill on 2008-08-04
Due to not having a wireless connection to the internet for my Ubuntu Heron I can not do any updates.  Sorry..

Steve

---

### Post by ingeva on 2008-08-05
> **SteveHill said:**
> Due to not having a wireless connection to the internet for my Ubuntu Heron I can not do any updates.  Sorry..

Steve

Get a cable! :)

Oh, this is my post no. 100. Should we celebrate? :)

---

### Post by northern lights on 2008-08-05
> **ingeva said:**
> Get a cable!
+1

Theoretically, you could add the CD to the sources or download a .deb, but dude, hook the laptop up with a cable until the wireless works.

---

### Post by bobnutfield on 2008-08-05
> There is no wireless connection in the Network Settings. Just Wired Connection and Point to point connection. What is confusing is that if I right click what looks like a monitor icon at the top of the screen that says "no network connection" (when my mouse arrow hovers over it) and then click on "edit wireless networks" I can see my wireless network in the window that pops up. Anyway, when I typed in what you asked here is what the terminal showed:

Unless, I am missing something (I could be), the wireless card is receiving a transmission from the router as the network name is "seen" in the drop down from the network icon.  I believe it might be a matter of configuration.

Type

> ifconfig -a

This will show all network devices the system recognizes even if they are not up.  If it shows up, it can be configured on the command line.

---

### Post by Kevbert on 2008-08-05
What you could do is put the Hardy CD in the drive, browse to pool, main, n, ndiswrapper and double click on each of the .deb files in turn in this directory to install ndiswrapper and utils.  Next you want to go up one directory and go into the ndisgtk directory and double click on the .deb file there.  The file that you've just installed in the graphical front end for ndiswrapper.  This file can be found under System-Admin-Windows Wireless Drivers.  You can now use your windows drivers by browsing to them using this program.

---

### Post by SteveHill on 2008-09-21
Well, that's about it.  I think Ubuntu is a fine OS system for some but not for me. This is just too unnecessarily complicated.  Maybe sometime in the future I will try a newer version and see if it will work.  Please, Ubuntu just make a simple, full featured down loadable OS.  Until then, thanks for trying to help.  Let me know if, sometime in the future, Ubuntu does make such an OS.  Thanks again.

Steve

---

