---
title: "Xsession: 192: ls: not found boot problem"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by martynJ on 2008-09-12
Hi 
I have a fairly fresh installation of the latest Ubuntu (2 weeks), and have been getting along pretty well, but have hit a bit of a problem...

On startup I am locked out of logging on normally with the errors file...
```

/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: 192: ls: not found
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
exec: 205: x-terminal-emulator: not found

```
I can boot up fine in *GNOME safe-mode* and the system appears to work fine in that mode (including internet).

Any help pointing me in the direction of the cause would be greatly appreciated.

Thanks

Martyn

---

### Post by KIAaze on 2008-09-12
What did you do before that happened? Any idea what might have caused this?

Anyway, here are a few things you should check right away and fix if necessary:

1)Check that x-terminal-emulator and coreutils are installed:
```
dpkg -l x-terminal-emulator coreutils
```
If not install them:
```
sudo apt-get install x-terminal-emulator coreutils
```

2)Check that **/bin** and **/usr/bin** are present in the PATH variable in the file **/etc/environment**
```
cat /etc/environment
```
On my PC, it looks like this for example:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:**/usr/bin**:/sbin:**/bin**:/usr/games"
LANG="en_US.UTF-8"
```

If it's not the case, edit the file to add them:
```
sudo nano /etc/environment
```

3)Make sure "ls" and "x-terminal-emulator" are where they should be:
```
ls /bin/ls
ls /usr/bin/x-terminal-emulator

```
If not reinstall the previously mentioned packages.

---

### Post by martynJ on 2008-09-12
Solved! I had been following a redmine installation on the internet and had modified the file /etc/profile and this had broken the boot sequence. Removing the added line corrected the issue.

Unfortunately my wireless is now broken

sudo iwlist scan produces
```

wlan0   No scan results

``` 

I am on a Presario C700

:???:

---

### Post by KIAaze on 2008-09-12
What wifi card do you use?

Please post the output of the following commands:
```
lshw
lspci -vvnn
lsmod

```

---

### Post by martynJ on 2008-09-12
Hi KIAaze

lshw
AR242x 802.11abg Wireless PCI Express Adapter
lspci...
Atheros Comm Inc. AR242x 802.11abg 

lsmod
ndiswrapper    192920 0

(+ a bunch of other stuff, none of which looks relevant)

Thanks

---

### Post by KIAaze on 2008-09-12
According to [this page]("http://ubuntuforums.org/showthread.php?t=902860"), madwifi should work.

If you have madwifi installed, try:
```
sudo modprobe ath_pci
sudo modprobe ath5k (if you use Ubuntu intrepid)

```

Make sure they aren't blacklisted in /etc/modprobe/blacklist.

---

### Post by martynJ on 2008-09-12
Hi 

ath_pci was blacklisted so I deleted those lines?

However I've now discovered I can't connect via ethernet either. 

I have...
repaired packages automatically which appeared to do stuff.
ifconfig finds eth0 and wlan0
if i boot in ubuntu 8.04.1 recovery mode...
 my ethernet works
 iwlist scan finds my hub but wireless doesn't work

:(

---

### Post by KIAaze on 2008-09-12
If ifconfig sees wlan0, I think it means the driver is loaded.
Can you confirm this in the output of "lspci -v"?

I get this for example:
```

$lspci -v
...
02:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: Atheros Communications Inc. Device 1051
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 34000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
[B]        Kernel driver in use: ath_pci
        Kernel modules: ath_pci
[/B]...

```

> iwlist scan finds my hub but wireless doesn't work
What do you mean by "hub"?
You see the network, but have no internet access?

I don't think I'll be able to help you much more than google at this point...

---

### Post by martynJ on 2008-09-12
> **KIAaze said:**
> If ifconfig sees wlan0, I think it means the driver is loaded.
Can you confirm this in the output of "lspci -v"?
```

[B]        Kernel driver in use: ath_pci
        Kernel modules: ath_pci
[/B]...

```


I don't get this but i've a feeling I had to use ndiswrapper as madwifi didn't work with my hardware (my brains so leaky I can't remember) and i don't yet know how to find out.

I am looking at syslog and it is suggesting there is a problem with dhcp...
```

dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
etc
dhclient: send_packet: no such device
```
[/CODE]
> 
What do you mean by "hub"?
You see the network, but have no internet access?

The hub is a wireless hub with wired and wireless connections.

I guess I can reinstall everything but to be honest I'm only trying ubuntu since I program a lot in ruby (on windows), and it seemed the natural thing to do, but even ruby seems _much_ more reliable on xp (i'm fairly proficient on xp however and a complete noob in this os).

Many thanks for your help anyway

Martyn

---

### Post by martynJ on 2008-09-13
Reinstalled, this time managing to get madwifi drivers to work instead of ndiswrapper

I wasn't losing anything important and the reinstall actually helped solidify various commands. It was all very easy to get back to what I had this time, and was a worthwhile exercise in itself.

redmine installed too surprisingly easy with mongrel in production mode, mysql and php.

I guess I had broken a number of things and my inexperience with linux left me just a little too in the dark.

Now to put the gui to bed and learn the basics. Wish me luck!

Thanks again for your help

Martyn

---

