---
title: "Unable to install sendmail"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by RanZo on 2012-08-20
Hi, I am trying to install sendmail on my Ubuntu 12.4, but when I use:
sudo apt-get install sendmail
I get a message:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sendmail
I could not find anything on the Internet on this for two days of searching.

---

### Post by raja.genupula on 2012-08-20
have you tried updating your system ? 
open terminal and type as 

```
sudo apt-get update
```

then 
```
 raja@badfox:~$ sendmail
The program 'sendmail' can be found in the following packages:
 * exim4-daemon-heavy
 * exim4-daemon-light
 * postfix
 * citadel-mta
 * courier-mta
 * dma
 * esmtp-run
 * lsb-invalid-mta
 * masqmail
 * msmtp-mta
 * nullmailer
 * qmail-run
 * sendmail-bin
 * ssmtp
 * xmail
Try: sudo apt-get install <selected package>

```

---

