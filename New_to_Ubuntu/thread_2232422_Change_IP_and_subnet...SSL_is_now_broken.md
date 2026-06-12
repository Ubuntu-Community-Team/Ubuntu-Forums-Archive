---
title: "Change IP and subnet...SSL is now broken?"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by WhatIsChazaq on 2014-07-01
I loaded 14.04 via USB at work, brought it home and gave it a static IP on my home network.

I was logging in to a service at work to [https://xx.xx.xx.xx:7443](https://xx.xx.xx.xx:7443) with no problems. Now I get "SSL connection error".

Webmin is still working from [https://xxx.xxx.xxx:10000](https://xxx.xxx.xxx:10000)

Also...I can no longer SSH into the new IP address (using Putty). PuTTY Fatal Error "Server unexpectedly closed network connection"

What gives?

---

### Post by cariboo on 2014-07-02
You can see what's happening with ssh by using the following command:

```
ssh user@server -vvv
```

---

### Post by WhatIsChazaq on 2014-07-02
debug1: Reading configuration data /etc/ssh/ssh_config                          
debug1: /etc/ssh/ssh_config line 19: Applying options for *                     
ssh: Could not resolve hostname server: Name or service not known               
donaldsonclan@A860:~$

---

