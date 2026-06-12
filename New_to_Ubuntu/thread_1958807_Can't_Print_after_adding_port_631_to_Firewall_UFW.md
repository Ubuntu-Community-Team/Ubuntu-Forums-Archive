---
title: "Can't Print after adding port 631 to Firewall UFW"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by Nalcap657 on 2012-04-14
I have an HP Photosmart C4700.  I have enabled the Uncomplicated firewall for Ubuntu 11.10.  I can connect and print to the printer when all outgoing is allowed under UFW.  I have Been using GUFW and when i deny outgoing and add "allow out port 631" for both TCP and UDP i cannot print.

IPP and Localhost: 631

Don't Know if maybe there is another port it will
accept have also tried 515 and 9100.

---

### Post by Lemuriano on 2012-04-14
Hi,

I allow port 515/tcp and 1155/udp and was able to print without any problem.

Hope this help,
Regards.

---

