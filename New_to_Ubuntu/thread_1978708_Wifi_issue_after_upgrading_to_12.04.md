---
title: "Wifi issue after upgrading to 12.04"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by Zieloniutki on 2012-05-12
Hi,

After upgrading to 12.04 Wifi stopped working. Computer is a Sony Vaio VGN-NS31S. Before the upgrade wifi was working correctly, now it says that Hardware switch is off although it is set to ON. The wifi LED is off all the time. 

Any help would be appreciated, as bringing this back to life is very important for me.

UPDATE
I am sorry for putting this thread in incorrect forum, so Mod please move to Networking & Wireless subforum.

As I have found new topic on how to report wifi issues, please find the rquested details below:

> lspci
05:00.0 Network controller: Intel Corporation WiFi Link 5100> iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
> 
lsmod | grep iwlwifi
iwlwifi               291847  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac8021> dmesg | grep iwlwifi
[   14.269161] iwlwifi 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.269198] iwlwifi 0000:05:00.0: setting latency timer to 64
[   14.269240] iwlwifi 0000:05:00.0: pci_resource_len = 0x00002000
[   14.269243] iwlwifi 0000:05:00.0: pci_resource_base = f8450000
[   14.269246] iwlwifi 0000:05:00.0: HW Revision ID = 0x0
[   14.269515] iwlwifi 0000:05:00.0: irq 46 for MSI/MSI-X
[   14.269619] iwlwifi 0000:05:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   14.269754] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[   14.293617] iwlwifi 0000:05:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   14.293620] iwlwifi 0000:05:00.0: Device SKU: 0Xf0
[   14.336659] iwlwifi 0000:05:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.341488] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[   14.355734] iwlwifi 0000:05:00.0: RF_KILL bit toggled to enable radio.
[   14.592118] iwlwifi 0000:05:00.0: loaded firmware version 8.83.5.1 build 33692
[   15.485714] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[ 2054.968815] iwlwifi 0000:05:00.0: PCI INT A disabled
[ 2101.905280] iwlwifi 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2101.905327] iwlwifi 0000:05:00.0: setting latency timer to 64
[ 2101.905370] iwlwifi 0000:05:00.0: pci_resource_len = 0x00002000
[ 2101.905372] iwlwifi 0000:05:00.0: pci_resource_base = f8450000
[ 2101.905375] iwlwifi 0000:05:00.0: HW Revision ID = 0x0
[ 2101.905633] iwlwifi 0000:05:00.0: irq 46 for MSI/MSI-X
[ 2101.905730] iwlwifi 0000:05:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 2101.905858] iwlwifi 0000:05:00.0: L1 Enabled; Disabling L0S
[ 2101.925643] iwlwifi 0000:05:00.0: device EEPROM VER=0x11f, CALIB=0x4
[ 2101.925649] iwlwifi 0000:05:00.0: Device SKU: 0Xf0
[ 2101.925687] iwlwifi 0000:05:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 2101.925863] iwlwifi 0000:05:00.0: RF_KILL bit toggled to disable radio.
[ 2101.930289] iwlwifi 0000:05:00.0: loaded firmware version 8.83.5.1 build 33692
> 
sudo lshw -C network
[sudo] password for gosia: 
  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:24:be:38:b1:6b
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.142 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:d2920000-d2923fff ioport:c000(size=256) memory:d2900000-d291ffff
  *-network DISABLED
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:b7:00:68
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic-pae firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:d0100000-d0101fff> iwlist scan
lo        Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.
> 
lsb_release -d
Description:    Ubuntu 12.04 LTS> uname -mr
3.2.0-24-generic-pae i686
> 
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                         [ OK ] Thanks in advance and best regards,
Pawel

---

### Post by r0roncoszek on 2012-05-12
Hi,
I have the same equipment: vaio vgn ns31s/s and no problems with it.
I tried both: upgrading from 11.10 to 12.04 and fresh install - everything worked fine.
Maybe try to start the machine from cd and run live version of 12.04 to check if the wifi works in the "clean" environment :)

Rgds,

Rafal

---

