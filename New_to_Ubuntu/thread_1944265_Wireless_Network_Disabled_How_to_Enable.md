---
title: "Wireless Network Disabled: How to Enable??"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by brainglitch on 2012-03-21
Hey everyone!

I posted another thread on this the other day. I have a Lenovo laptop. I installed Ubuntu 11.10 the other day and love it. The only problem is, I cannot enable the WiFi! I have gone into Network Settings and tried to enable the WiFi literally a dozen times. I slide the little bar from OFF to ON; it stays on for half a second and then goes back to Off. 

After a few hours of reading nd much command-pasting into the Terminal, I have determined that:

a) Ubuntu can see my wireless card (an Intel WiFi 1000 BGN)
b) the driver is installed.
c) I can connect to the internet no problem with an Ethernet cable.

Again, everything about Ubuntu runs great and I love it, but it is a major problem that I can only connect to the Internet with a hard connection. If anyone has any ideas, please let me know, so I can get this fixed over spring break! :)

Here is what I'm seeing in Terminal:

nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        74:E5:0B:3C:F3:50

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        "blanked out by me"

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


---------@ubuntu:~$  sudo lshw -C network
[sudo] password for -----: 
[B]  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000[/B]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:3c:f3:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       c**onfiguration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn**
       resources: irq:43 memory:d0500000-d0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:8a:32:b4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff

 sudo lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
**02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000**
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

If anyone wants me to try any commands, or has any ideas, I would greatly appreciate it. Thanks in advance!

---

### Post by NikTh on 2012-03-21
Hi , 
here is your solution.. i think 
Open terminal and , 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` then add this line at the end 
```
blacklist acer_wmi
```click save and restart.

---

### Post by brainglitch on 2012-03-21
Thank you so much! It worked!

I'll mark this problem solved. If you have time, would you be able to explain exactly how that worked? If not, then that is cool since the problem is solved. I suspect that it had something to do with the 

3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

But I am not sure. Just a college student trying to learn more about computers.... :)

---

### Post by NikTh on 2012-03-21
> **brainglitch said:**
> Thank you so much! It worked!

I'll mark this problem solved. If you have time, would you be able to explain exactly how that worked? If not, then that is cool since the problem is solved. I suspect that it had something to do with the 

3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

But I am not sure. Just a college student trying to learn more about computers.... :)

Yes . You suspected correctly. You helped to solve your problem . With command's output. This problem is almost common. I had the answer ready (it is not my "hack" ) . Here -->  [http://ubuntuforums.org/showthread.php?t=1745317](http://ubuntuforums.org/showthread.php?t=1745317) look [chili555]("http://ubuntuforums.org/member.php?u=35909") answer (#7 post) . Here again --> [http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi) (#6 post). 
It is the module that creates the problem. We blacklisted that module and its all ok! 
Here --> [http://ubuntuforums.org/showthread.php?t=1587928](http://ubuntuforums.org/showthread.php?t=1587928) explains the bug and the fix . 

):P

---

### Post by brainglitch on 2012-03-22
OK, that makes sense now. Again, thank you!

---

