---
title: "Wireless Internet Broken"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by cafeinoz on 2008-09-09
I use a standard Compaq Presario C700 and the built in wireless internet worked in vista but not in Ubuntu.

---

### Post by Blutack on 2008-09-09
Could you open a terminal window, by going
Applications --> Accessories --> Terminal
and paste in the following commands?
```

lspci
lsusb
lshw -class network

```
then paste the results here please.

---

### Post by cafeinoz on 2008-09-09
cafeinoz@cafeinoz-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
cafeinoz@cafeinoz-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
cafeinoz@cafeinoz-laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:15:14:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
cafeinoz@cafeinoz-laptop:~$

---

### Post by Batsmasher on 2008-10-06
I have the same problem, Does the actual wireless light turn on?

---

### Post by nothingspecial on 2008-10-06
I have had success getting atheros cards working in ubuntu using madwifi.



Download the latest madwifi snapshot.

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
```

Unzip it

```
tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
```

At the beginning of the untarred  (unziped) folders ie the lines of gobbldygook the terminal just spat out will be the name of the current madwifi directory. In your case it is madwifi-hal-0.10.5.6-r3861-20080903

navigate to the extracted file


```
cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you`ve not got the tools necessary for compiling get them


```
sudo apt-get install build-essential linux-headers-$(uname -r)

```
Then  compile it 


```
sudo make

```

```
sudo make install

```

I hope that works

---

### Post by SolRebel on 2008-10-06
```
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.24-19-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.24-19-generic/net
make[1]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath'
make[1]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.24-19-generic/net
make[1]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal'
make[1]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr'
make[2]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe'
make[2]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample'
make[2]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.24-19-generic/net
make[2]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel'
make[1]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate'
make[1]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
test -d //lib/modules/2.6.24-19-generic/net || mkdir -p //lib/modules/2.6.24-19-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.24-19-generic/net; \
	done
make[1]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/net80211'
(export KMODPATH=/lib/modules/2.6.24-19-generic/net; /sbin/depmod -ae 2.6.24-19-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
make[1]: Leaving directory `/home/cramirez/madwifi-hal-0.10.5.6-r3835-20080801/tools'
cramirez@ubuntu:~/madwifi-hal-0.10.5.6-r3835-20080801$ 

```

This is what I got. The wireless will connect, but it can't hold that connection. Suggestions? :confused:

Edit: No clue why, but a second reboot did wonders!

---

