---
title: "Total Noob Question about Drivers"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by ltkdrury on 2008-06-25
I recently converted from windows to ubuntu.  I got it installed but I cannot get on the internet to do anything.  I have a linksys wireless lan adapter (and I have the disk) but I cant find any simple directions (for someone who isnt a programmer) for how to install the driver for my network card.  I appreciate any help.  Thanks

---

### Post by dwhitney67 on 2008-06-25
Ah, the rush to get wireless working.  I presume the wired-port is working, yes?

Which particular Linksys Wireless USB LAN adapter do you have?  It wouldn't by chance be the WUSB54GC?

---

### Post by Het Irv on 2008-06-25
Please post the output of ```
lspci
```Also, Do you have a way to temporarily hook up to the internet?

---

### Post by Shuko on 2008-06-26
> **dwhitney67 said:**
> Ah, the rush to get wireless working.  I presume the wired-port is working, yes?

Which particular Linksys Wireless USB LAN adapter do you have?  It wouldn't by chance be the WUSB54GC?

I do have that adapter and don't know how to get it recognised by Hardy heron. Any advice would be greatly appreciated. I can connect via wired port OK.

---

### Post by dwhitney67 on 2008-06-26
Well, I have the same USB wifi dongle.  I'm not impressed with it (it's slow and doesn't receive well), but nevertheless I got it to work on my Fedora 9 system.

Btw, you don't need the CD.

Does your system already have a built-in wifi chip-set?  My system did and thus to get the dongle to work, I had to blacklist the driver for the built-in chip-set on my system (it only supports 802.11 a/b).  For now, I will assume that this is not an issue on your system.

The Linksys WUSB54GC requires the 'rt73usb' driver which is available with Ubuntu 8.04 (Hardy).  So let's give it a try...

First, plug in the dongle into an available USB port.
Second, run these commands (copy/paste them to avoid error):
```
$ sudo echo "alias wlan0 rt73usb" >> /etc/modprobe.d/aliases
$ sudo depmod -a
$ sudo modprobe rt73usb
```
Don't panic if you do not see any output from these commands; otherwise do panic!

Your USB dongle should now be working.  Verify if your system is able to detect any wireless Access Point (AP) in your area:
```
$ iwlist wlan0 scan
```
Hopefully your AP (or your neighbour's?) is visible.

The next thing is to add the 'rt73usb' driver to /etc/modules so that each and every time you reboot, the driver is automatically loaded.  This is how:
```
$ sudo echo rt73usb >> /etc/modules
```

Anyhow, the Network Manager (NM), which is accessible via the Gnome NM applet, should provide you a more user-friendly interface than the 'iw' commands (iwlist, iwconfig, etc).

P.S.  The built-in LED on my USB dongle does not light up when I am connected to my AP; don't be surprised if yours exhibits the same "feature".

---

### Post by Shuko on 2008-06-26
On the first command: sudo echo "alias wlan0 rt73usb" >> /etc/modprobe.d/aliases
I got: bash: /etc/modprobe.d/aliases: Permission denied

For info: -rw-r--r-- 1 root root 4624 2008-02-25 21:20 /etc/modprobe.d/aliases

sudo did not ask me for a password.

Now managed to do above as root. Carrying on...

---

### Post by unutbu on 2008-06-26
```
echo "alias wlan0 rt73usb" | sudo tee --append /etc/modprobe.d/aliases
```

---

### Post by dwhitney67 on 2008-06-26
Sorry about the bad commands.  Follow unutbu's advice.  Or just just enter the commands as root, thus obviating the need to use sudo for each command:
```
$ sudo su
```

---

### Post by Shuko on 2008-06-26
Ok all commands worked as root. What next? I get:
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:C9:4D:90
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level=-64 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000025ad22b521a
and Netgear is me.

But if I unplug the cable I still lose access. That is firefox stops working and I can't pick up mail. I don't know anything about the tools you mention.

---

### Post by unutbu on 2008-06-26
You can have a wired connection with your router, or a wireless connection with your router, but you can't use both at the same time because the computer would not know if it should send packets down the wire or through the wireless card.

To use wireless, disable the wired interface (probably called eth0) and then restart the networking script:
```

sudo ifdown eth0
sudo /etc/init.d/networking restart
```

---

### Post by Shuko on 2008-06-26
x

---

### Post by Shuko on 2008-06-26
Sorry but Can't do that without knowing how to start it again. Or will it start again automatically if I reboot with the the connection in?

I don't really want to be using the terminal window to swith connections anyway. Can't I use "Network Manager". I know I have it installed but not how to invoke it. Or is it also called Network Tools? There is also something just called Network whihc list network settings. This lists both wireless and wired and it let me remove the tick from wired but this has had no obvious effect. It won't let me put a tick by wirless.

---

### Post by unutbu on 2008-06-26
The commands I gave you will only affect the current session. If you were to reboot the machine, whatever default network configuration you are using now will be activated again.

You can turn interfaces on and off with

```
sudo ifup eth0   # To turn eth0 on again
sudo ifdown eth0 # To turn eth0 off.
```

I don't use the Network Manager myself, so I'm sorry but I can't advise you about how to make it work.
Network Manager is just a GUI frontend to the commands I'm telling you, however. Also, I think I can help you set it up so you won't have to type anything once we get things working.

Are you trying to get your machine to use wireless automatically every time you boot up? Or are you intending to switch between wired and wireless connections at various times?

[Edit: By the way, the restart command I gave you last time would not have worked properly, because it would have re-activated your eth0 interface. To get wireless networking to start (without eth0 starting as well) you'll need to edit /etc/network/interfaces. Once you answer the questions above, we'll be able to advise you better how to set things up.]

---

### Post by dwhitney67 on 2008-06-26
Shuko -

Do you not have an applet in the upper right-hand side of your screen that looks like two computers side-by-side when using the wired network?  When you pull the cable, the applet should change to indicate that you are disconnected.

That same icon is what you need to get set up with the wireless.  First, right-click on the applet to ensure that "Enable Wireless" has a check-mark next to it.

Then left-click on the same applet icon to select your Access Point (Netgear?).  If you are using encryption on your AP, then you should be prompted for the password to gain access to the AP (note, not the admin password, but the wireless security password).

I am using WPA Personal with my router and I am able to connect to my router.  Some people have said they have had trouble with WPA2 Personal and above.  So if you are using that protocol, consider changing it to WPA Personal (or WEP, or nothing at all if you wish).

---

### Post by Shuko on 2008-06-26
dwhitney

I do have usch an icon, in fact there are two identical icons (each of two screens). The first one says wired network connection with mouse over it and  Right click shows a tick against enable networking and also atext & pencil icon saying edit wireless networks. 

The second one says "Network Connection: lo" and is grayed out a bit - right clicking on it lets me select properties which lets me get information about three connections: wlan0:avahi(disconnected)  and eth0(idle but shows lots of data has been exchanged so i assume this is my wired connection and lo (idle with a 100k sent and received).

I don't have time now to carry on (my better half will get cross). I'll check out the rest of what you said tomorrow eveninh hopefully.

Thanks

---

