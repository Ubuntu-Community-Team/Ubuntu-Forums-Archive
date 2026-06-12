---
title: "Need simple mail server for system mails"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by lht2685 on 2012-05-17
Got any suggestions for a simple and very easy to configure mail server I can install on 10.04 or 12.04 server?

It is just to send out system emails (like backup completed) & bulk mail for our customers etc.

Something we can point an external Mx record at for <ourcompany>.info 

FYI We don't have an internal mail server, we use hosted and there are limits to the number of mail/day/user. 

I have been looking at this product([Axigen]("http://www.axigen.com/")), but not unsure if there is an easier way 

Thanks in advance

---

### Post by JKyleOKC on 2012-05-17
Take a look at postfix, which is in the repositories. It's a full-fledged mail server but can easily be configured for the simple needs you mention, and its documentation includes details for doing just that.

I've used it for this same purpose for years, and the only problem I've encountered is that my main mail server (at a third-party provider) refuses to accept any traffic from my AT&T IP address. I solved that by sending the affected traffic to a GMail account instead, which isn't so picky.

---

### Post by lht2685 on 2012-05-18
Hi JKyleOKC

Thanks for the reply, sounds like a great option!

Thank you :)

---

### Post by lht2685 on 2012-05-22
Got Postfix setup, but I got a problem sending mails to another internal mail server, I think it is because they access the internet though the same gateway/firewall.

I have added the other internal mail server to the hosts file, so if you ping mail.<mycompany>.co.uk it it will resolve the internal adr, but that does not seam to be enough.

The two servers are on the same network, so there is nothing internal to stop them talking to each other.

any suggestions?

---

### Post by kmyram on 2012-05-22
> **lht2685 said:**
> The two servers are on the same network, so there is nothing internal to stop them talking to each other.


Can you "telnet <server2> 25" from <server1> and get a response?

/Kasper

---

### Post by lisati on 2012-05-22
> **lht2685 said:**
> Got Postfix setup, but I got a problem sending mails to another internal mail server, I think it is because they access the internet though the same gateway/firewall.

I have added the other internal mail server to the hosts file, so if you ping mail.<mycompany>.co.uk it it will resolve the internal adr, but that does not seam to be enough.

The two servers are on the same network, so there is nothing internal to stop them talking to each other.

any suggestions?

You might want to look into something like Postfix's [transport_maps]("http://www.postfix.org/postconf.5.html#transport_maps") option to redirect mail to the internal IP address.

---

### Post by HermanAB on 2012-05-22
Nullmailer is as simple as it gets.

---

### Post by lht2685 on 2012-05-22
> **lisati said:**
> You might want to look into something like Postfix's [transport_maps]("http://www.postfix.org/postconf.5.html#transport_maps") option to redirect mail to the internal IP address.

:guitar: Thank you!


Fixed, here is how (for others that may be in the same boat)

in /etc/postfix/main.cf add the following line
```

transport_maps = hash:/etc/postfix/transport

```

create or edit /etc/postfix/transport
```

<mycompany>.co.uk smtp:[192.168.1.xxx]
<mycompany>.com smtp:[192.168.1.yyy]

```
or
```

example.co.uk smtp:insidesmtp.example.co.uk
example.com smtp:insidesmtp.example.com

```


Execute 
```

postmap hash:/etc/postfix/transport

```
to build the db required (do it every time you change the file)

Execute 
```

postfix reload

```
to restart the mail server

---

