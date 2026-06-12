---
title: "DVB tunung guide Belmont transmitter"
date: 2006-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by gary101 on 2006-11-03
I searched the web for over a week looking for info on DVB tuning for the Belmont transmitter in Lincolnshire. In the end I created my own file and can confirm that I have had it working for Kaffeine and dvb-utils scan.

Hope the info save someone alot of time.

Gary

## Tuning info for BELMONT
## Save this file as 'uk-Belmont' and
## save in /usr/share/doc/dvb-utils/example/scan/dvb-t to use scan from terminal
## save in .kde/share/apps/kaffeine etc to use in Kaffeine
##
## Uncomment one of the lines below

# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
#T 690000000 8MHz 1/2 NONE QAM16 2k 1/32 NONE

# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
#T 766167000 8MHz 1/2 NONE QAM16 2k 1/32 NONE

# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
#T 786000000 8MHz 1/2 NONE QAM16 2k 1/32 NONE

# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
#T 834000000 8MHz 1/2 NONE QAM16 2k 1/32 NONE

# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
#T 850000000 8MHz 1/2 NONE QAM16 2k 1/32 NONE

---

