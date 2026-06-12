---
title: "wireless keeps disconnecting in ubuntu 10.04"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by bh89 on 2012-07-27
Hello,

I am having a problem connecting to wireless networks, I can connect to the network, and everything works normally for ten or fifteen minutes before ubuntu disconnects. I am using a hp laptop running ubuntu 10.04.

thanks.

---

### Post by f1tz on 2012-07-27
Is this with all wireless networks, or just one? What does /var/log/syslog say when you are disconnected?

---

### Post by mapes12 on 2012-07-27
Try turning your router off then on again. And for us to look at your laptop wifi adapter then go to Terminal and do ```
sudo lshw -C network
``` and post the output back here.

BTW - have you got all the updates installed?

---

### Post by Petro Dawg on 2012-07-27
Could be an issue with the router, have you tested it on other networks? Do any other devices disconnect when on your network?

---

