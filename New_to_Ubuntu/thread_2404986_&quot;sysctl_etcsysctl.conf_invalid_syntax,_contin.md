---
title: "&quot;sysctl: /etc/sysctl.conf: invalid syntax, continuing&quot;?"
date: 2018-10-31
forum: New to Ubuntu
---

### Post by %7#28K8 on 2018-10-31
Is there a mistake in what I added in the log? I don't remember what I originally added there but I added on the Martian and ICMP.

```
# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
net.ipv4.tcp_syncookies=1

# Do not accept ICMP redirects (prevent MITM attacks)
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#net.ipv4.conf.default.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0
&#8203;#
# Log Martian Packets
net.ipv4.conf.all.log_martians = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
&#8203;#
#
```

---

### Post by dino99 on 2018-10-31
As the other lines, let a space after #

#net.ipv4.conf.all.send_redirects = 0
#net.ipv4.conf.default.send_redirects = 0

---

### Post by deadflowr on 2018-11-01
There's a default sample sysctl.conf file in /usr/share/doc/procps/examples you can use as a compare to what you have to see what differs.

---

