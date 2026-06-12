---
title: "Port 25 pls help"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by ahbb on 2008-07-01
Hi there,

Iv set up pine and all but keep getting error about port 25.

I try to telnet into it, but then get this msg.

root@shells:# telnet localhost 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

Where can i go and have a look to open it?

Please advice.

Thanks

Andrew

---

### Post by brian_p on 2008-07-01
> **ahbb said:**
> Hi there,

Iv set up pine and all but keep getting error about port 25.

I try to telnet into it, but then get this msg.

root@shells:# telnet localhost 25
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

Where can i go and have a look to open it?


Sounds like you need an MTA (Mail Transport Agent). exim or postfix would do.

---

### Post by imolafem on 2008-07-01
Pine is a program to read mail.  By connecting to port 25 it sounds like you are trying to connect to a mail server, not a client such as pine.  Pine would be used to talk to your ISP to get your email.  You want to install a mail daemon on your local server if you want to use it to send mail without talking to your ISP.

---

### Post by ahbb on 2008-07-01
Hi there,

Im am running postfix but keep on getting this error regarding it as well.

Maybe you can shed some light on it for me pls?

 * Reloading Postfix configuration...                                                                                        postfix/postfix-script: fatal: the Postfix mail system is not running
                                                                                                                      [fail]

Thanks

Andrew

---

### Post by ahbb on 2008-07-01
HI,

What mail deomon would you say is the best to use then?

ta

Andrew

---

### Post by brian_p on 2008-07-01
> **ahbb said:**
> Hi there,

Im am running postfix but keep on getting this error regarding it as well.

Maybe you can shed some light on it for me pls?

 * Reloading Postfix configuration...                                                                                        postfix/postfix-script: fatal: the Postfix mail system is not running
                                                                                                                      [fail]

Do you get that when you do

```
sudo /etc/init.d/postfix restart


```

I'm familiar with exim but not postfix. How do you go on with

```
dpkg-reconfigure postfix
```

This link could be helpful

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by ahbb on 2008-07-01
Hi Brian,

I done everything they say on the url you gave me.

But now i get this when i restart the postfix.

root@shells:/etc/postfix# sudo /etc/init.d/postfix restart
 * Stopping Postfix Mail Transport Agent postfix                                                                      [ ok ]
 * Starting Postfix Mail Transport Agent postfix                                                                             postfix: warning: inet_protocols: IPv6 support is disabled: Address family not supported by protocol
postfix: warning: inet_protocols: configuring for IPv4 support only
  
Iv tried to telnet in to port 25 as well and it still dont want to work.

Hope you can advice me to what mite the problem..

Thanks

Andrew

---

### Post by ahbb on 2008-07-01
Iv fixed the IPV6 took that out of master.cf file so that is sorted when i restart it i get this msg now.

root@shells:/etc/postfix# sudo /etc/init.d/postfix reload
 * Reloading Postfix configuration...                                                                                        postfix/postfix-script: fatal: the Postfix mail system is not running
                                                                                                                      [fail]
root@shells:/etc/postfix#

It does not give me a reason or a proper error msg that I could go and have a look to see what is wrong....

Thanks

Andrew

---

### Post by alez1601 on 2008-07-29
you can try axigen mail server ([www.axigen.com](www.axigen.com))

they have a full featured 5 mboxes free edition and you will find video tutorials on how to install it and set it up. you also have support from them on their forum.

---

