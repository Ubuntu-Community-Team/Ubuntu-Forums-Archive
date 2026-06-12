---
title: "VSFTPD problem"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by schoft on 2012-08-26
I can only access my VSFTPD server from internally. External connections, from the internet, don't work and the ftp client says:

> Command:    PASV
Response:    227 Entering Passive Mode (192,168,133,7,47,76).
Status:    Server sent passive reply with unroutable address. Using server address instead.
Command:    LIST
Error:    Connection timed out
Error:    Failed to retrieve directory listingMy server: 192.168.133.7
Ports forwarded correctly

I'm suspecting there is something wrong with my /etc/hosts file. I remember having this problem a year ago and doing something to /etc/hosts to make it work...

> 127.0.0.1       localhost
127.0.1.1       box
192.168.133.7   domain.be

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
Any idea ?!

Maybe change the listen_address in my vsftpd.conf to my internet address?

---

