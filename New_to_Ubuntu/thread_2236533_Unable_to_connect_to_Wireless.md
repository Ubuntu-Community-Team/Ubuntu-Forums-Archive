---
title: "Unable to connect to Wireless"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by Stairwell on 2014-07-27
I'm new to Linux/Ubuntu. I just installed Ubuntu 14.04.1 on a Dell Latitude 620 Laptop. Ethernet connects fine but I need the wireless connection to work. In looking through the forum maybe I am missing the driver?, but I don't know how to find it or install it. I found these commands in the forum that might give more information about the wireless "lshw -c network" and "sudo lspci -v", and here are the results. Any help would be appreciated!

```
[FONT=arial]*-network [/FONT]
[FONT=arial]description: Network controller[/FONT]
[FONT=arial]product: BCM4311 802.11b/g WLAN[/FONT]
[FONT=arial]vendor: Broadcom Corporation[/FONT]
[FONT=arial]physical id: 0[/FONT]
[FONT=arial]bus info: pci@0000:0c:00.0[/FONT]
[FONT=arial]version: 01[/FONT]
[FONT=arial]width: 32 bits[/FONT]
[FONT=arial]clock: 33MHz[/FONT]
[FONT=arial]capabilities: bus_master cap_list[/FONT]
[FONT=arial]configuration: driver=b43-pci-bridge latency=0[/FONT]
[FONT=arial]resources: irq:17 memory:dfdfc000-dfdfffff[/FONT]
```


and
```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
Subsystem: Dell Wireless 1390 WLAN Mini-Card
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 2
Capabilities: [58] MSI: Enable- Count=1/1 Maskable- 64bit-
Capabilities: [d0] Express Legacy Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting
Capabilities: [13c] Virtual Channel
Kernel driver in use: b43-pci-bridge
```

---

### Post by kira-yamato-2008 on 2014-07-27
Is your network manager running?

---

### Post by Stairwell on 2014-07-27
Under "Settings--> Network" there is a "Wired" Connection listed with the Ethernet connection that is working. Is this the network manager that you are referring to?

---

### Post by kira-yamato-2008 on 2014-07-27
Try going to run and doing nm-applet or sudo nm-applet in terminal.

---

### Post by Stairwell on 2014-07-27
> **kira-yamato-2008 said:**
> Try going to run and doing nm-applet or sudo nm-applet in terminal.

This is the message I get when running sudo nm-applet in terminal. There is an icon on the right top - which when I open it up is labeled "Network Connection" and the Ethernet connection is listed.

```
nm-applet-Message: using fallback from indicator to GtkStatusIcon
```

---

### Post by kira-yamato-2008 on 2014-07-27
That should bring up an icon in your tray to manage your networks which is how you connect to a wireless network. My system gives me the same message and puts the icon in the tray when I use it.

---

### Post by Stairwell on 2014-07-27
> **kira-yamato-2008 said:**
> That should bring up an icon in your tray to manage your networks which is how you connect to a wireless network. My system gives me the same message and puts the icon in the tray when I use it.

Under "Network Connections" I used the "Add" button to add a Wifi connection, I put in the SSID, chose Mode = Adhoc and in Wifi Security Tab chose "WPA & WPA2 Personal" along with the password, under the tab IPV4 Settings I use "Automatic DHCP" then I save this new connection.

I then unhooked the ethernet cord - still no wifi connection.

---

### Post by kira-yamato-2008 on 2014-07-27
No the nm-applet in the tray is what I'm talking about it should be somewhere in the right hand bottom corner with things like the shut down button, clock, keyboard options sound, and things like that. If not connected look for an icon that looks like two computers one slightly behind the other with an X in the corner of it.

---

### Post by Stairwell on 2014-07-27
> **kira-yamato-2008 said:**
> No the nm-applet in the tray is what I'm talking about it should be somewhere in the right hand bottom corner with things like the shut down button, clock, keyboard options sound, and things like that. If not connected look for an icon that looks like two computers one slightly behind the other with an X in the corner of it.

No icon like that is showing up. But all the options you mention are available when I choose the System Settings Icon on the left hand side of the screen. Under "Hardware" things like Keyboard, Network, Sound, etc. are listed, Under "System" things like Time & Date, etc are listed. When I click on Network there are two things listed. "Wired" and "Network Proxy". There is a + and - button.

---

### Post by Stairwell on 2014-07-27
Also, I have tried to work through the Ubuntu Wireless troubleshooting guide, and saw the command "sudo iwconfig" might give more information. This is the result:

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by NM5TF on 2014-07-27
you might try these to see if your driver gets loaded.....which seems to be your problem.....

```
sudo apt-get install linux-firmware-nonfree
```

if that doesn' fix it, try this....

```
sudo apt-get firmware-b43-installer
```

might have to reboot after each install....

and if it still doesn't work, go here & follow directions

[http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/)

good luck...

tommy

---

### Post by Stairwell on 2014-07-27
> **NM5TF said:**
> you might try these to see if your driver gets loaded.....which seems to be your problem.....

```
sudo apt-get install linux-firmware-nonfree
```

if that doesn' fix it, try this....

```
sudo apt-get firmware-b43-installer
```

might have to reboot after each install....

and if it still doesn't work, go here & follow directions

[http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/)

good luck...

tommy

Thank you so much Tommy! The 3rd option worked! And I didn't need the extra code "sudo su" etc. to make it work automatically.

---

### Post by NM5TF on 2014-07-27
> **Stairwell said:**
> Thank you so much Tommy! The 3rd option worked! And I didn't need the extra code "sudo su" etc. to make it work automatically.

great news....glad it worked for you !!!

if you have any more troubles in your Linux adventures, these Forums are
the best resource on the 'net....

now if you could mark the thread as Solved so others can find the same help that would also be great....

use the "thread tools" at the top of your 1st post in this thread to mark it solved....

tommy

---

