---
title: "Java Socket/Networking"
date: 2012-05-07
forum: Programming Talk
---

### Post by 3246251196 on 2012-05-07
Hi guys,

I have a client and server (both on different computers on the same network) that talk to each other fine when they are both on the same operating system. Now, let me run the server on Windows and run a client on Linux and there are problems:

- UnknownHostException
- ConnectionRefused

There seems to be some difference with the host name?

---

### Post by dwhitney67 on 2012-05-08
> **3246251196 said:**
> Hi guys,

I have a client and server (both on different computers on the same network) that talk to each other fine when they are both on the same operating system. Now, let me run the server on Windows and run a client on Linux and there are problems:

- UnknownHostException
- ConnectionRefused

There seems to be some difference with the host name?

Your assumption is incorrect.  An UnknownHostException means that the client cannot determine the server's IP address.  A ConnectionRefused implies that the client was denied the opportunity to connect to the server.

If you do not have a DNS running on your local network, try connecting to the IP address, not the host name.

When running a server on a system, the easiest way to determine if it is possible to connect to it is using 'telnet'.  The other option, on the server system, is to verify using 'netstat' if the port is indeed bound to the appropriate network interface.

Since your server is running on Windows, I would also check to see if the firewall is enabled.

There are also other reasons why a client may not be able to connect to a server (e.g. /etc/hosts.allow and /etc/hosts.deny), however I'm unfamiliar with Windows, thus I do not know how the rules in these Linux files translates to Windows.

---

