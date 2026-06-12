---
title: "wireless problem"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by mspotter56 on 2008-10-13
I have just installed Ubuntu 8.04 on my Dell Inspiron 1525 laptop that has been running Vista SP1. I have a dual boot now. I booted into Ubuntu for the first time after installation today and had no wireless connection. I have an Apple Airport router that I have been using that Vista connected to fine. I tried to make a connection in Network Manager, but it did not even list my wireless network as an option. Can anyone tell me how to get Ubuntu to connect to my wireless network, step by step? I have a Dell WLAN Mini-card and my network SSID is Apple Network 373aae. Thanks for any help!

---

### Post by cheetaux on 2008-10-13
Open a terminal window and type the following command:

```
lspci
```

Report back the output.

---

### Post by mspotter56 on 2008-10-15
> **cheetaux said:**
> Open a terminal window and type the following command:

```
lspci
```

Report back the output.
Thanks for the response, here's what I got:

bash:1spci:command not found

---

### Post by nothingspecial on 2008-10-15
copy and paste please

```
lspci -v
```

Then copy and paste the output

---

### Post by superprash2003 on 2008-10-15
this link helped me [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

