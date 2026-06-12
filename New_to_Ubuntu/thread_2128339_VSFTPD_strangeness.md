---
title: "VSFTPD strangeness"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by DefiniteIntegral on 2013-03-22
Hi,

I am experiencing some strange behavior with vsftpd. It is actually working but the configuration doesn't make much sense. This pertains to PASV mode settings.

My /etc/vsftpd.conf is configured like this:
pasv_enable=YES
pasv_address=<WAN IP address>
pasv_min_port=20000
pasv_max_port=21000

Setting it like this causes PASV connections to time out. However if I change to this:

pasv_address=127.0.0.1

then my FTP client complains with this message:

Command:    PASV
Response:    227 Entering Passive Mode (127,0,0,1,79,15).
Status:    Server sent passive reply with unroutable address. Using server address instead.

yet PASV mode does work after that. 

This makes no sense because my server is NOT behind a NAT, it is directly exposed to WAN, also iptables is allowing ALL incoming traffic so there should be no problem. Since the client indicates "Using server address instead" and it works, I am stumped as to why putting the exact same server address for pasv_address would not work. I have quadruple checked I was entering the correct IP. I also tried adding the ip_conntrack_ftp module to iptables which made no difference, as well as adding a specific rule to iptables to allow the passive ftp traffic through, even though that is basically redundant.

It isn't exactly critical because it does work, but I'd prefer to have a correct configuration. If anyone has an idea please let me know.

---

