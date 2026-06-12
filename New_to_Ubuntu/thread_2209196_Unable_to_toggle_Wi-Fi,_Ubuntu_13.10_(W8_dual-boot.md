---
title: "Unable to toggle Wi-Fi, Ubuntu 13.10 (W8 dual-boot)"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by Henrik_Edholm on 2014-03-04
Hi. 

The issue I have is with the Network Manager.
The following are 100% disabled (grey marked):
Wi-Fi Networks
Wi-Fi is disabled by hardware switch
Enable Wi-Fi
Connection Information

Just installed Ubuntu 13.10 and dual-booting it with Windows 8. 
I'm running on a Lenovo Yoga 2 Pro, which of course comes without Ethernet possibilities (since I don't own a USB-ethernet adapter).
Why I mention this is since I read on some forum posts about downloading firmware updates through the terminal, which becomes quite impossible atm.
If it's not obvious yet I'm more or less a total beginner when it comes to Linux.

So, what I've tried so far:
1. Enable/disable "Networking" with no success (through Terminal and by clicking)
2. All the Fn-key combination without any success.
3. Followed this forum-post: [http://ubuntuforums.org/showthread.php?t=1962191](http://ubuntuforums.org/showthread.php?t=1962191) without any luck.
4. Went into BIOS to see that Wireless was enabled.

Things I think might be helpful to those wanting to help me:
1. Typing "sudo rfkill list all" displays:
    0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
    1: ideapad_bluetooth: Bluetooth
        Soft Blocked: no
        Hard Blocked: yes
    2: phy0: Wireless LAN
        Soft Blocked: no
        Hard Blocked: no
    3: hci0: Bluetooth
        Soft Blocked: no
        Hard Blocked: no

2. Typing "rmmod iwlwifi" displays:
    Error: Module iwlwifi is in use byt: iwlmvm

3. Typing "rmmod iwldvm" displays:
    Error: Module iwldvm is not currently loaded

4. Typing "iwconfig" displays:
    lo    no wireless extensions.

    wlan0    IEEE 802.11abgn ESSID:off/any
        Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm
        Retry long limit: 7    RTS thr:off    Frament thr:off
        Power Management:off

5. Typing "lspci | grep Network" gives me:
    01:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

6. Typing "lshw -C network" gives me:
*-network DISABLED
description: Wireless Interface
product: Wireless 7260
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:01:00.0
logical name: wlan0
version: 6b
width: 64 bits
clock: 33MHz
driver = iwlwifi
driverversion = 3.11.0-12-generic
firmware = 22.0.7.0

7. When typing "lsmod" I react on the following:
Module                 Size    Used  by
iwlmvm               161349   0
mac80211           596969   1  iwlmvm
iwlwifi                 165398   1  iwlmvm
cfg80211             479757   3 iwlwifi, mac80211, iwlmvm
ideapad_laptop       18342  0
(does this look as it's supposed to?)

I will of course keep searching for solutions, but feels like I could use some advice from this lovely community as well.

Thanks in advance.

---

### Post by Henrik_Edholm on 2014-03-04
Solved the issue thanks to this link: [http://www.scrye.com/wordpress/nirik/2013/10/18/lenovo-yoga-2-pro-and-fedora-review/](http://www.scrye.com/wordpress/nirik/2013/10/18/lenovo-yoga-2-pro-and-fedora-review/)
Had to blacklist ideapad_laptop

---

