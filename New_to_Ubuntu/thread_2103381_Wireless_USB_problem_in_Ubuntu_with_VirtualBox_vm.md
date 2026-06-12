---
title: "Wireless USB problem in Ubuntu with VirtualBox vm"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by uusr1 on 2013-01-10
Hello Ubuntu Forum,

Does anyone know how to get TP-Link TL-WN722N wireless USB adaptor working in Ubuntu with VirtualBox as the virtual machine running Ubuntu? 

This adapter works fine in Ubuntu when using VMware as the virtual machine, but fails to work when using VirtualBox. Any suggestions?

When I do a **lsusb** i get this:

```

:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
```but when I do a **ifconfig**, *wlan0* wont show up.

Doing an **ifconfig wlan0 up** shows this:

```

:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```and a **iwconfig**:

```

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```[U]

**Computer Set-up Info**[/U]**:**
Virtual machine: VirtualBox 4.2.6
Guest OS: Ubuntu 12.04.1 LTS
Host OS: Mac OS X 10.8.2
USB Wireless Adaptor: TP-Link TL-WN722N

***Thank you***

---

### Post by squakie on 2013-01-10
Did you install the guest additions to the virtualbox vm?  It should give you access to your USB device.  However, I would have thought that defining the network connection as NAT would have sufficed.

---

### Post by uusr1 on 2013-01-10
Hello Squakie,

Yes, I have Guest Additions on VirtualBox installed. As for defining the network as NAT, I think I did that. In the vm settings I clicked on ***Adapter 2** *then on ***Enable Network Adpater***. I went to the ***Advanced*** section. For the adapter type I have the default ***Intel PRO/1000 MT Desktop***. I didn't see TP-Link or Atheros there.

After doing that I went to the Terminal window and did [B]lsusb

[/B]
```

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n

```My wireless chipset is shown again like last time (Atheros Communication...)
but when I do an **ifconfig** wlan0 isn't there:

```

ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:ef:ae:f1  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:feef:aef1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27006 (27.0 KB)  TX bytes:15753 (15.7 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:a8:18:3a  
          inet addr:10.0.3.15  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fea8:183a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1180 (1.1 KB)  TX bytes:9414 (9.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4705 (4.7 KB)  TX bytes:4705 (4.7 KB)

```and **ifconfig wlan0 up**:

```

ifconfig wlan0
wlan0: error fetching interface information: Device not found

```**iwconfig**:

```

iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

```Adding another adapter only added another **eth** but not a **wlan**.

Thank you for your response.

---

### Post by haqking on 2013-01-10
defining NAT is for the built in network adaptor.

If you are accessing the USB adaptor in the VM the network settings for the VM are redundant.

---

### Post by squakie on 2013-01-10
Not sure I quite understand that - do you mean "built in" as to VirtualBox?  I have wireless on my desktop that attaches via USB and my VM settings to NAT and it works great.  I thought the idea was so that you didn't need to install a driver, but perhaps mine works out of the box and that was why I didn't need a driver?  At any rate, what can we do to help the OP - do they need to install a driver?

EDIT:  Ah, I think I understand what you were saying now ;)  The op shouldn't need a driver because, like my setup, VirtualBox treats NAT as using a virtual ethernet adapter (not wireless) to connect to the host adapter (which can be wireless).  I hope I have that right now.   OP:  don't try to connect with wireless in your VM - just try something like the browser and it should open up, I think.

---

### Post by haqking on 2013-01-10
> **squakie said:**
> Not sure I quite understand that - do you mean "built in" as to VirtualBox?  I have wireless on my desktop that attaches via USB and my VM settings to NAT and it works great.  I thought the idea was so that you didn't need to install a driver, but perhaps mine works out of the box and that was why I didn't need a driver?  At any rate, what can we do to help the OP - do they need to install a driver?

The network setting in virtualbox for the VM are for configuring networking using the HOST OS network adapter. So yes you are right it doesnt need a driver.

To the OP,  What do you want to do, use the HOST network adapter which is USB or use the USB adapter seperately in the VM as standalone?

If the USB adapter you want to use is the one on your HOST then you dont need to do anything with USB in the VM.

In the settings choose NAT if you want it to get its own IP from the host via DHCP, you wont see your USB listed.

In the VM it will be seen as eth0 or eth1.

it wont be seen as a USB device or wireless device in the VM, it will be seen as a hardwired ethx connection, if you want to use the USB as  seperate stand alone wireless device in the VM then you need to choose the device from the devices menu and then you will lose connectivity on your host but gain USB wifi in the VM.

---

### Post by uusr1 on 2013-01-10
> **haqking said:**
> 
it wont be seen as a USB device or wireless device in the VM, it will be seen as a hardwired ethx connection, if you want to use the USB as  seperate stand alone wireless device in the VM then you need to choose the device from the devices menu and then you will lose connectivity on your host but gain USB wifi in the VM.

Thank you all for your responses. I appreciate them much.

Haqking and forum, 

My wireless USB adapter is separate from the host's wireless card. I don't use the USB adapter on my host computer because it won't work on Mac. And yes, I would like to use the USB adapter seperately in the VM as a standalone. I wish for Ubuntu/VirtualBox to recognize my USB adapter as a wireless device. Haqking, when you say, "...you need to choose the device from the devices menu", where is this menu located? Is the menu called ***Adapter Type:*** shown in the attached picture below with the following list in ***Adapter Type*** : 

