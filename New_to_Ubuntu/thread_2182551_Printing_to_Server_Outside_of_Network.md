---
title: "Printing to Server Outside of Network"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by samalex1014 on 2013-10-21
Hey,

I recently installed and set up a Samba and Cups print server on my Ubuntu server at home.  I was wondering if it was at all  possible to be able to print to it from outside of the network it is on.  I have configured a dynamic host, and can SSH in from the outside, but I haven't been able to find anything on printing to the server outside of the local network.  Is this at all possible? And, if so, how do I go about setting it up?

Thanks!

---

### Post by tgalati4 on 2013-10-21
Yes, it is possible.  Open port 631 on your router/firewall and send a print across the network.  This can have some security implications because anyone can send anything to that port to cause your printer to print something or to inject something malicious.  If it is within a subnet, but you still have outside (WAN) protection on port 631 then you should be OK.

There are some tips in the "Troubleshooting" section:  [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by samalex1014 on 2013-10-24
Ok, I have port 631 open.  How do I actually go about sending a print to there?  Do I have to install my printer on the machine I'm on?

---

### Post by SeijiSensei on 2013-10-24
Yes. Install CUPS on the client then point a browser at [http://localhost:631/](http://localhost:631/).  You'll get the CUPS admin page.  Follow the steps to Add a Printer.  You'll be prompted for your username and password when root ("sudo") privileges are required.

You might want to set the external port number to something other than 631 to obscure it.  Pick a number between 1024 and 65534, say 6631, and forward that port back to 631 on the print server.  Then in your client CUPS configuration specify 6631 rather than the default 631 value.

I believe you can also configure the print server to force a login before the print job is accepted.  That provides additional security.

---

### Post by tgalati4 on 2013-10-24
You generally want to pick a port between 11000 and 65534 since ports below 10K are reserved for other services.  You wouldn't want to clobber an existing service by accidently grabbing its port.

First test it with port 631 and see if it works as intended.  If it is something that you will use all of the time, then shift the port to a much higher number.  This is security by obscurity, not ideal, but it prevents common port 631 attacks.

If it is something that will only be used once a quarter--say to print out company quarterly reports--then set up a script or procedure to open the port 631, perform the print, then close the port.

It's a rare Use Case that you need to print over the network, when you can just as easily email or ssh-copy a PDF of the file and print it locally and securely.

---

### Post by SeijiSensei on 2013-10-24
> **tgalati4 said:**
> You generally want to pick a port between 11000 and 65534 since ports below 10K are reserved for other services.  You wouldn't want to clobber an existing service by accidently grabbing its port.you can just as easily email or ssh-copy a PDF of the file and print it locally and securely.

By definition I don't believe any port above 1023 can actually be "[reserved]("http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml")," though many of them have well-established customary assignments like 3128 for squid, 3306 for MySQL, and 5432 for PostgreSQL.  The file /etc/services includes a very complete list from [IANA]("http://www.iana.org").  You can quickly check a port number by using "grep port_number /etc/services" at the command prompt.  For instance, a "grep 6631 /etc/services" returns nothing, but "grep 5432 /etc/services" yields:

```
postgresql      5432/tcp        postgres        # PostgreSQL Database
postgresql      5432/udp        postgres

```

This assignment includes both TCP and UDP traffic, but many services just use one or the other.  SMTP uses TCP port 25; UDP traffic to this port has no assigned service.

The method I suggested of forwarding 6631 back to 631 shouldn't interfere with anything, since we're talking about the router's 6631 on its external address.  The server itself is unchanged and listening at 631.

---

### Post by samalex1014 on 2013-10-30
Ok, so from the client outside of the network, how do I go about this?  Let's say the host is UbuntuServer, the domain is printserver.org, and I'm attempting to print a PDF file.  Do I go to the browser and type something like [EMAIL="UbuntuServer@printserver.org:631"]UbuntuServer@printserver.org:631[/EMAIL] (theoretically, I'll be changing the external port tonight)?

---

