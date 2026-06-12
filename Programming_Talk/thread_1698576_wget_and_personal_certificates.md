---
title: "wget and personal certificates"
date: 2011-03-02
forum: Programming Talk
---

### Post by miak on 2011-03-02
Hi,

I am trying to download a file that can be accessed only using a personal certificate, i.e. you need a personal certificate on your browser to get to it.
I'm trying to download that file with wget. I have exported the personal certificate from firefox and trid ```
wget --certificate="$PATH_TO_CERTIFICATE" "$FILE_TO_DOWNLOAD"
```, but I got ```
OpenSSL: error:14094410:SSL routines:SSL3_READ_BYTES:sslv3 alert handshake failure
```
Does anyone know what's the right way to do this?

-miak

---