[I]PCnet-PCI ll (Am79....)
PCnet-Fast lll (AM....)
Intel PRO/1000 MT Desktop (84....)
Intel PRO ......
Intel PRO .....
Paravirtualized Network (virtio-net)[/I]

If this is the case I don't see *TP-Link* or the chipset *Atheros* in that list. Please see the attached pictures of the VirtualBox **Settings**, **Network** menu.

---

### Post by haqking on 2013-01-10
> **uusr1 said:**
> Thank you all for your responses. I appreciate them much.

Haqking and forum, 

I would like Ubuntu/VirtualBox to recognize my USB adapter as a wireless device. Haqking, when you say, "...you need to choose the device from the devices menu", where is this menu located? Is the menu called ***Adapter Type:*** shown in the attached picture below with the following list in ***Adapter Type*** : 

[I]PCnet-PCI ll (Am79....)
PCnet-Fast lll (AM....)
Intel PRO/1000 MT Desktop (84....)
Intel PRO ......
Intel PRO .....
Paravirtualized Network (virtio-net)[/I]

If that is the case I don't see *TP-Link* or the chipset *Atheros* in that list. Please see the attached pictures of the vm setting network menu.

No that is your VM settings, forget that, that is for a HOST adapter.  If you want to use the USB device as standalone then fire up the virtual machine and mount it from devices menu, at the top of the running machine there will be a menu with (machine, view, devices, help)

From devices menu choose USB then choose your adapter this will mount it into the VM

as shown below from a image i found on web as i cant be bothered to load a VM ;-) (obviously you need to choose the USB devices option)

[IMG]https://lh3.ggpht.com/_k8O8x4HeDAo/TQZtvPyPkeI/AAAAAAAAAFc/-gUdFjkaYuk/s1600/boot.png[/IMG]

It might look like this as you said you are on a Mac [http://blog.rahady.com/media/blogs/blog/connect_to_usb_mouse.jpg](http://blog.rahady.com/media/blogs/blog/connect_to_usb_mouse.jpg)

---

### Post by uusr1 on 2013-01-10
I see what you are saying Haqking. Yes, I have done that. That is why when I do an [B]lsusb
[/B]the wireless usb shows up (It is the Atheros one as seen below)

```

 lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n

```but when I do other **ifconfig**,** ifconfig**** wlan0 up**,[B] iwconfig
[/B]my device is not found or functioning, as seen in the previous post in this thread.

###

---

### Post by squakie on 2013-01-10
Try:
 
sudo modprobe ath9k

---

### Post by uusr1 on 2013-01-11
Just tried that. Still not working.

---

### Post by uusr1 on 2013-01-11
Just tried that. Still having the same problem.

---

### Post by squakie on 2013-01-11
I wonder if having the NAT network device makes it such that the wireless isn't working.  Perhaps (if you haven't already) you should either try testing it with the network adapter on the host not plugged in, or by disabling the NAT device in the VM settings.

---

### Post by uusr1 on 2013-01-11
I tried that also. Still nothing unfortunately.

Are any of you using this same device through VirtualBox and have this setup working with the wireless capabilities (**wlan0**)?

---

### Post by squakie on 2013-01-11
Well, if you are trying to access the device directly from the VM and not as a virtual device via the host adapter, then I would suppose you also need a driver.  Why not try connecting with host adapter (NAT) and then trying Additional Drivers and see if anything shows up?  You may need to check network manager and be sure that wired connections is enabled.
 
I'm also curious, if you don't mind, why you aren't just using the host adapter?  I assume you do know it just shares it with the host - the host will still have net access while the VM is using the virtual adapter.

---

### Post by squakie on 2013-01-11
I just thought of something else - I'm just not sure if they apply anymore:
 
- it used to be you had to add a filter in order to use a USB device.  Just putting in a single rule with a name but no conditions used to allow all USB devices to be accessed.
 
- have you enabled the device by clicking on the USB icon on the VM?  I'm not sure if this still applies or not either.
 
Some things have changes since Oracle picked up these things.

---

### Post by squakie on 2013-01-12
Uh, I noticed in the screen shots you posted you are looking at the NAT adapter and it is device 2.  What is listed under device1, 3 and 4?

---

### Post by uusr1 on 2013-01-12
> **squakie said:**
> 
- it used to be you had to add a filter in order to use a USB device.  Just putting in a single rule with a name but no conditions used to allow all USB devices to be accessed.
 
- have you enabled the device by clicking on the USB icon on the VM?  I'm not sure if this still applies or not either.

Hello Squakie,

Yes I have tried tried that also. I added the wirless USB device to the vm filter, but it doesn't make a difference.

Regarding the *Network Settings* for the adapters, I have adapters 3, 4 disabled. Adapter 1 is **Attached to:** ***NAT*** and the **Adapter Type: *Intel PRO...*** My wireless USB isn't found in either of those *Attached To *or *Adapter Type*.

#

---

### Post by squakie on 2013-01-13
Hum, in the screen shot you posted earlier it shows you are looking at device 2.  Does that mean device 1 and device 2 look the same right now?

---

### Post by uusr1 on 2013-01-14
Yea. Well they were the same, but now I also disabled adapter 2 since it didn't make a difference when I used a NAT adapter type. Doing that only gave me a ethx connection, but I also want the wlanx capabilities.

---

### Post by squakie on 2013-01-14
I think I'd try using the ethernet connection and running Additional Drivers - that is if you haven't already.  Don't know if you tried installing the driver for the wireless.  I'm not that great at all of this so I'm running out of ideas.

---

