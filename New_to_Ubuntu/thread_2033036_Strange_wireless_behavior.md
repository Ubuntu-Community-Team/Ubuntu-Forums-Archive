---
title: "Strange wireless behavior"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by gleble on 2012-07-25
Every time I try to connect to Orange through my home hub on my My Acer aspire one happy2 it searches for a while and connects to BTFON. Why can't I connect to my home router?

---

### Post by gleble on 2012-07-25
Does this shed any light on the matter. The first one is when I try to connect. The second is after BTFON sneaks in.

```
annette@annette-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WANNADOO-C995"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E0:91:F5:51:75:30   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

annette@annette-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTFON"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 0A:8B:5D:93:FA:4A   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

```

---

### Post by mapes12 on 2012-07-25
Sounds as though your connection is defaulting to the BTFON open network because your system has got fed up of waiting for any WEP key your Orange router requires to authenticate the connection. Have a look at the security procedures for your Orange router. Find out what the security key is. Reboot Ubu then click your wireless connection before it defaults to the BTFON service. You should see your Orange router with a padlock on its icon. Click it then enter your security key to connect.

---

### Post by gleble on 2012-07-26
I have two acer laptops. This one connects OK, the HAPPY2 still won't connect.  Edit Connections gives the same info on both machines. Is there something I am missing that can be causing this problem? I can still connect to BTFON. The HAPPY2 is dual boot with windows 7 which gets on line fine.

---

### Post by NikTh on 2012-07-26
Hi , 
i see a low bit rate and link quality. Is your router close ? 

Try this command and see if fixes something 
```
sudo iwconfig wlan0 rate 54M
```Thanks

---

### Post by gleble on 2012-07-26
No luck, the laptop is line of sight 2m from the router.
Good machine
```
wlan0     IEEE 802.11bgn  ESSID:"WANNADOO-C995"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E0:91:F5:51:75:30   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Bad machine
```
wlan0     IEEE 802.11bgn  ESSID:"WANNADOO-C995"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: E0:91:F5:51:75:30   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0
```

---

### Post by NikTh on 2012-07-26
Hi , 
i cannot see something wrong with this "Bad machine" . 

I see you are connected up and running with a signal i never seen before !!! (70/70) 

What is the problem ? its seems you are connected normally.  

Thanks

---

