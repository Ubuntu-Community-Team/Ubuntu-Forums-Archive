---
title: "Networking icon disappeared"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-03-26
Is there a Terminal entry that will bring back the networking icon that vanished when I accidentally hit the "disconnect wired network" button in the networking drop-down menu?  This is a Dell XPS Studio running 12.04. No dual boot, just 12.04.  

On bootup, I get a momentary notice that I need to download a driver and firmware for the network card in this computer.  The wired network did work until I hit the disconnect button, and now I need to get it working again to download the items that will (hopefully) get the wireless to work.

---

### Post by Vladlenin5000 on 2014-03-26
Hopefully you'll be able to solve it in a nice GUI :)...
Try system settings > Network  -- Re-enable the wired connection. The icon should appear.

---

### Post by riverguy99 on 2014-03-26
> **Vladlenin5000 said:**
> Hopefully you'll be able to solve it in a nice GUI :)...
Try system settings > Network  -- Re-enable the wired connection. The icon should appear.

Settings > Network brings me a fairly useless screen.  On the left is the box that says "Wired." Under that it says "Proxy."  On the right at the top it says "Wired" and below that, "Unmanaged."
Does that offer any clues?
Certainly there is a Terminal entry that will restore the Network icon?  It worked great right up until I clicked the "disconnet" button in the network icon dropdown menu.  The menu that vanished, along wtih the icon.
If I could figure out a way to reinstall 12.04 clean, I'd be happy to do it.  I would lose nothing, as I just got done installing it the first time when this happened.  Nobody seems to know of a way to reinstall the OS.  Nobody seems to know how to change the boot order in Linuz so that I can use the 12.04 ISO on a usb stick that I used originally.
Basically, I'm lost here with a laptop that has turned into a paperweight.

---

### Post by grahammechanical on 2014-03-26
> Nobody seems to know of a way to reinstall the OS.  Nobody seems to know  how to change the boot order in Linuz so that I can use the 12.04 ISO  on a usb stick that I used originally.

This is not true. These matters are frequently discussed on this forum. In fact I am posting this from a new installation of Ubuntu that I have just installed. 

If you installed Ubuntu then you know how to re-install it. Just do the same thing as you did before. Install using the entire disk is the simple option if you do not mind losing all the files and data on the disk.

If we did not know how to alter the boot priority in the BIOS/UEFI boot system then none of us would be able to install Linux. Of course, I cannot explain how to do it on your machine. So, I will not try. But unless you have changed the boot priority or reset the BIOS since you installed Ubuntu then the machine should still boot from the USB stick.

You could save yourself all that by trying this command. I do not know if it will work.

```
unity --reset-icons
```

Other than that you could also try using the software centre to re-install Network Manager.

Just a thought. Does this machine have a key combination that turns off  the network adapter? If the machine is a laptop, then it may have a  method of saving power by switching off the network adapter. In that  case Ubuntu may not offer a network icon. This is something that I have  not tested. Run this command

```
rfkill list
```

You should see something like this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


If you see a Yes to either of these then the network adapter is either switched off in software (not enabled in Network manager) or it is switched off by a hardware switch (key combination?)

Regards.

---

### Post by steeldriver on 2014-03-26
Just disconnecting the wired connection via the GUI (nm-applet) should not have caused the icon to disappear (although it might have changed it from an "up/down arrow" to an "empty fan")


[LIST]
[*]perhaps something is preventing network-manager from starting - look in your dmesg log and/or check 
[/LIST]
  ```
service network-manager status
```

[LIST]
[*]look in ~/.xsession-errors to see if just the nm-applet is failing to start 
[*]you could also attempt to run nm-applet from a terminal 
[*]"unmanaged" usually means that there is a competing interface definition in the /etc/network/interfaces file - check its contents 
[/LIST]

---

### Post by Navneet_Kumar on 2014-03-27
Just reboot the PC and type 'top' in the terminal......to see if the network-manager service is running or not......if not then start gnome-network-manager

---

### Post by james114 on 2014-04-01
I rebooted my computer after installing Apache web server, then met the same problem~ ( [http://i.imgur.com/rXKh6sv.jpg](http://i.imgur.com/rXKh6sv.jpg) )

My /etc/network/interfaces file: ( [http://i.imgur.com/xAf2WRC.jpg](http://i.imgur.com/xAf2WRC.jpg) )

Currently I cannot connect to Internet on my ubuntu computer

---

### Post by Bashing-om on 2014-04-01
james114; Hi !

A bit for fault isolation.
Can you ping your router ?( if you have a router in your set up)
terminal command:
```

ping -c3 192.168.0.1

``` where "192.168.0.1" is the more common IP address.
No return from the router, we start working back to the hardware and it's interface.
1st step in my procedure -> is the hardware recognized, and is a driver module loaded ?
```

sudo lshw -C Network

```

we be lookn'
[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james114 on 2014-04-01
Bashing-om, Thank you! 

ping -c3 192.168.0.1
```

connect: Network is unreachable
```

sudo lshw -C Network
```

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:67:80:7f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:57 ioport:a800(size=256) memory:cfbff000-cfbfffff memory:cfbf8000-cfbfbfff

```

I also tried grahammechanical's solutions but they don't work.

---

### Post by james114 on 2014-04-01
Just found the solution!

1) vi /etc/NetworkManager/NetworkManager.conf

2) set managed=true

3) reboot

The Networking icon is back!

---

### Post by bapoumba on 2014-04-01
Please mark your thread as solved (under Thread Tools), thanks!

---

### Post by riverguy99 on 2014-04-02
I won't have the culprit laptop back until the weekend, but I'll try all of these suggestions as soon as I can.  Thanks, everybody.

---

