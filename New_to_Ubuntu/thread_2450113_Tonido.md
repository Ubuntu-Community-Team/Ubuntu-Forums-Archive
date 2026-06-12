---
title: "Tonido"
date: 2020-09-07
forum: New to Ubuntu
---

### Post by mavrickiller on 2020-09-07
How to install tonido cloud server in a raspberry Pi 4 which is running on Ubuntu 18.04

---

### Post by Holger_Gehrke on 2020-09-07
Have you tried the instructions at [https://www.tonido.com/support/display/docs/Raspberry+Pi](https://www.tonido.com/support/display/docs/Raspberry+Pi) ? Those are probably for Raspberry Pi OS / Raspbian, but since both that and Ubuntu are based on Debian there's a good chance it will work.

Holger

---

### Post by mavrickiller on 2020-09-09
No I tried it didn't work as well,

---

### Post by ActionParsnip on 2020-09-09
When you say "didn't work" it helps nobody, most of all you. What happened? What error messages did you see? Details.............

---

### Post by Holger_Gehrke on 2020-09-09
> **ActionParsnip said:**
> When you say "didn't work" it helps nobody, most of all you. What happened? What error messages did you see? Details.............

I just tried it on my Raspberry Pi 4 on Raspberry OS. In his defence I have to say that it doesn't give any error messages. You call it, it outputs 'Starting Tonido service' followed by a message from nohub about redirection of standard error to standard output and that's it.

Only by looking in the tonido.sh file did I find out that it does write to a log file in /tmp/tonido_$USER.log. In that file I found a complaint about needing libcrypto.so.1.0.0. After creating a link to libcrypto.so.1.0.1 named libcrypto.so.1.0.0 it wanted libssl.so.1.0.0 and I created a link to libssl.so.1.0.2. After both of these links were available it complains about not finding a symbol OPENSSL_1.0.0 in these libraries. That's when I took a hard look at the dates on the files and found they are from 2015 ! OpenSSL 1.0.0 has been deprecated for security reasons. Any program that still wants this needs to be patched and recompiled. 

Sadly Tonido seems to be closed source and more or less abandoned (newest files are from 2015, forums are closed and the last few postings are from 2014). I'd say remove it and find something that's still supported.

Holger

---

