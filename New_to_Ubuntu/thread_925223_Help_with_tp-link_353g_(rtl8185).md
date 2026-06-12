---
title: "Help with tp-link 353g (rtl8185)"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Bauldrick on 2008-09-20
I'm trying to get this card running, without any luck.

I upgraded to Intrepid so as to use lataest kernel because I read in a bug that it supported it. So this is what I see module wise:

/lib/modules/2.6.27-3-generic/kernel/drivers/net/usb/rtl8150.ko
/lib/modules/2.6.27-3-generic/kernel/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.27-3-generic/kernel/drivers/net/wireless/rtl8187.ko

lshw:

*-network:1 UNCLAIMED
             description: Ethernet controller
             product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32 maxlatency=64 mingnt=32

but when I try to insmod rtl8180 I get this error:

insmod: error inserting '/lib/modules/2.6.27-3-generic/kernel/drivers/net/wireless/rtl8180.ko': -1 Unknown symbol in module

and dmesg then shows:

[ 9570.373921] rtl8180: Unknown symbol ieee80211_free_hw
[ 9570.374159] rtl8180: Unknown symbol ieee80211_alloc_hw
[ 9570.374366] rtl8180: Unknown symbol ieee80211_register_hw
[ 9570.374575] rtl8180: Unknown symbol ieee80211_wake_queue
[ 9570.374845] rtl8180: Unknown symbol ieee80211_tx_status_irqsafe
[ 9570.375047] rtl8180: Unknown symbol eeprom_93cx6_multiread
[ 9570.375423] rtl8180: Unknown symbol ieee80211_stop_queue
[ 9570.375638] rtl8180: Unknown symbol ieee80211_unregister_hw
[ 9570.375862] rtl8180: Unknown symbol ieee80211_frequency_to_channel
[ 9570.376049] rtl8180: Unknown symbol ieee80211_rx_irqsafe
[ 9570.376176] rtl8180: Unknown symbol eeprom_93cx6_read
[ 9570.376308] rtl8180: Unknown symbol ieee80211_rts_duration

Is it true that it will not work that way?
When I try with ndiswrapper it loads and I can see my 'network' but can not connect to internet or anything local, AND pc freezes every few seconds due to load going to something like 5.2.

Does any one got this working or ca anyone help with me on this pease

---

### Post by mrund on 2009-01-17
I've also got a Tp-Link TL-WN353G wifi card in my machine, and I have no idea how to get it to work in Ubuntu Hardy. Please, somebody help!

Got it to work, easily! [http://ubuntuforums.org/showpost.php?p=6570508&postcount=2](http://ubuntuforums.org/showpost.php?p=6570508&postcount=2)

---

