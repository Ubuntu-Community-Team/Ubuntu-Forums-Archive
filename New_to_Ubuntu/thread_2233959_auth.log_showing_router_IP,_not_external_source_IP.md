---
title: "auth.log showing router IP, not external source IP"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by hatfield2 on 2014-07-11
Hello all, I've been struggling with this problem all week and so far have had no luck with Google.

I've installed Ubuntu Server 14.04, OpenSSH and Denyhosts on a server which is behind a Tenda W300D ADSL modem / router with port-forwarding for ports 80 and 22.   

Looking at auth.log all the attempted logins are recorded as coming from the router's LAN-side IP (192.168.1.1) which then results in the router's LAN-side IP being picked up by Denyhosts with the result that it then blocks me from logging in from the WAN.  Therefore, I either leave SSH open to brute force login attempts or lose the ability to SSH from outside my LAN.

My understanding is that
[LIST=1]
[*]Denyhosts picks  up the details of attempted logins from the auth.log file (so I assume it is not an issue with Denyhosts) and
[*]When the router forwards an external packet, whilst it changes my external IP (the destination IP address of the packet) to the LAN IP of the server (192.168.1.xx) it should not alter the original source IP (being the external WAN address) of the person attempting to log in.  If the server responds to the external packet it would use the original external originating address as the return destination and my LAN would identify this as not being an internal LAN address and therefore send it to the router for transmission to the WAN  (so it does not seem to be a problem with the router)
[*]As the incoming login attempts therefore presumably still carry the original external WAN source address it seems there must be something up in how auth.log logs these attempts.
[/LIST]

Is there some configuration step I need to do so that the external WAN source address of incoming login attempts, rather than my router's internal LAN address is shown in auth.log? 

Any help gratefully received!

---

### Post by ultrabutu on 2014-07-13
Sorry I can't offer help, but I read your post with great interest because I'm about to attempt something similar.   I suppose forth comming pleas for help are in the pipe line from me.

---

### Post by The Cog on 2014-07-13
I would suggest that since the login attempts come from your router's IP address, then maybe your router has been compromised. I would try to confirm with tcpdump that the log is giving you the correct address though. Use a command like this:
**sudo tcpdump tcp port 22**
leave it running and see if the packets shown in tcpdump match the log reports.

---

### Post by SeijiSensei on 2014-07-13
I suspect it has nothing to do with a compromise but is a consequence of using "network address translation."

If the router uses NAT to connect between your local private network and the Internet, then there is no way for the external IP addresses of remote machines to be logged on your server.  Every connection will appear to come from the router's address.  The only way to see the actual remote IPs is to connect the server directly to the Internet with a public IP address.  Alternatively, if you can configure logging on the router, you can log the traffic there.  You could probably do this if you run something like dd-wrt or tomato on the router.

NAT works well for client-side operations but poses problems like these for servers.

---

### Post by Vladlenin5000 on 2014-07-13
> **SeijiSensei said:**
> If the router uses NAT to connect between your local private network and the Internet, then there is no way for the external IP addresses of remote machines to be logged on your server.  Every connection will appear to come from the router's address.  The only way to see the actual remote IPs is to connect the server directly to the Internet with a public IP address.  Alternatively, if you can configure logging on the router, you can log the traffic there.  You could probably do this if you run something like dd-wrt or tomato on the router.

+1 +1 +1

---

### Post by Doug S on 2014-07-13
> **SeijiSensei said:**
> I suspect it has nothing to do with a compromise but is a consequence of using "network address translation."

If the router uses NAT to connect between your local private network and the Internet, then there is no way for the external IP addresses of remote machines to be logged on your server.  Every connection will appear to come from the router's address.  The only way to see the actual remote IPs is to connect the server directly to the Internet with a public IP address.  Alternatively, if you can configure logging on the router, you can log the traffic there.  You could probably do this if you run something like dd-wrt or tomato on the router.

NAT works well for client-side operations but poses problems like these for servers.Seiji: I follow your posts avidly, however in this case I disagree. What the OP described should be what is observed. The original external source IP address will be presented to the internal server and it should know who is trying to log in. Here is an excerpt from one time when I had my internal test server connected to internet via port forwarding on my router (another Ubuntu server box at internal = 192.168.111.1 and external = 173.180.45.4), and I accessed it from another computer at my 2nd external IP address:```
173.180.45.3 - - [26/Feb/2014:21:05:46 -0800] "GET / HTTP/1.1" 200 1008 "-" "Mozilla/5.0 (Windows NT 6.0; rv:27.0) Gecko/20100101 Firefox/27.0"
173.180.45.3 - - [26/Feb/2014:21:05:46 -0800] "GET /includes/smythies.css HTTP/1.1" 200 1013 "http://smythies.com:8083/" "Mozilla/5.0 (Windows NT 6.0; rv:27.0) Gecko/20100101 Firefox/27.0"
173.180.45.3 - - [26/Feb/2014:21:05:46 -0800] "GET /favicon.ico HTTP/1.1" 200 1445 "-" "Mozilla/5.0 (Windows NT 6.0; rv:27.0) Gecko/20100101 Firefox/27.0"
173.180.45.3 - - [26/Feb/2014:21:06:12 -0800] "GET /blog HTTP/1.1" 301 564 "-" "Mozilla/5.0 (Windows NT 6.0; rv:27.0) Gecko/20100101 Firefox/27.0"
173.180.45.3 - - [26/Feb/2014:21:06:12 -0800] "GET /blog/ HTTP/1.1" 404 404 "-" "Mozilla/5.0 (Windows NT 6.0; rv:27.0) Gecko/20100101 Firefox/27.0"
...
```

