---
title: "OpenDNS encrypts but has &quot;bad&quot; code"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-02-17
I've been using OpenDNS for 3 or 4 years. Never had a problem.

Imagine how excited I was when today, I saw:
[Tales from the DNSCrypt: Linux Rising]("http://blog.opendns.com/2012/02/16/tales-from-the-dnscrypt-linux-rising/")
by David Ulevitch, Founder/CEO.

SO, I d/l'd the .deb (32-bit) for my 'puter and went to the Ubuntu Software Center to install it.

I received a very odd message from Ubuntu, which said:

The package is of bad quality - The installation of a package which violates the quality standres ins't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details, beneath.

Which are:

Lintian check results for /home/mark/Downloads/dnscrypt-proxy_0.9_i386.deb:
Use of uninitialized value $ENV{"HOME"} in concatenation (.) or string at /usr/bin/lintian line 112.
E: dnscrypt-proxy: maintainer-name-missing <root@debian>
E: dnscrypt-proxy: maintainer-address-malformed <root@debian>

SO, will someone tell me what is going on here? I'm not a programmer. And I cannot afford to harm my DNS/Network, etc.

---

### Post by Mark_in_Hollywood on 2012-03-06
The solution has been posted at:

[https://github.com/jordansissel/fpm/pull/159](https://github.com/jordansissel/fpm/pull/159)


and appears to be a very very minor error.

---

### Post by Bobhuber on 2012-03-06
> **Mark_in_Hollywood said:**
> I've been using OpenDNS for 3 or 4 years. Never had a problem.

Imagine how excited I was when today, I saw:
[Tales from the DNSCrypt: Linux Rising]("http://blog.opendns.com/2012/02/16/tales-from-the-dnscrypt-linux-rising/")
by David Ulevitch, Founder/CEO.

SO, I d/l'd the .deb (32-bit) for my 'puter and went to the Ubuntu Software Center to install it.
  
SO, will someone tell me what is going on here? I'm not a programmer. And I cannot afford to harm my DNS/Network, etc.
In reading the post about the problem and fix on the forum AND  if your sure about the source (this applies to any package you install) you may wan't to try the Gdebi package installer instead of the Software Center to install the package. I've installed the 64/bit version of Dnscrypt and other than slowing things down a bit it seems to work fine. This is not to say that it will install without errors but might be worth a try. As usual a backup of your system is well advised.

---

