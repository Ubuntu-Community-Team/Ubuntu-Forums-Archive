---
title: "unoconv on ubuntu 14.04"
date: 2015-11-09
forum: New to Ubuntu
---

### Post by Amaefula_Chukwuebu on 2015-11-09
Hey Guys 

I installed unoconv through terminal using 

sudo apt-get install unoconv

Everything works perfect on terminal when I do

unoconv -f pdf filename.ppt 

but when try doing the same using php 

shell_exec(unoconv -f pdf filename.ppt)

I get the following errors

/usr/lib/libreoffice/program/soffice.bin: /opt/lampp/lib/libldap_r-2.4.so.2: no version information available (required by /usr/lib/x86_64-linux-gnu/libcurl-gnutls.so.4)
/usr/lib/libreoffice/program/soffice.bin: /opt/lampp/lib/liblber-2.4.so.2: no version information available (required by /usr/lib/x86_64-linux-gnu/libcurl-gnutls.so.4)
No protocol specified
Failed to connect to /usr/lib/libreoffice/program/soffice.bin (pid=6009) in 6 seconds.
Connector : couldn't connect to socket (Success)
Error: Unable to connect or start own listener. Aborting.


Please what am i doing wrong?

---

### Post by sandyd on 2015-11-09
See [https://github.com/dagwieers/unoconv/issues/87#issuecomment-18800070](https://github.com/dagwieers/unoconv/issues/87#issuecomment-18800070)

---

