---
title: "Which FTP Server Supports SSL On the Control Channel Only?"
date: 2015-08-16
forum: New to Ubuntu
---

### Post by lambdafox on 2015-08-16
I see that glftpd, Pure-FTPd, vsftpd, proftpd are all recommended for different situations, but I cannot figure out which, if any of them, will allow me to use TLS on the control channel only.  [(like this...)]("http://blogs.msdn.com/b/vijaysk/archive/2009/07/08/iis-7-tip-11-you-can-restrict-ssl-to-only-the-control-channel-on-ftps.aspx")

Here is a link to

---

### Post by sandyd on 2015-08-16
The closest I could find was on pure-ftpd:
From the [README]("http://download.pureftpd.org/pub/pure-ftpd/doc/README.TLS"):
>    ------------------------ ACCEPTING TLS SESSIONS ------------------------

Once the certificate has been installed, you need to start a TLS-enabled
pure-ftpd daemon with the -Y (or --tls=) switch. Example :

/usr/local/sbin/pure-ftpd --tls=1 &

- With "--tls=0", support for SSL/TLS is disabled. This is the default.

- With "--tls=1", clients can connect either the traditional way or through an
SSL/TLS layer. This is probably the setting you need if you want to enable
TLS without having too much angry customers.

- With "--tls=2", cleartext sessions are refused and only SSL/TLS compatible
clients are accepted.

- With "--tls=3", cleartext sessions are refused and only SSL/TLS compatible
clients are accepted. Clear data connections are also refused, so private
data connections are enforced. This is an extreme setting.

When SSL/TLS has been successfully negociated for a connection, you'll see
something similar to this in log files :

<<
SSL/TLS: Enabled TLSv1.2 with AES256-SHA, 256 secret bits cipher
Seems like with --tls=2, people can connect only using SSL/TLS on the control channel, but have the choice of connecting either with SSL/TLS or unencrypted on the data channel (inference made based on --tls=3).

---

### Post by lambdafox on 2015-08-17
> **sandyd said:**
> The closest I could find was on pure-ftpd:
...

Seems like with --tls=2, people can connect only using SSL/TLS on the control channel, but have the choice of connecting either with SSL/TLS or unencrypted on the data channel (inference made based on --tls=3).

Thank you for the clarification.   I read that yesterday, but wasn't sure that was what it meant!.  I have messed around with proftpd and pure-ftpd.  proftpd, although infinitely configurable, is a bit too complicated for me.  Thank you again.

---

