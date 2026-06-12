---
title: "Need help installing RTL8187b-modified.tar.gz"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by mbarvian on 2008-05-16
Hi guys, I'm a complete newbie to Ubuntu, but I think I'm getting a little better.  What I wanted to know was where to get the right drivers for my wireless card (RTL 8187b), and I found it.  Now, I need to know how to download it, I downloaded this link: rtl8187b-modified-jadams-2-1-2008.tar.gz on [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)

Thanks

---

### Post by kwacka on 2008-05-16
1. in the directory you have the file, open terminal and type ```
tar -zxvf filename
```

or

2. right mouse click on file in nautilus, and then 'extract here'

---

### Post by mbarvian on 2008-05-16
> **kwacka said:**
> 1. in the directory you have the file, open terminal and type ```
tar -zxvf filename
```

or

2. right mouse click on file in nautilus, and then 'extract here'

OK, done, now what?

---

### Post by kwacka on 2008-05-16
now you have a new folder named rtl8187b-modified-jadams-2-1-2008.

What is in it?

What are the instructions that took you to the site originally?

---

### Post by mbarvian on 2008-05-16
> **kwacka said:**
> now you have a new folder named rtl8187b-modified-jadams-2-1-2008.

What is in it?

What are the instructions that took you to the site originally?

I didn't follow any instructions that took me to that site, I just found it because a few people had my similar problem and this fixed it.  Here's what's in the folder:
[img]http://i231.photobucket.com/albums/ee240/mbarvian/Screenshot-1-1.png[/img]

---

### Post by kwacka on 2008-05-16
> **mbarvian said:**
> I didn't follow any instructions that took me to that site, I just found it because a few people had my similar problem and this fixed it.  

And what did they do?

BTW, the names of the files might give you a clue, specifically 'README' and 'README.FIRST'

Alternatively you can forget the sight and search 'RTL8187B' here and you'll find this: [http://ubuntuforums.org/showthread.php?t=788954&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=788954&highlight=rtl8187)

---

### Post by mbarvian on 2008-05-16
> **kwacka said:**
> And what did they do?

BTW, the names of the files might give you a clue, specifically 'README' and 'README.FIRST'

Alternatively you can forget the sight and search 'RTL8187B' here and you'll find this: [http://ubuntuforums.org/showthread.php?t=788954&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=788954&highlight=rtl8187)

OK, this is what I did and what the outcomes were:

```

maxwell@maxwell-laptop:~$ cd /home/maxwell/Documents/rtl8187b-modified
maxwell@maxwell-laptop:~/Documents/rtl8187b-modified$ sudo chmod +x makedrv
maxwell@maxwell-laptop:~/Documents/rtl8187b-modified$ sudo ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/maxwell/Documents/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.o
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:433: warning: initialization from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:432: warning: unused variable ‘dwork’
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_probe_resp’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:710: warning: ISO C90 forbids mixed declarations and code
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_retry_wq’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2253: warning: initialization from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2252: warning: unused variable ‘dwork’
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2475: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2476: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2477: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2478: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2479: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2480: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1666: warning: ‘chlen’ may be used uninitialized in this function
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_rx.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_tx.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_wx.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_module.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:87: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:109: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:125: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:141: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:423: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211-rtl.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211-rtl.ko
  CC      /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/maxwell/Documents/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.o
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:934: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_manage_urbsubmit’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:954: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_rtx_disable’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:1255: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2220: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2227: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2277: warning: ISO C90 forbids mixed declarations and code
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2280: warning: cast from pointer to integer of different size
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2281: warning: ISO C90 forbids mixed declarations and code
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2290: warning: cast to pointer from integer of different size
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2310: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2256: warning: unused variable ‘i’
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_deleteendpoints’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2328: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: At top level:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: ‘struct struct_work’ declared inside parameter list
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: its scope is only this definition or declaration, which is probably not what you want
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_wmm_param_update’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2437: warning: initialization from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2439: warning: initialization from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2654: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:2702: warning: assignment from incompatible pointer type
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_adapter_start’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:3054: warning: unused variable ‘bInvalidWirelessMode’
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:3053: warning: unused variable ‘SupportedWirelessMode’
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:3052: warning: unused variable ‘InitWirelessMode’
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:3051: warning: unused variable ‘ieee’
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187_core.c:3769: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8180_93cx6.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8180_wx.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8180_rtl8225.o
  CC [M]  /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_wx_get_freq" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko] undefined!
  CC      /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.mod.o
  LD [M]  /home/maxwell/Documents/rtl8187b-modified/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
maxwell@maxwell-laptop:~/Documents/rtl8187b-modified$ 


```

But, you see, that's what the problem is, that I don't know how to finish the installation. :(  Any help after this?

---

