---
title: "Linksys WPC54G and ndiswrapper"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by The Titan on 2008-05-28
I have an old 600mhz laptop with a WPC54G wireless card. I have  read about 20 different threads trying to figure this out.   This laptop is ubuntu 7.10 command line system only.  I plan on installing fluxbox on it. but i cant until i can use apt-get  :P

 I have installed the card using ndiswrapper and everything seems normal.  when i issue the "ndiswrapper -l" command it says driver installed and device present (alternate driver: bcm43xx)  when i issue the "iwlist wlan0 scan" command it says scanning not supported and /etc/network/interfaces is configured for eth0.  

i am very new at all this wireless stuff.  Note: there is no way for me to transfer files from the laptop to my desktop but i can from my desktop to the laptop.  Also my laptop has no internet so apt-get is off limits.  Any suggestions?

---

### Post by drkameleon on 2008-05-28
Can you please post the results of your ifconfig and iwconfig?

---

### Post by The Titan on 2008-05-28
> **drkameleon said:**
> Can you please post the results of your ifconfig and iwconfig?

NOTE: This is typed manually because i cant copy paste form laptop, no way to transfer =/

```

titan@mobilab:~$ sudo ifconfig
lo                  Link encap:Local Loopback
                     inet addr:127.0.0.1 Mask:255.0.0.0
                     UP LOOPBACK RUNNING MTU:16436 Metric:1
                     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                     TX packets:0 errors:0 dropped:0 overruns:0 frame:0
                     collisions:0 txqueuelen:)
                     RX bytes:) (0.0 b) TX bytes:0 ().0 b)

```
```

titan@mobilab:~$ sudo iwconfig

lo                  no wireless extensions.

eth0              IEEE 802.11b/g   ESSID:"ACTIONTEC" Nickname:"Broadcom 4306"
                    mode:Managed Access Point: Invalid
                    RTS thr:off   Fragment thr:off
                    Encryption key:1234-5678-90 Security mode:open
                    Link Quality=0/100 Signal level=-256 dBm Noise level=-256dBm
                    Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
                    Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```

---

### Post by drkameleon on 2008-05-28
Have you tried any 

```
modprobe ndiswrapper
```

and then restart?

---

### Post by The Titan on 2008-05-28
> **drkameleon said:**
> Have you tried any 

```
modprobe ndiswrapper
```and then restart?

yeah, i got errors when it trys to start the network.  

```


[101.2240000] bcm43xx: Error: Mocrocode "bcm43xx_microcode5.fw" not available or load failed.
SIOCSOFFLAGS: No such file or directory

(3 times in a row, same error but the [###.#######] increments up)

failed to bring up eth0.

                                                                                        [ OK ]

```

---

