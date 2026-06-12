---
title: "how can I change language?"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by mk-ned on 2015-02-10
on vps is ubuntu 14.04 server 64bit installed, but everything is on Dutch language, I thought to change it, made search in google, and I did each example I've found, but without any success.

can somebody tell me what where and how should I configure to change Dutch language to English?

I already made (all with sudo)
locale-gen en_US.UTF-8

cat /etc/default/locale
LANG=en_US.UTF-8

update-locale LANG=en_US.UTF-8

dpkg-reconfigure locales

and much more. In the .bashrc and .profile I found nothing about language

> 
locale

LANG=nl_NL.utf8
LANGUAGE=nl_NL.utf8
LC_CTYPE="nl_NL.utf8"
LC_NUMERIC="nl_NL.utf8"
LC_TIME="nl_NL.utf8"
LC_COLLATE="nl_NL.utf8"
LC_MONETARY="nl_NL.utf8"
LC_MESSAGES="nl_NL.utf8"
LC_PAPER="nl_NL.utf8"
LC_NAME="nl_NL.utf8"
LC_ADDRESS="nl_NL.utf8"
LC_TELEPHONE="nl_NL.utf8"
LC_MEASUREMENT="nl_NL.utf8"
LC_IDENTIFICATION="nl_NL.utf8"
LC_ALL=nl_NL.utf8


> 
locale -a

C
C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US
en_US.iso88591
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
nl_NL.utf8
POSIX


---

