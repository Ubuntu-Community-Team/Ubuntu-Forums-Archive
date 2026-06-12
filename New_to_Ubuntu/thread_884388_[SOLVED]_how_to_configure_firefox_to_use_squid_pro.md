---
title: "[SOLVED] how to configure firefox to use squid proxy"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-08
h guys , i am kinda new to this squid proxy thing i have heard about squid can cache the website and helpful in loading pages quickly but how to configure firefox to use squid as proxy i tried that local host an 127.0.0.1  but my firefox wasnt able to connect after it so i removed it and also i am till confused with squid configuration

---

### Post by RealPSL on 2008-08-09
Use the instructions [here]("http://doc.ubuntu.com/ubuntu/serverguide/C/squid.html") to configure squid. You will need the IP address and port number for the squid server. You should also use an acl when configuring the squid to ensure that only your desired clients can use it.

To configure firefox once you have a working configuration 

Edit > Preferences > Advanced Tab > Network > Settings

Enter the proxy information from above.

---

