---
title: "Software that will detect new computers on my network?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-04-29
Hi,

Is there software I can install that will detect when new computers or devices connect to my network?  Currently I have no idea when other devices log in or off.  I wouldnt know if someone unauthorized was on my network. 

Any ideas?

Thanks,
Rich

---

### Post by Monicker on 2008-04-29
Take a look at arpwatch or arpalert.  These will detect when a new mac address appears on the lan and can send email alerts to you.  

At a previous job I used arpwatch in conjunction with nmap to initiate port scans on new network devices, so I would get a nice email saying the mac address, ip address, and what open ports were found for the device.

---

