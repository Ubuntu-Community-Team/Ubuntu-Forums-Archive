---
title: "mod_security 2.6.0 on Ubuntu 12.04 LTS?"
date: 2013-10-07
forum: New to Ubuntu
---

### Post by optize on 2013-10-07
Is there a way to use mod_security 2.6.0 with 12.04 LTS (via apt)?  It seems it installs 2.5.11, there's functions in 2.6.0 which are required for the ruleset I'm using.

Thanks

---

### Post by sandyd on 2013-10-07
Mod_Security is at 2.6.3 ([http://packages.ubuntu.com/search?keywords=modsecurity&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=modsecurity&searchon=names&suite=precise&section=all))

You can download the latest core rules at [https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project#tab=Download](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project#tab=Download)

---

### Post by optize on 2013-10-07
> **sandyd said:**
> Mod_Security is at 2.6.3 ([http://packages.ubuntu.com/search?keywords=modsecurity&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=modsecurity&searchon=names&suite=precise&section=all))

You can download the latest core rules at [https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project#tab=Download](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project#tab=Download)

Thanks, how do I get 2.6.3?  When I installed it via apt-get last night, it gave me 

ii  libapache-mod-security          2.5.11-1ubuntu0.1              Tighten web applications security for Apache
ii  mod-security-common             2.5.11-1ubuntu0.1              Tighten web applications security - common files

Running 10.04.4 LTS

---

### Post by sandyd on 2013-10-07
> **optize said:**
> Thanks, how do I get 2.6.3?  When I installed it via apt-get last night, it gave me 

ii  libapache-mod-security          2.5.11-1ubuntu0.1              Tighten web applications security for Apache
ii  mod-security-common             2.5.11-1ubuntu0.1              Tighten web applications security - common files

Running 10.04.4 LTS

You wrote 12.04 LTS in your first post, and now 10.04 - which one are you using?

You will have to upgrade or manually backport libapache2-mod-security if you are using 10.04

---

### Post by optize on 2013-10-07
> **sandyd said:**
> You wrote 12.04 LTS in your first post, and now 10.04 - which one are you using?

You will have to upgrade or manually backport libapache2-mod-security if you are using 10.04


12.04, sorry.

---

### Post by sandyd on 2013-10-07
can you post the output of
```

lsb_release -a
```

Thanks.

---

### Post by optize on 2013-10-07
# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

---

### Post by optize on 2013-10-07
Ah, I think I see the problem.

I was installing libapache-mod-security, libapache2-mod-security has 2.6.x.

Thanks!

---

