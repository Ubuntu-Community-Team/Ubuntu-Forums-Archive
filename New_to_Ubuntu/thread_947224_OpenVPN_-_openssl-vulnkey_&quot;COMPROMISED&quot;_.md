---
title: "OpenVPN - openssl-vulnkey &quot;COMPROMISED&quot; key problem"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by laleelay on 2008-10-14
Hi!

SUMMARY: I have a nasty problem with my OpenVPN passphrase-protected certificate which openssl-vulnkey reports as COMPROMISED. This is not the standard problem of out-dated certificate.

DETAILS: System: Ubuntu 8.04, all current updates. Openvpn passphrase-protected certificate, issued 1 day ago by our SysAdmin (i.e. the key is not old, not pre-may 2008 )

PROBLEM: When I try to connect i got this output:
```
ERROR: key.key is a known vulnerable key. See 'man openssl-vulnkey' for details.
Exiting
$ openvpn-vulnkey key.key
Not blacklisted: #### key.key
$ openssl-vulnkey key.key
COMPROMISED: #### key.key
```

OpenVPN under Windows CAN CONNECT. The problem is only under my Ubuntu. 

I have read some articles and understood that initially the problem could be that the certificate is too old. Then my SysAdmin re-issued the certificate, but NOOO, the problem is there:)

I have also found out solutions which basically render the openssl-vulnkey check invalid. I do not like it as an approach.

The most logical approach now for me is to add a single exception for this specific key, as I know it is from a safe source (openssl-blacklist?) However, I do not know how to do this. Any advice? Any other solutions?

Thanks to you all!

---

### Post by laleelay on 2008-10-15
Well, I needed my work done so I chose the approach to ignore the openssl-vulnkey check. I know this is bat but could not figure anything better.

I followed this advice: 
[http://www.annoying.dk/2008/07/15/error-clientkey-is-a-known-vulnerable-key-see-man-openssl-vulnkey-for-details/ ](http://www.annoying.dk/2008/07/15/error-clientkey-is-a-known-vulnerable-key-see-man-openssl-vulnkey-for-details/ ) 
ONLY FOR THE openssl-vulnkey part, which basically tells you to make a soft link to the /bin/true file, e.g. rendering any openssl-vulnkey check as positive.

One small note: on my system the openssl-vulnkey was located in /usr/bin, not in /usr/sbin as stated in the article above

I will post the problem in a mail group and if smth bette comes out I will add another reply.

---

### Post by jamesrl on 2008-10-15
The problem with the certificate is that openssl-vulnkey is that it was generated with an old version of openssl that had a major security issue, so it is easy for someone to exploit that security issue and break into your system if you protect it with a bad certificate.

It has nothing to do with the certificate coming from a shady person/source.

from man openssl-vulnkey
> 
     openssl-vulnkey checks a certificate, request or key against a blacklist
     of compromised moduli.

     A substantial number of certificates, requests and keys are known to have
     been generated using a broken version of OpenSSL distributed by Debian
     which failed to seed its random number generator correctly.  x509 cer&#8208;
     tificates, certificate requests and RSA keys generated using these
     OpenSSL versions should be assumed to be compromised.  This tool may be
     useful in checking for such OpenSSL x509 certificates, certificate
     requests and RSA keys.

     Certificates, requests and keys that are compromised cannot be repaired;
     replacements must be generated using openssl(8).



I'd really recommend just upgrading openssl where you created the certificate, and just create a new one.

More info:
[http://news.netcraft.com/archives/2008/06/12/ssl_certificates_vulnerable_to_openssl_flaw_on_debian.html](http://news.netcraft.com/archives/2008/06/12/ssl_certificates_vulnerable_to_openssl_flaw_on_debian.html)

---

### Post by anthro398 on 2008-10-22
Ah, but that may not be the problem.  See my post to [this thread]("http://ubuntuforums.org/showthread.php?p=6014622#post6014622").  I created a key today using the current version of OpenSSL and it caused OpenVPN to refuse to start.  From my OpenVPN.log:
```
Wed Oct 22 16:41:34 2008 us=877199   remote_float = DISABLED
Wed Oct 22 16:41:34 2008 us=877211   ipchange = '[UNDEF]'
Wed Oct 22 16:41:34 2008 us=877224   bind_defined = DISABLED
Wed Oct 22 16:41:34 2008 us=877236 NOTE: --mute triggered...
Wed Oct 22 16:41:34 2008 us=877257 187 variation(s) on previous 20 message(s) suppressed by --mute
Wed Oct 22 16:41:34 2008 us=877276 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Wed Oct 22 16:41:34 2008 us=886169 Diffie-Hellman initialized with 1024 bit key
Wed Oct 22 16:41:34 2008 us=886848 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Wed Oct 22 16:41:34 2008 us=995622 ERROR: '/etc/openvpn/easy-rsa/keys/zulu.key' is a known vulnerable key. See 'man openssl-vulnkey' for details.
Wed Oct 22 16:41:34 2008 us=995690 Exiting

```

Edit: Realized my configuration file was pointing at an old key.  

Not sure what to do from here.

---

