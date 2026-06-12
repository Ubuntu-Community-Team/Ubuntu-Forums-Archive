---
title: "unable to import the public keys in QGIS"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by ilFonta on 2013-06-09
Hi folks

when I try to import the public keys 

gpg --keyserver keyserver.ubuntu.com --recv 997D3880
gpg --export --armor 997D3880 | sudo apt-key add -

(I don't use "sudo" in front of gpg)

for QGIS I get those message:

gpg: WARNING: unsafe permissions on configuration file "/home/giacomo/.gnupg/gpg.conf"
gpg: external program calls are disabled due to unsafe options file permissions
gpg: error communicating with the server key: general error
gpg: keyserver receive from failed: general error


Instead, if I try wit

sudo gpg --keyserver keyserver.ubuntu.com --recv 997D3880
sudo gpg --export --armor 997D3880 | sudo apt-key add -

I get 

gpg: WARNING: unsafe ownership on configuration file, "/home/giacomo/.gnupg/gpg.conf"
gpg: external program calls are disabled due to unsafe options file permissions
gpg: error communicating with the server key: general error
gpg: keyserver receive from failed: general error

if I try with

ls -la /home/giacomo/.gnupg/gpg.conf

I get 

-rw------- 1 giacomo giacomo 9398 ott 17  2012 /home/giacomo/.gnupg/gpg.conf

Waiting for your help

Thank you very much
Giacomo

---

### Post by wildmanne39 on 2013-06-09
Thread closed. Please do not post duplicates, it dilutes community effort.

Please only bump your thread once every 24 hours.
Thanks

---