---

### Post by SeijiSensei on 2014-07-13
You were running a Linux box as a router.  Commercial routers may or may not handle the situation correctly.  I have no experience with the OP's Tenda W300D, but the couple of reviews I glanced at stressed how cheap it was.  Maybe it's just not very well designed?

If the router simply uses NAT to masquerade all incoming traffic as originating on its internal interface, then the OP will be unable to view the external addresses in the server's log.

---

### Post by Vladlenin5000 on 2014-07-13
Here the manual for Tenda W300D (v5.0 - released in 2012): [http://www.tenda.cn/tendacn/DownLoads/show.aspx?downid=1160](http://www.tenda.cn/tendacn/DownLoads/show.aspx?downid=1160)

(Just for fun... I doubt you can extract meaningful information concerning this case there)

---

### Post by hatfield2 on 2014-07-13
Thanks for your help everyone.

Turns out it was the router, having swapped it for an older Edimax AR 7084 router all seems to be working as it should and auth.log is now picking up the external WAN addresses of the various connection attempts.

Good luck with your setup, ultrabutu, looks like it may be a bit of pot luck in choosing a router.

```
Jul 13 20:59:09 ubuntu sshd[11835]: reverse mapping checking getaddrinfo for 197.51.174.61.dial.wz.zj.dynamic.163data.com.cn [61.174.51.197] failed - POSSIBLE BREAK-IN ATTEMPT!Jul 13 20:59:09 ubuntu sshd[11835]: User root from [61.174.51.197]("tel:61.174.51.197") not allowed because not listed in AllowUsers
Jul 13 20:59:09 ubuntu sshd[11835]: input_userauth_request: invalid user root [preauth]
Jul 13 20:59:10 ubuntu sshd[11835]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=[61.174.51.197]("tel:61.174.51.197")  user=root
Jul 13 20:59:11 ubuntu sshd[11835]: Failed password for invalid user root from [61.174.51.197]("tel:61.174.51.197") port 37948 ssh2
Jul 13 20:59:24 ubuntu sshd[11835]: message repeated 5 times: [ Failed password for invalid user root from [61.174.51.197]("tel:61.174.51.197") port 37948 ssh2]
Jul 13 20:59:24 ubuntu sshd[11835]: Disconnecting: Too many authentication failures for root [preauth]
Jul 13 20:59:24 ubuntu sshd[11835]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=[61.174.51.197]("tel:61.174.51.197")  user=root
Jul 13 20:59:24 ubuntu sshd[11835]: PAM service(sshd) ignoring max retries; 6 > 3
Jul 13 20:59:25 ubuntu sshd[11837]: Set /proc/self/oom_score_adj to 0
Jul 13 20:59:25 ubuntu sshd[11837]: refused connect from [61.174.51.197]("tel:61.174.51.197") ([61.174.51.197]("tel:61.174.51.197"))
Jul 13 20:59:26 ubuntu sshd[11838]: Set /proc/self/oom_score_adj to 0
Jul 13 20:59:26 ubuntu sshd[11838]: refused connect from [61.174.50.224]("tel:61.174.50.224") ([61.174.50.224]("tel:61.174.50.224"))
Jul 13 20:59:36 ubuntu sshd[11839]: Set /proc/self/oom_score_adj to 0
Jul 13 20:59:37 ubuntu sshd[11839]: refused connect from [61.174.51.197]("tel:61.174.51.197") ([61.174.51.197]("tel:61.174.51.197"))
Jul 13 20:59:46 ubuntu sshd[11840]: Set /proc/self/oom_score_adj to 0
Jul 13 20:59:46 ubuntu sshd[11840]: refused connect from [61.174.50.224]("tel:61.174.50.224") ([61.174.50.224]("tel:61.174.50.224"))
Jul 13 21:00:20 ubuntu sshd[11841]: Set /proc/self/oom_score_adj to 0
Jul 13 21:00:20 ubuntu sshd[11841]: refused connect from [61.174.51.197]("tel:61.174.51.197") ([61.174.51.197]("tel:61.174.51.197"))
Jul 13 21:01:48 ubuntu sshd[11842]: Set /proc/self/oom_score_adj to 0



```

---

