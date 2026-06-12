---
title: "waiting for network configuration"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yumi on 2011-09-15
11.10 on my notebook is a slow starter. Since yesterdays update it shows a message "Waiting for network configuration" and then "Waiting up to 60 seconds more for network configuration".

But then, the network is ok. 11.10 on my stationary computer starts faster.

Michael

---

### Post by fdrake on 2011-09-15
it's not really a big issue to me. you can check your logs to see what's going one with it

```
less /var/log/syslog | grep -i network
```

---

### Post by Yumi on 2011-09-16
Does not mean much to me, but maybe you find the problem:
```
michael@Aspiremobile:~$ less /var/log/syslog | grep -i network
Sep 16 08:22:51 Aspiremobile kernel: [   14.339070] type=1400 audit(1316132568.710:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=696 comm="apparmor_parser"
Sep 16 08:22:51 Aspiremobile kernel: [   14.343109] type=1400 audit(1316132568.714:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=598 comm="apparmor_parser"
Sep 16 08:22:54 Aspiremobile avahi-daemon[930]: Network interface enumeration completed.
Sep 16 08:22:55 Aspiremobile NetworkManager[932]: <info> NetworkManager (version 0.9.0) is starting...
Sep 16 08:22:55 Aspiremobile NetworkManager[932]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Sep 16 08:22:56 Aspiremobile NetworkManager[932]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: init!
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: update_system_hostname
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: adding eth0 to iface_connections
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: adding iface eth0 to well_known_interfaces
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: autoconnect
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPluginIfupdown: management mode: unmanaged
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/eth0, iface: eth0)
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPluginIfupdown: locking wired connection setting
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0)
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: end _init.
Sep 16 08:22:56 Aspiremobile NetworkManager[932]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Sep 16 08:22:56 Aspiremobile NetworkManager[932]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    Ifupdown: get unmanaged devices count: 1
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: (162646696) ... get_connections.
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    SCPlugin-Ifupdown: (162646696) ... get_connections (managed=false): return empty list.
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto BACKUP ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto BACKUP'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto mghome ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto mghome'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto SCCNC-ATI-XC-281-E ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto SCCNC-ATI-XC-281-E'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto huanghua ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto huanghua'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto TP-LINK_2C1858 ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto TP-LINK_2C1858'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto CU_SP6X ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto CU_SP6X'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto TP-LINK_glin ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto TP-LINK_glin'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto TP-LINK_2F1E00 ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto TP-LINK_2F1E00'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto D-Link_DIR-600A ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto D-Link_DIR-600A'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto eth0 ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto eth0'
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile: parsing Auto xing ... 
Sep 16 08:22:56 Aspiremobile NetworkManager[932]:    keyfile:     read connection 'Auto xing'
Sep 16 08:22:57 Aspiremobile NetworkManager[932]:    Ifupdown: get unmanaged devices count: 1
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> modem-manager is now available
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> monitoring kernel firmware directory '/lib/firmware'.
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/ieee80211/phy0/rfkill2) (driver (unknown))
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/acer-wmi/rfkill/rfkill0) (driver acer-wmi)
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> WiFi enabled by radio killswitch; enabled by state file
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> WWAN enabled by radio killswitch; enabled by state file
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> WiMAX enabled by radio killswitch; enabled by state file
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> Networking is enabled by state file
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (eth0): carrier is OFF
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (eth0): new Ethernet device (driver: 'atl1c' ifindex: 2)
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcmsmac' ifindex: 3)
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): now managed
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): bringing up device.
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): preparing device.
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): deactivating device (reason: 2).
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> wpa_supplicant started
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): supplicant interface state: starting -> ready
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:22:57 Aspiremobile NetworkManager[932]: <info> (wlan0): supplicant interface state: ready -> inactive
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Auto-activating connection 'Auto mghome'.
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) starting connection 'Auto mghome'
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0/wireless): connection 'Auto mghome' has security, and secrets exist.  No new secrets needed.
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Config: added 'ssid' value 'mghome'
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Config: added 'scan_ssid' value '1'
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Config: added 'psk' value '<omitted>'
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> Config: set interface ap_scan to 1
Sep 16 08:22:58 Aspiremobile NetworkManager[932]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep 16 08:22:59 Aspiremobile NetworkManager[932]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep 16 08:22:59 Aspiremobile NetworkManager[932]: <info> (wlan0): supplicant interface state: authenticating -> associating
Sep 16 08:22:59 Aspiremobile NetworkManager[932]: <info> (wlan0): supplicant interface state: associating -> associated
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> (wlan0): supplicant interface state: associated -> completed
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'mghome'.
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> dhclient started with pid 982
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Beginning IP6 addrconf.
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 16 08:23:00 Aspiremobile NetworkManager[932]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info>   address 192.168.0.103
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info>   prefix 24 (255.255.255.0)
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info>   gateway 192.168.0.1
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info>   nameserver '208.67.222.222'
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info>   nameserver '208.67.220.220'
Sep 16 08:23:03 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep 16 08:23:04 Aspiremobile NetworkManager[932]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Sep 16 08:23:04 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:23:04 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:23:04 Aspiremobile NetworkManager[932]: <info> Policy set 'Auto mghome' (wlan0) as default for IPv4 routing and DNS.
Sep 16 08:23:04 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) successful, device activated.
Sep 16 08:23:04 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 16 08:23:04 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 16 08:23:20 Aspiremobile NetworkManager[932]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 16 08:23:20 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Sep 16 08:23:20 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Sep 16 08:23:20 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep 16 08:23:20 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 16 08:23:20 Aspiremobile NetworkManager[932]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Sep 16 08:24:51 Aspiremobile kernel: [  137.220991] type=1400 audit(1316132691.950:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1084 comm="apparmor_parser"
Sep 16 08:24:58 Aspiremobile NetworkManager[932]: <warn> bluez error getting default adapter: No such adapter
Sep 16 08:26:44 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:26:48 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 16 08:28:42 Aspiremobile NetworkManager[932]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))

```

