---
title: "Need to install Dovecot on Ubuntu on ubuntu 22, But error"
date: 2024-09-10
forum: New to Ubuntu
---

### Post by elegance on 2024-09-10
Hello,
I need to install Dovecot on Ubuntu but after:
```
apt install dovecot-core dovecot-pop3d dovecot-imapd
```

I have this error:
```

The following packages have unmet dependencies:
 dovecot-core : Depends: libexttextcat-2.0-0 (>= 3.3.0) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

I spend more than day on this issue but I couldn't fix this

---

### Post by elegance on 2024-09-10
problem solved I removed all files inside /etc/apt/sources.list.d

---

### Post by ActionParsnip on 2024-09-10
Yeah adding PPAs randomly is a great way to cause package issues

---

