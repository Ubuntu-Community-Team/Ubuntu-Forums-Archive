---
title: "Laptop freezes when i enable wireless and ac adapter is plugged"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by cesarmvb on 2012-08-30
GOOD, DAY!

MY LAPTOP FREEZES WHEN I ENABLE WIRELESS AND AC ADAPTER IS PLUGGED.

ETHERNET WORKS FINE ALONG WITH AC ADAPTER.
I FOLLOWED A THREAD THAT SAID SOMETHING ABOUT "echo <N" etc, etc. AND SO FAR SAME BEHAVIOR.

MY LAPTOP IS TOSHIBA.

ANY ASSISTANCE WILL BE GREATLY APPRECIATED.

---

### Post by NikTh on 2012-08-30
Hi , 
boot in to BIOS configuration page and set as first option for boot, the Network (or something similar)
Thanks

---

### Post by cesarmvb on 2012-09-02
> **NikTh said:**
> Hi , 
boot in to BIOS configuration page and set as first option for boot, the Network (or something similar)
Thanks


Hi, NikTh
Changed BIOS same result.

By the way, I left out some important info in my original message:
1. I am using Kubuntu 12
2. I can log in without any problem
3. Ethernet and Wireless can work w/no issues
4. Ethernet and AC Adapter can also work w/no issues
5. When I click on the little network manager icon sitting at the bottom right corner of my kubuntu and check the Wireless box, the computer slows down while the connection is established, then a little green check mark signals wireless is enabled and working. However, when the same check mark signals ethernet is enabled and working... the computer freezes.
This happens when the ac adapter is plugged, otherwise the computer functions properly.
Again, 
AC adapter+ethernet OK
ethernet+wireless OK
wireless+AC adapter BAD (with or without the ethernet cable plugged in)

My wireless card is Realtek and... I cannot think of anything else.

Many thanks for your support!

---

### Post by NikTh on 2012-09-02
Hello , 
the truth is that I cannot think anything else too. 

Weird problem . Hardware maybe ? did you try to unplug the battery and the AC adapter (of course while laptop is closed) and hold down the power button for at least 10 secs ? 

Then plugin the AC adapter and try again to see what happened . 

Thanks

---

### Post by cesarmvb on 2012-09-02
Hi, NikTh
I have windows 7 installed (dual boot, kubuntu and windows 7) and everything works perfect on windows... Therefore, we can rule out hardware issues (fortunately)

Thankx for giving it a try NikTh. 
I will post this issue on different forums also and let's see what happens.

See you around






> **NikTh said:**
> Hello , 
the truth is that I cannot think anything else too. 

Weird problem . Hardware maybe ? did you try to unplug the battery and the AC adapter (of course while laptop is closed) and hold down the power button for at least 10 secs ? 

Then plugin the AC adapter and try again to see what happened . 

Thanks

---

### Post by NikTh on 2012-09-03
> **cesarmvb said:**
> Hi, NikTh
I have windows 7 installed (dual boot, kubuntu and windows 7) **and everything works perfect on windows...** Therefore, we can rule out hardware issues (fortunately)

Hello , 
then is not a hardware problem. You know, Windows (or a completely different O.S than Linux) is a good comparison. So you can say "Hey everything works perfect on Windows (or another O.S) , so is not a hardware problem". 

I think if is a problem with ACPI and PCI card ? (energy management) 
Or 
a wireless driver issue ? 

Can you give the results of 
```
lspci -nnk | grep -iA3 net
``` 

Thanks

---

### Post by cesarmvb on 2012-09-03
> **NikTh said:**
> Hello , 
then is not a hardware problem. You know, Windows (or a completely different O.S than Linux) is a good comparison. So you can say "Hey everything works perfect on Windows (or another O.S) , so is not a hardware problem". 

I think if is a problem with ACPI and PCI card ? (energy management) 
Or 
a wireless driver issue ? 

Can you give the results of 
```
lspci -nnk | grep -iA3 net
```Thanks

---------------------------

Sure, this is the result:

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
        Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
        Kernel driver in use: rtl8192ce
        Kernel modules: rtl8192ce
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
        Subsystem: Toshiba America Info Systems Device [1179:fcd3]
        Kernel driver in use: atl1c
        Kernel modules: atl1c

THANX!!

---

### Post by cesarmvb on 2012-09-03
(SOLVED)

Found the solution at:
[http://kb.wheretolookfor.me/content/install-wireless-driver-ubuntu-1010-realtek-8176](http://kb.wheretolookfor.me/content/install-wireless-driver-ubuntu-1010-realtek-8176)

It was a driver issue.
The above link tells you step by step how to install the correct driver.
I followed it, rebooted and tested it
wireless enabled+ac adapter plugged
wireless enabled+ac adapter plugged and ethernet cable plugged
ethernet cable plugged+ac adapter plugged
ethernet cable plugged+wireless enabled

All scenarios worked OK

I appreciate your support NikTh

---

### Post by NikTh on 2012-09-03
Hello , 

Glad you solved it. 

Please mark the thread as solved , by clicking on Thread Tools . 

Thanks

---