---

### Post by cmccauley on 2011-09-16
I hate "Me-too" posts but this affects one of my laptops too.

---

### Post by nick_stokie on 2011-09-16
I think this delay is due to one (or more) network interfaces not being present on start-up so the system is giving them time (120secs) to try to come on line.

I had a similar issue and found an obsolete 'auto wlan0' entry in my /etc/network/interfaces.conf file - commenting this out returning the boot time to the normal speedy self.

I'll try to dig out the bug report and supporting info.

---

### Post by nick_stokie on 2011-09-16
Here we go. As per the second half of this post:

[http://ubuntuforums.org/showpost.php?p=11242427&postcount=37](http://ubuntuforums.org/showpost.php?p=11242427&postcount=37)

---

### Post by Yumi on 2011-09-16
Well, you had an entry too many, 

I do not have a interfaces.conf file. Maybe this is needed and it looks for it on the filesystem. Do I have to create one?

Michael

---

### Post by cariboo on 2011-09-16
You should have one in /etc/network, it's just called interfaces. No .conf extension.

---

### Post by Yumi on 2011-09-16
Thanks, that solved it.

The file is called /etc/network/interfaces. I commented out the first two lines referring to eth0 and now the notebook starts quicker.

Thanks for the help.

Michael

---

### Post by hawthornso23 on 2011-09-17
There should be an option to delay network startup until after login. Some people need networking to come up early during boot because they need to login via a network. No network = they can't login. But this isn't most of us. And when the networking concerned is  wireless on a laptop it makes no sense to force people to wait before they can login.

---

### Post by Podex on 2011-09-28
I have the same problem but there is no eth0 mentioned in my /etc/network/interfaces so this did not fix it for me.
After further search I found this bug report: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/856810)
They suggest this solution (from another bug report): [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441/comments/9](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441/comments/9)
However, this also does not fix my problem.
Anyone else have any more ideas?

---

### Post by flammon on 2011-09-28
Same problem here. None of the proposed solutions work. The system hangs with a message saying "Booting system without full network configuration..."

I don't want my laptop to connect to any networks before I login. This was a leftover from the Oneiric update. It configured my system to logon to my wireless network during boot and it stayed that way. How can I undo this?

---

### Post by flammon on 2011-09-28
I just installed GDM and it fixed the problem. I had tried that earlier but it didn't work so it must have been a combination of installing GDM one or more of the following.

[LIST=1]
[*]Removing references to my network devices in the interfaces file
[*]Removing lightdm
[*]Re-installing NetworkManager
[/LIST]

---

