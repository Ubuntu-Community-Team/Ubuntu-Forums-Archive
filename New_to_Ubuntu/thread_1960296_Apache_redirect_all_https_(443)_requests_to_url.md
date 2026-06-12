---
title: "Apache redirect all https (443) requests to url"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by aktiwers on 2012-04-17
I want to redirect all https requests (443) to another server, how can I do this in apache?

What I want to do is:

All https requests on [https://server1.com](https://server1.com)  redirect to [https://server2.com](https://server2.com)

Anyone knows how I can achieve this?

---

### Post by aktiwers on 2012-04-17
A silent bumb :P

---

### Post by Michael Dooley on 2012-04-17
This should be covered in an .htaccess file. Try googling "apache redirect 443" or "apache https redirect".

Good luck aktiwers.

---

### Post by aktiwers on 2012-04-17
I have googled already michael.. only seams to be able to find how to redirect port 80 to 443..

I wanna redirect all 443 requests to another server (url) port 80.

Could you share your findings or an example?
Thanks

---

### Post by SeijiSensei on 2012-04-17
You have to do this at the transport layer, I believe.  Otherwise the client will complain about a certificate mismatch.  

You can try using iptables or install an application-level proxy like [tcpproxy]("http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/proxies/TcpProxy").  I've used the latter to forward connections on port 443 to a server behind the firewall.

I don't think you can redirect an SSL request to an insecure server listening on port 80, though.  The client will expect there to be a certificated server on the other end and will start off by "handshaking" with the server and trying to exchange the encryption key.

---

### Post by aktiwers on 2012-04-18
Thanks SeijiSensei I will try it out.

Also I made a mistake, I didnt want to forward from 443 to 80, but from 443 to 443 on another server.

Cheers

---

