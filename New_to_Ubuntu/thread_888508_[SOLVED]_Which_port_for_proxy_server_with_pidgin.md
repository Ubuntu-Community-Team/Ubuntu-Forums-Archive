---
title: "[SOLVED] Which port for proxy server with pidgin?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by t0p on 2008-08-13
I use a mobile phone as a modem with my computer.  I recently changed phone.

When using my old phone (which was on the Orange UK network) I could use pidgin for yahoo messenger.  But now, with my new phone (on T-Mobile) as modem, pidgin tells me it has lost connection, due to connection being dropped by peer.

I assume this is because T-Mobile is blocking IM traffic.  I want to try and get round this by using an anonymous proxy server.  There is a list of proxy servers at [http://www.samair.ru/proxy/]("http://www.samair.ru/proxy/"), and I'll see if one of those will work for me.  But, when configuring pidgin to use a proxy, it wants me to supply a port number.  And I don't know which port to specify.

Is there a particular port or port range that is used for IM?

---

### Post by ajmorris on 2008-08-13
hi there,
those proxies are HTTP proxies, i.e. they are for http traffic. You may need to forward a port range, manually specified in the pidgin properties, through T-Mobile. However, if it is a tunneling you are requiring, you could look into [http://your-freedom.net](http://your-freedom.net). It is a java application that routes traffic through it to its own proxy servers.
The easiest method of running it is to download the java package, and run java -jar freedom.jar.

AJ

---

### Post by t0p on 2008-08-13
:) Thanks for the tip ajmorris, I'll check it out!

**EDIT:**  OMG, they want paying! *Boo!!* :mad:

Can anyone tell me the port range I should give to a proxy server for pidgin?

---

### Post by t0p on 2008-08-13
Well, I solved my problem.  I used **Your Freedom**, a tunnelling app - info and download at [http://your-freedom.net]("http://your-freedom.net").  It's playing nicely with pidgin, and I also have a pdf user's manual to read.  I'm using the free service which comes with some restrictions, but it's okay.  Worth checking out if you have a mean ISP.

---

