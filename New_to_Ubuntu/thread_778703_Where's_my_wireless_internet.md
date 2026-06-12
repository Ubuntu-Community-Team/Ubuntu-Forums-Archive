---
title: "Where's my wireless internet?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by pointyblue on 2008-05-02
I just installed 8.04 with Wubi from Vista on my Acer laptop.

The laptop has wireless internet. Vista automatically scans and finds it when I boot it, but Ubuntu can't seem to find it.

It's probably very simple to fix this but I have no idea what to do next! :lol:

Could somebody please point me in the right direction?

O:)

---

### Post by slimx3m on 2008-05-02
one of my friends is having the same kind of problem with a toshiba.

what do you get when you type "iwlist scan"?

---

### Post by jatiesch on 2008-05-02
try using *ndiswrapper -m* to ensure driver is loaded with every boot..
if still not successful there are many softwares in repos for managing wireless networks...u can try them also...

---

### Post by w4lgh on 2008-05-02
I am having the same wireless problem with my Acer Laptop. I think I know what the problem is, however it will NOT let me edit the file. When I go to... /etc/network/interfaces ... I can ope the interface file, and I think I see the problem, but when I correct it and try to save it, it says I dod not have permission to write this file. I thought as Admin you have full privledges. So if someone can tell me what I am doing wrong, or what I need to do to edit this file, I may have a FIX for the wireless issue. My direct email is: [email]agj2@bellsouth.net[/email]

---

### Post by plucky on 2008-05-02
w4lgh,

To edit any system file,you need to become privileged so ```
gksudo gedit /etc/network/interfaces
``` is what you need to do.Enter password and you are good to go.


Good Luck

---

### Post by pointyblue on 2008-05-03
When I do "iwlist scan" it returns:

[INDENT]lo     Interface doesn't support scanning

eth0     Interface doesn't suppert scanning[/INDENT]

I checked the restricted drivers. It says "Support for Atheros 802.11 wireless LAN cards enabled".

By exploring randomly (think I right-clicked the network icon, top right of the screen) I found a place with the headline Wireless Networks where I could fill in Name and Bssids. What on earth is bssids? :lol:

In Network Tools I pinged for a reaction and it returned IP Address 127.0.0.1 and Netmask/prefix 255.0.0.0 - which I have no idea what means, hehe!

Ok, then I restarted the laptop and logged into Vista in stead of Ubuntu. In my browser I accessed the wireless base station's address. To my surprise, under DHCP Client Log, Information on LAN DHCP clients currently linked to the wireless base station I found:
[INDENT]ip=192.168.1.100  mac=00-14-85-01-8E-23  name=sm-desktop[/INDENT]

And sm-desktop is the name of the Ubuntu 8.04 install on the computer! :-k (Naturally the name of my Vista install was there too.) So I guess Ubuntu actually found and connected to the wireless LAN... Isn't that strange?

Anyway, I found these pieces of information too:

[INDENT]Internet:
WAN IP: 
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1
Primary DNS: 192.168.0.1
Secondary DNS: 0.0.0.0

Home Network (LAN)
IP Address: 
Subnet Mask: 255.255.255.0[/INDENT]

(Don't know if this is relevant but I guess it might be if I have to setup something manually in Ubuntu.)

Where to go next? O:)

(Oh! By the way Ubuntu seems to be MUCH faster than Vista it's so cool!)

---

### Post by pointyblue on 2008-05-18
Anyone?

Or is Ubuntu not ready for wireless desktop use yet?

---

### Post by plucky on 2008-05-18
> When I do "iwlist scan" it returns:


try ```
sudo iwlist scan
``` which will show any local wireless access point.

If you left click on the nm-applet icon,if your wireless is working,you should see any local wireless networks in your area.If your network is there,select it and it should ask you for a WEP or WPA passphrase.

If you don't see any networks open a terminal and copy and paste the output to these commands ```
ifconfig
iwconfig
```


Good luck

---

### Post by RequinB4 on 2008-05-18
There are multiple Acer laptops.  If you have a problem, it's a lot more useful to know what wireless card you have.  Post the output of
```

lspci

```

This will list all your pci hardware devices and we can get your drivers working instead of messing around in network tools.  (By the way, you may want to delete your IP address for security). :)

---

### Post by pointyblue on 2008-09-12
When I do 

```
lspci
```

it returns

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I've tried to get used to Vista on the laptop since I couldn't make the wireless connection work in Ubuntu but Vista sucks and I really hope you guys can help me fix this problem...

---

### Post by pointyblue on 2008-09-13
Anyone..?

---

