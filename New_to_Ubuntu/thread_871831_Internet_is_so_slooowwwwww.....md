---
title: "Internet is so slooowwwwww...."
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Reinbag on 2008-07-27
So I posted this in the network forum, but got only one response. Basically, I switched to Ubuntu last week and things are going relatively well. One thing that is driving me crazy though is my internet connection. I used to own a 28.8 modem and that was honestly about the same speed as my internet now. I use a wireless router and a cable modem, which worked relatively fine in windows, but now it is absolutely miserable. 

I did try to switch the DNS servers to opendns with the IP addresses 208.67.222.222 and 208.67.220.220, but with little luck. Plus, they disappear from my system every time I reboot. I dont´t understand this all too well, so a little help would be greatly appreciated.

Thanks.

---

### Post by frank002 on 2008-07-27
What version are you installing? Is it Hardy 8.04? In Gutsy 7.10 you had to disable IPv6 to get good speeds. You might want to do that.

---

### Post by phidia on 2008-07-27
Maybe the correct driver is not enabled for your wireless card?
Do you know what card you have and how you set it up?
From a terminal window enter "iwconfig"  & "lshw -C network"
Post the output of that here.

---

### Post by Reinbag on 2008-07-27
Okay, so I have Hardy, and here´s the info from the wireless card.
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"fabio"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:65:40:B2
          Bit Rate=54 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=34/100  Signal level=-61 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lshw -c network:
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

