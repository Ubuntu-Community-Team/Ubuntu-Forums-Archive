---
title: "handle lid switch disables wi-fi, only restart will turn it back on"
date: 2015-08-18
forum: New to Ubuntu
---

### Post by Athterath on 2015-08-18
I'm a new Linux user, running Ubuntu 14.04 LTS on a HP Pavilion 15-AB023CL.  I installed it using Pendrivelinux' *Universal USB Installer*, initially as a dual boot with Windows 8.1.  I've since upgraded the other partition to Windows 10, which has had no apparent effect on the way Ubuntu runs.

Ubuntu has no problem connecting to wi-fi on startup, after a reboot, when waking from hibernation, after the designated "airplane mode" function key has been depressed, or when resuming from a manual or automatic (inactivity) suspension.  But when "HandleLidSwitch" is set to "suspend", if I close the laptop without shutting down or hibernating "Wi-Fi is disabled by hardware switch," when it is reopened (even if I first manually suspended Ubuntu).  The "Enable Wi-Fi" option is greyed out and "sudo rfkill unblock wifi" does nothing.  The only way I've found to reconnect is to restart the computer.  No other function of Ubuntu or any of my applications seems to be affected.  Closing the lid while "HandleLidSwitch" is set to "ignore" does not cause disconnection.

When the wi-fi is disabled, "nmcli nm" yields:

RUNNING: running
STATE: disconnected
WIFI-HARDWARE: disabled
WIFI: disabled
WWAN-HARDWARE: enabled
WWAN: enabled

"sudo rfkill list" yields:

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

and "sudo lshw -C network" yields:

description: Wireless interface
product: Wireless 3160
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:08:00.0
logical name: wlan0
version: 83
serial: 34:e6:ad:3e:9e:5a
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-46-generic firmware=25.228.9.0 ip=192.168.1.118 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
resources: irq:67 memory:c3100000-c3101fff

(I don't know enough to know whether any of that is relevant, but I've seen similar information requested in other threads dealing with wi-fi problems, so I thought I'd get it out of the way.)

I'd really like to be able to have my machine suspend when I close the lid, without having to restart it to regain wi-fi access.  Any suggestions?

---

### Post by HermanAB on 2015-08-18
Howdy,

You should be able to recover by unloading and reloading the WiFi device driver with 'rmmod' and 'insmod'.  Reloading the driver, will typically also reset the WiFi adaptor and redownload the code for the little ARM processor on the WiFi thingy, which should get it going again.

The problem is figuring out what exactly the driver name is.  You can list all the loaded modules with 'lsmod' and try to google everything that looks remotely like it may be the culprit.

---

