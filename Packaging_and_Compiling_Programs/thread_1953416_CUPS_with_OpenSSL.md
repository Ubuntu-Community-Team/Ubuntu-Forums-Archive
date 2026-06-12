---
title: "CUPS with OpenSSL"
date: 2012-04-06
forum: Packaging and Compiling Programs
---

### Post by brainwash on 2012-04-06
Hey there,

I'm trying to rebuild the CUPS package (1.5.0-8ubuntu6_amd64) to support OpenSSL. After editing the build rules (--enable-openssl) and building the new package CUPS does not seem to depend on libssl:

```
$ dpkg --info cups_1.5.0-8ubuntu6+openssl_amd64.deb | grep Depends
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.7), libcups2 (>= 1.5.0), libcupscgi1 (>= 1.4.2), libcupsdriver1 (>= 1.4.0), libcupsimage2 (>= 1.4.0), libcupsmime1 (>= 1.5.0-0ubuntu1), libcupsppdc1 (>= 1.4.0), libdbus-1-3 (>= 1.0.2), libgcc1 (>= 1:4.1.1), libgnutls26 (>= 2.9.11-0), libgssapi-krb5-2 (>= 1.8+dfsg), libijs-0.35, libkrb5-3 (>= 1.6.dfsg.2), liblcms1 (>= 1.15-1), libldap-2.4-2 (>= 2.4.7), libpam0g (>= 0.99.7.1), libpaper1, libpoppler13, libslp1, libstdc++6 (>= 4.1.1), libusb-0.1-4 (>= 2:0.1.12), zlib1g (>= 1:1.1.4), debconf (>= 1.2.9) | debconf-2.0, upstart-job, poppler-utils (>= 0.12), procps, ghostscript (>= 9.02~), lsb-base (>= 3), cups-common (>= 1.5.0), cups-client (>= 1.5.0-8ubuntu6+openssl), ssl-cert (>= 1.0.11), adduser, bc, ttf-freefont, cups-ppdc
```

Do I have to disable GnuTLS to force the usage of OpenSSL?

Thanks

---

### Post by brainwash on 2012-04-15
bump

---

### Post by brainwash on 2012-04-23
bump :-k

---

