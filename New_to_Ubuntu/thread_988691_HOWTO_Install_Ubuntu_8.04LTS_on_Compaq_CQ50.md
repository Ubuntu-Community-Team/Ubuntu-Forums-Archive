---
title: "HOWTO: Install Ubuntu 8.04LTS on Compaq CQ50"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by lkraemer on 2008-11-20
How to Install Ubuntu 8.04 LTS on a Compaq CQ50-139NR (CQ50 series)


When trying to install a typical LiveCD of Ubuntu 8.04 LTS, the boot process hangs, and gives a
busybox error, and halts...........at a prompt........  Google searches show lots of folks
having this problem on Compaq CQ50's.

The solution is to download the Ubuntu 8.04 Alternate Install ISO image, VERIFY the MD5SUM, Burn
it as DAO at 4x or 8x, and use that CDR to install Ubuntu 8.04 LTS.  I am not sure, but I think it
hangs during the boot process because of the new Atheros Communications Inc. AR242x 802.11abg
Wireless PCI Express Adapter (rev 01).  Searches of all forums hasn't turned up a good solution.
(I installed the Ubuntu 32 bit software)

The following steps will get Ubuntu 8.04 LTS installed on your Compaq Hard Drive.

ASSUMPTIONS:
250 Gig Drive already has Windows Vista installed (with a 10 Gig Compaq Presario Recovery Partition),
and you want to add an Ubuntu 8.04 Partition along with a Linux-Swap Partition.  (MAX of FOUR
Primary Partions on any one Physical Drive)  I could have blown away Windows Vista, and used
the total 250 Gigs for Ubuntu, but I wanted to test everything first.  The easiest thing to do 
is make a Dual Boot system, and then never use Vista after using Ubuntu for 6 months.  By that
time you won't ever want to go back to Vista.  I resized the Vista partition so I had 120 Gig for
Ubuntu, and used a 6 Gig Linux-Swap Partition.  Ubuntu 8.10 LiveCD with Gparted was used for this.

1.  Insert Ubuntu 8.10, and Boot as LiveCD.  Use Gparted to RESIZE the Vista Partition, MOVE the
    CompaqRP so that it is immediately after the now smaller Vista Partition.  Now CREATE a new primary
    partition for Ubuntu, and format it as ext3.  Then create a new Linux-Swap Partition, and Format
    it as Linux-Swap.  This will allow you to install Ubuntu, and you can manually add the mount
    point of / during the install process.
2.  Insert the Ubuntu Alternate CDR and Boot on it.  Click INSTALL after it boots.
3.  Answer all the questions until it asks about guided versus manual partitioning.  Use manual,
    and insert the mount point as / and reformat as ext3.  I can't remember if I had to set the
    mount point for the swap partition, but if it shows up in the process also do it.
    I made the Ubuntu 120 Gig Partition root(/) and a 6 Meg Swap partition, twice my available RAM.
4.  After everything is finished, reboot from the hard drive into Ubuntu.  I skipped the Wifi Network setup.
5.  Once Ubuntu 8.04 is up and running, connect a wired ethernet cable, and update Ubuntu, then
    reboot as needed.
6.  Now boot into Vista, and let it use the Recovery Console to resize and adjust it's settings
    accordingly.
7.  Boot into Ubuntu, and open a terminal window.  Use lspci to see what your system has for a Wifi
    controller.  Here is what my computer displays.  Now all we need is the Driver for the Atheros
    AR242x (rev 01) Wireless PCI Adapter to make it functional.

Open a Terminal window and use the following commands to verify the Wifi information.

lspci
    
	larry@ubuntu:~$ lspci
	01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
	02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

lspci -v | less
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 360b
        Flags: bus master, fast devsel, latency 0, IRQ 221
        I/O ports at 3000 [size=256]
        Memory at d0410000 (64-bit, prefetchable) [size=4K]
        Memory at d0400000 (64-bit, prefetchable) [size=64K]
        Expansion ROM at d0420000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 137a
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

larry@ubuntu:~$ lsmod | grep ath
ath_rate_sample        16128  1 
ath_pci               249016  0 
wlan                  236400  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               305376  3 ath_rate_sample,ath_pci

larry@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:7b:92:97
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:23:4d:15:1e:78
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
larry@ubuntu:~$

larry@ubuntu:~$ dmesg | grep -e iwl -e wlan -e ath
[   33.215950] ath_hal: module license 'Proprietary' taints kernel.
[   33.809495] MadWifi: ath_attach: Switching rfkill capability off.
[   33.892481] ath_pci: wifi0: Atheros 5424/2424: mem=0xd2600000, irq=20
[   74.428240] ath0: no IPv6 routers present
larry@ubuntu:~$

larry@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
larry@ubuntu:~$ 

larry@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

larry@ubuntu:~$

larry@ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

iwlist scan 2>/dev/null | grep ESSID


8.  Go here and follow the steps to install the Wifi Drivers.
    [http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=792158&highlight=AR5007EG)
9.  If your Wifi still doesn't work try blacklisting the Restricted Hardware Drivers. 

sudo gedit /etc/modprobe.d/blacklist

#blacklist the Hardware Drivers (Restricted)
blacklist ath_hal
blacklist ath_pci

Reboot and see if your CQ50's Wifi is functional.

Ubuntu 8.04 LTS Guide URL:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

Atheros AR242x Info URL:
[http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/)

32 Bit - Reference URl'S:
[http://www.dailygeeks.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/](http://www.dailygeeks.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/)
[http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodTypeId=321957&prodSeriesId=3739787](http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&taskId=135&prodTypeId=321957&prodSeriesId=3739787)
[http://www.linuxforums.org/network/wlan_cards_and_linux.html](http://www.linuxforums.org/network/wlan_cards_and_linux.html)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://www.ubuntukungfu.org/blog/2008/11/make-almost-any-wifi-card-work-with-ubuntu/](http://www.ubuntukungfu.org/blog/2008/11/make-almost-any-wifi-card-work-with-ubuntu/)
[http://ubuntuforums.org/showthread.php?t=902860&highlight=Atheros+AR242+Driver](http://ubuntuforums.org/showthread.php?t=902860&highlight=Atheros+AR242+Driver)

64 Bit Info:
[http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278](http://forumubuntusoftware.info/viewtopic.php?f=7&t=1278)

---

