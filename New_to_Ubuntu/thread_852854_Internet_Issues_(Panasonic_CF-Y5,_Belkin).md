---
title: "Internet Issues (Panasonic CF-Y5, Belkin)"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by eternallyverdant on 2008-07-08
I know you all must get tired of patiently dealing with our internet problems, but I've been doing some searching and I'm still fresh out of ideas.

I'm trying to get online with a wireless router (a Motorola Surf board), a Belkin Pre-N F5D8230-4 router, and Intel PRO/Wireless Adapter, and a Panasonic CF-Y5 laptop in the United States. I'm dual-booting with Windows XP, and I'm a total noob with Linux, so I'm sure my problem is something stupid. My current Linux system is Kubuntu 8.04 Hardy Heron, and I can only access the net with my wireless router. My internet connects just fine in Windows, but I'm using another computer to post this right now so that I can simultaneously use Linux and the Internet. Here are my KConsole results (I've included a slightly condensed version of the results because I have no way to get this info from one computer to another; I can type up anything else that might be needed, but I'd rather not do it needlessly):

lspci:
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


lsusb
Bus 005 Device 004: ID 1058:0902 Western Digital Technologies, Inc.
Bus 005 Device 003: ID 04da:2505 Panasonic (Matsushita)
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0c24:000e Taiyo Yuden
Bus 001 Device 001: ID 0000:0000


lshw -C network
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:54:12:06
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by chetan.89 on 2008-07-08
Hi there !

If you haven't yet tried anything, go to System-->Help and support and check the article on 'connecting to the internet'.

If you get any problems with it, try this article --> [http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

This was how I did it and it's working perfect now :). Hope it does for you too...

Good luck !
Chetan.

---

### Post by eternallyverdant on 2008-07-08
I've looked at the article, but when I try to do that or other installs I saw "kernel headers" mentioned, and apparently I don't have all the proper ones for some installs. I did a basic Google search on it, but couldn't find any relevant information on how to install. 

I also looked at a few repair threads, and did some scans and failed installs, but can't get ndiswrapper onto my computer-- it won't install from the disk when I use the relevant command in Konsole, which means that any drivers I install won't help me anyway, if I undersand the tutorials correctly. Any ideas?

---

