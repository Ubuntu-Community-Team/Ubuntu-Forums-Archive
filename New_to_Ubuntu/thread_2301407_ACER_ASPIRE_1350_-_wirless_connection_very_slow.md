---
title: "ACER ASPIRE 1350 - wirless connection very slow"
date: 2015-11-02
forum: New to Ubuntu
---

### Post by chicky2 on 2015-11-02
Hi all,

first of all, i'm sorry for my english :P

I have a Aspire 1350 PC with latest Lubuntu distro, it's all good but i have problem with wirless connection.

It 's very very very slow, now i'm posting in ethernet connection mode instead with wifi i wait just an hour for charging a single page of google search...i don't know why, maybe the driver is not good?

I don't know any terminal command line but if you teach me in easy way :D ..... i try

Thanks

root@luca-Aspire-1350:~#iwconfig
lo        no wireless extensions.

wlp0s9    IEEE 802.11b  ESSID:"Vodafone-Tobia"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:89:E1:BD:8C   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/100  Signal level=63/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:625  Invalid misc:35   Missed beacon:0

enp0s18   no wireless extensions.


root@luca-Aspire-1350:~# lspci -k
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC
    Kernel driver in use: rtl818x_pci

---

