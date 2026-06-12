---
title: "Realtek 8185 on my Gateway"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by silkko on 2008-08-15
I have read a lot of articles on this and found a patch for this as well but i still can't get it working.. I believe this is because am a total noob.. all the same am a fast learner and would love it if i could have the step by step compilation.I use hardy.

I keep getting errors even after getting the patch. I got it from here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196285) and [http://www.willdaniels.co.uk/index.php/blog/tech-stuff](http://www.willdaniels.co.uk/index.php/blog/tech-stuff).

I'd like to display a break down of my display..

> silkko@DATA-laptop:~$ unzip /home/silkko/Desktop/rtl8185.zip
Archive:  /home/silkko/Desktop/rtl8185.zip
   creating: rtl8185/
  inflating: rtl8185/makedrv         
  inflating: rtl8185/wlan0down       
  inflating: rtl8185/release_note    
 extracting: rtl8185/ifcfg-wlan0     
  inflating: rtl8185/readme          
  inflating: rtl8185/wlan0dhcp       
  inflating: rtl8185/wlan0up         
  inflating: rtl8185/wpa_supplicant-0.4.9.tar.gz  
  inflating: rtl8185/rtl8185.tar.gz  
  inflating: rtl8185/rtl8185-fix2.6.24.patch  
  inflating: rtl8185/stack.tar.gz    
silkko@DATA-laptop:~$ cd rtl8185


> silkko@DATA-laptop:~/rtl8185$ ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
./makedrv: line 5: patch: command not found
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/silkko/rtl8185/ieee80211/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/silkko/rtl8185/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_softmac.o
/home/silkko/rtl8185/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/silkko/rtl8185/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_rx.o
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_tx.o
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_wx.o
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_module.o
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_crypt.o
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.o
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.o
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_encrypt’:
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.c:417: error: ‘struct scatterlist’ has no member named ‘page’
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.c: In function ‘ieee80211_tkip_decrypt’:
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.c:511: error: ‘struct scatterlist’ has no member named ‘page’
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.c: In function ‘michael_mic’:
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.c:613: error: ‘struct scatterlist’ has no member named ‘page’
/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.c:617: error: ‘struct scatterlist’ has no member named ‘page’
make[2]: *** [/home/silkko/rtl8185/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[1]: *** [_module_/home/silkko/rtl8185/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/silkko/rtl8185/rtl8185/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/silkko/rtl8185/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/silkko/rtl8185/rtl8185/r8180_core.o
/home/silkko/rtl8185/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_init’:
/home/silkko/rtl8185/rtl8185/r8180_core.c:588: error: ‘proc_net’ undeclared (first use in this function)
/home/silkko/rtl8185/rtl8185/r8180_core.c:588: error: (Each undeclared identifier is reported only once
/home/silkko/rtl8185/rtl8185/r8180_core.c:588: error: for each function it appears in.)
/home/silkko/rtl8185/rtl8185/r8180_core.c: In function ‘rtl8180_proc_module_remove’:
/home/silkko/rtl8185/rtl8185/r8180_core.c:594: error: ‘proc_net’ undeclared (first use in this function)
/home/silkko/rtl8185/rtl8185/r8180_core.c: In function ‘rtl8180_init’:
/home/silkko/rtl8185/rtl8185/r8180_core.c:3159: warning: assignment from incompatible pointer type
/home/silkko/rtl8185/rtl8185/r8180_core.c:3522: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/silkko/rtl8185/rtl8185/r8180_core.c:3522: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/silkko/rtl8185/rtl8185/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/silkko/rtl8185/rtl8185/r8180_core.c:4213: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/silkko/rtl8185/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/silkko/rtl8185/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
silkko@DATA-laptop:~/rtl8185$ 

> silkko@DATA-laptop:~/rtl8185$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device
silkko@DATA-laptop:~/rtl8185$ 

> silkko@DATA-laptop:~/rtl8185$ ./wlan0rmv
bash: ./wlan0rmv: No such file or directory
silkko@DATA-laptop:~/rtl8185$ ./wlan0down
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8180 does not exist in /proc/modules
ERROR: Module ieee80211_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_rtl does not exist in /proc/modules
silkko@DATA-laptop:~/rtl8185$ 


> silkko@DATA-laptop:~/rtl8185$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device
silkko@DATA-laptop:~/rtl8185$ 

---

### Post by silkko on 2008-08-15
Can anybody help

---

