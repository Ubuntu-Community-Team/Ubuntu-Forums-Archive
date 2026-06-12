---
title: "How to read OpenVPN VPN status and log files"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by walterdowis on 2014-01-06
Hi all, 
    I'm a newbi to Linux and Ubuntu.  When I have OpenVPN VPN running, where are the OpenVPN VPN status and log files located and how can I read them?

---

### Post by nerdtron on 2014-01-07
The OpenVPN log file is defined on the server.conf file. And the verbosity of the log is also defined in the server.conf file.
The file is not defined by by default so you should explicitly define it.

Here's the logging part on our vpn server:
```

....
status openvpn-status.log
log-append  openvpn.log
verb 4
...

```

Since the config file is in /etc/openvpn/server.conf, then the log file openvpn-status.log will be saved in /etc/openvpn/openvpn-status.log
The verbosity is 4, you can changed it to 5 or 6 if you need more info when you troubleshoot connections.

---

