---
title: "[python] pcapy - setting timeout??"
date: 2009-11-06
forum: Programming Talk
---

### Post by pokerbirch on 2009-11-06
I'm using the pcapy library to monitor a local client/server app. I need to be able to stop the pcap_loop if no data has been received for about 20 seconds, however i can't find any information regarding this. Google hasn't helped me much. Any suggestion from you more knowledgeable folks?

---

### Post by kripkenstein on 2009-11-06
I'm not familiar with pcap, but a quick google seems to say that calling pcap_breakloop will halt pcap_loop. So how about starting a thread before calling pcap_loop, and after 20 seconds it calls pcap_breakloop?

---

### Post by pokerbirch on 2009-11-06
I was looking at pcap_breakloop but as far as i understand, it will only break the loop after the next packet arrives. For my own application, this is obviously a problem because i need to detect when packets are no longer being received, and THEN break the loop and exit my script...so the loop will never break because the final packet will never arrive!

A quick Google confirms this problem: [http://osdir.com/ml/network.tcpdump.devel/2006-06/msg00046.html](http://osdir.com/ml/network.tcpdump.devel/2006-06/msg00046.html)

Have decided to check out some alternatives and am currently looking at a raw socket implementation which will also allow me to remove the dependency on pcapy.

---

### Post by pokerbirch on 2009-11-06
Have decided to go for the raw socket option. It's actually easier to work with than pcapy.

[http://oss.coresecurity.com/impacket/sniffer.py](http://oss.coresecurity.com/impacket/sniffer.py)

---

