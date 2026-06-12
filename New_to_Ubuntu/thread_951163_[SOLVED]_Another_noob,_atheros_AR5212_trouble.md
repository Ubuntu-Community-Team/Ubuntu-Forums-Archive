---
title: "[SOLVED] Another noob, atheros AR5212 trouble"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Krone1 on 2008-10-17
Hello, I've messed around for several hours, I just can't seem to find a solution.  It seems to me that I need madwifi, I downloaded it but I don't know how to proceed.  I have an IBM T42 laptop, built in wireless.  The hardware shows up in Admin/network, also admin/hardware drivers.  Sometimes I get the signal strength applet but never a connection.
uname -r is 2.6.24-21-generic.

lspci
...02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:206376  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks in advance

Mark

---

### Post by wolfen69 on 2008-10-17
since ubuntu 8.10 is less than 2 weeks away, why not download and try the live cd? for a customer of mine it was the only linux distro that worked good on his IBM thinkpad. otherwise you could try ndiswrapper to get the wireless going.

---

### Post by Krone1 on 2008-10-17
Thanks for the suggestion wolfen69, I saw in other posts that the new version would be better.  However, some other post had recommended to turn off then on the router.  I did this and presto, wireless is working!  So simple after all that messing around!

---

