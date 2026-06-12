---
title: "Cannot install proftpd"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Me+ on 2008-07-15
Hi

I have had prfoftpd installed before (dont know if this is a problem)

Heres what i get:

> sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
proftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 210 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up proftpd (1.3.0-21ubuntu1) ...
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'Unspecified' error: No address associated with hostname
 - Fatal: TLSRSACertificateFile: '/etc/gproftpd/gproftpd/gproftpd.pem' does not exist on line 90 of '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?

Thanks

---

### Post by jspolen on 2008-07-15
try removing it by going into your synaptic package manager. Remove anything that contains proftpd. 

Then try "sudo apt-get install proftpd" once more.

It looks like you have not completely removed it.

Do you have any other ftp servers installed?

---

### Post by Dedoimedo on 2008-07-15
Hi,

Do you have the file gproftpd.pem located where it says, under:

/etc/gproftpd/gproftpd/gproftpd.pem

By the way, why two sublocations? Try manually creating a certificate to see if this works.

See this for details ...

[http://www.tc.umn.edu/~brams006/selfsign.html](http://www.tc.umn.edu/~brams006/selfsign.html)

Then, lastly, convert the .csr to .pem

```
openssl x509 -inform der -in certificate.csr -out certificate.pem
```

Then, try to reinstall ...

Hope this helps.

Cheers,
Dedoimedo

---

