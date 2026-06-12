---
title: "Stunnel with Usenet"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by OmegaSix on 2008-11-16
I have attempted to set up a SSL Tunnel using Stunnel4 for usenet to no avail. I have properly installed and set up Stunnel4 according to all the posts/guides I have found and my usenet client will not connect. I'm using Klibido as my client, setting it to connect to localhost (127.0.0.1) port 119 and it just idles and does nothing. When I attempt to start Stunnel4 from console I get the following:

#stunnel

2008.11.16 06:34:59 LOG7[7034:3083544240]: Snagged 64 random bytes from /root/.rnd
2008.11.16 06:34:59 LOG7[7034:3083544240]: Wrote 1024 new random bytes to /root/.rnd
2008.11.16 06:34:59 LOG7[7034:3083544240]: RAND_status claims sufficient entropy for the PRNG
2008.11.16 06:34:59 LOG7[7034:3083544240]: PRNG seeded successfully
2008.11.16 06:34:59 LOG7[7034:3083544240]: Certificate: /etc/stunnel/stunnel.pem
2008.11.16 06:34:59 LOG7[7034:3083544240]: Certificate loaded
2008.11.16 06:34:59 LOG7[7034:3083544240]: Key file: /etc/stunnel/stunnel.pem
2008.11.16 06:34:59 LOG7[7034:3083544240]: Private key loaded
2008.11.16 06:34:59 LOG7[7034:3083544240]: SSL context initialized for service stunnel
inetd mode must define a remote host or an executable

I'm not very experienced with Unix/Linux and I'm at a total loss. Any sugestions would be greatly appreciated.

EDIT: Also when I check the process list stunnel does not even seem to be running.

---

### Post by ColinLouie on 2009-04-22
> **OmegaSix said:**
> I have attempted to set up a SSL Tunnel using Stunnel4 for usenet to no avail. I have properly installed and set up Stunnel4 according to all the posts/guides I have found and my usenet client will not connect. I'm using Klibido as my client, setting it to connect to localhost (127.0.0.1) port 119 and it just idles and does nothing. When I attempt to start Stunnel4 from console I get the following:

#stunnel

2008.11.16 06:34:59 LOG7[7034:3083544240]: Snagged 64 random bytes from /root/.rnd
2008.11.16 06:34:59 LOG7[7034:3083544240]: Wrote 1024 new random bytes to /root/.rnd
2008.11.16 06:34:59 LOG7[7034:3083544240]: RAND_status claims sufficient entropy for the PRNG
2008.11.16 06:34:59 LOG7[7034:3083544240]: PRNG seeded successfully
2008.11.16 06:34:59 LOG7[7034:3083544240]: Certificate: /etc/stunnel/stunnel.pem
2008.11.16 06:34:59 LOG7[7034:3083544240]: Certificate loaded
2008.11.16 06:34:59 LOG7[7034:3083544240]: Key file: /etc/stunnel/stunnel.pem
2008.11.16 06:34:59 LOG7[7034:3083544240]: Private key loaded
2008.11.16 06:34:59 LOG7[7034:3083544240]: SSL context initialized for service stunnel
inetd mode must define a remote host or an executable

I'm not very experienced with Unix/Linux and I'm at a total loss. Any sugestions would be greatly appreciated.

EDIT: Also when I check the process list stunnel does not even seem to be running.

You need to set the following (default is 0 in Ubuntu 8.10 desktop):

/etc/default/stunnel4
ENABLED=1

/etc/init.d/stunnel4
ENABLED=1

then, restart stunnel using:
sudo /etc/init.d/stunnel4 restart

The first one in /etc/default is required to make stunnel work in daemon mode. I assume the one in /etc/init.d is for boot time startup.

Cheers!

---

