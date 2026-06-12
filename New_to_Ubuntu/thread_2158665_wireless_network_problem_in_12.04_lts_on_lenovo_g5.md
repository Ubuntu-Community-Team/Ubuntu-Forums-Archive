---
title: "wireless network problem in 12.04 lts on lenovo g580"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by Mayank Tiwari on 2013-06-30
Hi everyone!

I am new to the ubuntu. I got lenovo g580(20150) model about 2 weeks ago. For MS Windows it has driver CD alright so its working well with windows 7. But I needed linux so i installed ubuntu 12.04 lts in dual boot. now the troubel is the ethernet and wireless network is not working.

I tried to use on/of switch (Fn+F5) nothing happened. its still showing wireless is disabled by hardware switch. well there is also trouble in bluetooth possibly but thats not the priority here.
i have searched a lot on this matter could not found appropriate solution :(

here are few details which i can provide
```

 hal.1: read hal dataprocess 2900: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
39: None 00.0: 10780 Network Interface                          
  [Created at net.124]
  Unique ID: Dxoz.GSopYcFr9cF
  SysFS ID: /class/net/usbpn0
  SysFS Device Link: /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.11
  Hardware Class: network interface
  Model: "Network Interface"
  Driver: "cdc_phonet"
  Driver Modules: "cdc_phonet"
  Device File: usbpn0
  HW Address: 1b
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.pIFk+DbcGO4
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "alx"
  Driver Modules: "alx"
  Device File: eth0
  HW Address: 20:89:84:4a:2c:db
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (Ethernet controller)

41: None 00.0: 10780 Network Interface
  [Created at net.124]
  Unique ID: RRvF.GSopYcFr9cF
  SysFS ID: /class/net/ppp0
  Hardware Class: network interface
  Model: "Network Interface"
  Device File: ppp0
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

42: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn._hWcjjS7AX5
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "ath9k"
  Driver Modules: "ath9k", "ath9k"
  Device File: wlan0
  HW Address: 2c:d0:5a:38:de:e3
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (Network controller)



```

```

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: yes



```

well i have tried

_rfkill unblock all_
 but no luck :confused:

here is the result of iwconfig

```

ppp0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

usbpn0    no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


```


please help me out.

---

### Post by carl4926 on 2013-06-30
Can you post
```
lspci -nnk | grep -iA2 net
```

---

### Post by Mayank Tiwari on 2013-06-30
thanks for reply sir!

this is my very first thread and i was not expecting help so soon, thanks alot .

here is what you asked for

```

mayank@mayank-Lenovo-G580:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lenovo Device [17aa:3218]
    Kernel driver in use: ath9k


```

---

### Post by carl4926 on 2013-06-30
Can we also see

```
lspci -nnk
```

---

### Post by Mayank Tiwari on 2013-06-30
here it is.

```


00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
    Subsystem: Lenovo Device [17aa:3977]
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: mei
    Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e59] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Kernel modules: i2c-i801
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx
    Kernel modules: alx
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lenovo Device [17aa:3218]
    Kernel driver in use: ath9k
    Kernel modules: wl, ath9k



```

---

### Post by carl4926 on 2013-06-30
OK I am not too sure
But I see a broadcom driver loaded. Lets remove it

```
sudo modprobe -rv wl
```This will only remove it until you reboot. If necessary you can uninstall it or blacklist it

I'm concerned though about what you posted
```
[COLOR=#000000][FONT=Ubuntu Mono]0: ideapad_wlan: Wireless LAN[/FONT][/COLOR]
    Soft blocked: no    Hard blocked: no1: ideapad_bluetooth: Bluetooth    Soft blocked: yes    Hard blocked: no3: phy2: Wireless LAN    Soft blocked: no [COLOR=#000000][FONT=Ubuntu Mono]    Hard blocked: yes[/FONT][/COLOR]
```we may have to blacklist ideapad_wlan

---

### Post by Mayank Tiwari on 2013-06-30
the terminal says

modprove: command not found

anyway if the trouble will be solved just upto the next reboot, do you think i shall remove it ?
but which one you are talking about ? alx or ath9k

---

### Post by carl4926 on 2013-06-30
I made a typo and corrected it
It's modprobe

---

### Post by carl4926 on 2013-06-30
This should remove 'wl'
```
sudo apt-get remove bcmwl-kernel-source
```
Then reboot

---

### Post by Mayank Tiwari on 2013-06-30
I did it, but no luck at all :/

---

### Post by carl4926 on 2013-06-30
So in /etc/modprobe.d
The file: blacklist.conf

Add the lines

blacklist ideapad_wlan
blacklist ideapad_bluetooth

You can always remove them later
And I'm not 100% sure I have the detail exact, but it's fine to try

---

### Post by Mayank Tiwari on 2013-06-30
well my friend I did it but its not showing any change in the situation :confused:
i kind of started to like ubuntu and then i came with this problem.
could you please suggest anything else ?

---

### Post by carl4926 on 2013-06-30
What do we see from rfkill now

---

### Post by Mayank Tiwari on 2013-06-30
the very same thing

```

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


```

---

### Post by carl4926 on 2013-06-30
I'll have to come back on this later as I have to do other stuff right now.

I see we still have the ideapad items listed
I'm pretty sure we need to take them out
IIRC some Dell and Acer devices have similar issues

Have a look at one quick google I did
[https://bbs.archlinux.org/viewtopic.php?id=146419](https://bbs.archlinux.org/viewtopic.php?id=146419)

---

### Post by Mayank Tiwari on 2013-06-30
yeah alright Thanks !
i'll take a look at the link if this could help.

---

### Post by carl4926 on 2013-06-30
Well it seems
[https://bbs.archlinux.org/viewtopic.php?pid=1143167#p1143167](https://bbs.archlinux.org/viewtopic.php?pid=1143167#p1143167)

The user also had Lenovo
But I assume it's actually acer_wmi
That needs blacklisting

---

### Post by Mayank Tiwari on 2013-06-30
well I tried something and here is the situation now.

I booted into windows and turned the wireless switch and bluetooth switch on.
I booted back into the ubuntu.
Its now working but now the trouble is i can not switch off the wireless device hardware or bluetooth device hardware.

It seems like the function switch is not working with the drivers in ubuntu.
is there anything which i could do ?
i dont want to make fool of myself switching again and again just to turn on and off the wireless system.

---

### Post by carl4926 on 2013-06-30
Sometimes the Fn button switches don't work well in Linux
Having said that mine are fine on 3 different Laptops but only my eeepc is Fn only control.
I'm not sure what to advise, but I never switch my wireless off anyway

---

### Post by Mayank Tiwari on 2013-06-30
well never mind that anyway.
I shall contact lenovo customer support team possibly they could suggest anything or i shall also keep wireless on alys :)
as i know there is no serious trouble the matter will be to save some of the battry power only.

Thanks for all the help you provided.:o

---

### Post by hiroshimakin on 2013-07-15
[COLOR=#000000]Hi Mayank,[/COLOR]

[COLOR=#000000]I met the same problems on my Lenovo G580, when I installed ubuntu 12.04.2 three days ago.[/COLOR]
[COLOR=#000000]But last night I solved them, it is as follows,[/COLOR]

[COLOR=#000000]1) You need a wireless pot around; 
2) Make sure you have already installed windows os on your computer;
3) Boot from windows os and switch on the wireless network;
4) Restart you computer and boot from ubuntu 12.04.02, then probably the wireless network is available; 
5) Update to the latest from "update manager";
6) If everything goes well, after restarting your computer, the ethernet network is available;
7) Enjoy!

I am not familiar with ubuntu os, especially on command, but I hope this method will be helpful to you.
If anything is not clear, or I made same mistakes on my tpying, pls send an email to me. 
[email]jinyong1221@gmail.com[/email][/COLOR]

---

### Post by eleternacho on 2014-02-15
After trying seeeeveral things, including some mencioned here, I SOLVED IT by reseting the BIOS.
When you turn on the computer, enter the BIOS (F2) and then reset it (F9)...

I have installed Ubuntu 12.04 on Lenovo B570.

---

### Post by wildmanne39 on 2014-02-15
Thread closed. Please do not post in old threads.

---

