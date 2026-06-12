---
title: "LInux Standard Base?"
date: 2007-09-18
forum: Programming Talk
---

### Post by DraconPern on 2007-09-18
Is Ubuntu 7.04 LSB compliant?  I couldn't find any recent information on this.  Thanks.

---

### Post by nonewmsgs on 2007-09-18
not fully.  it like it's parent debian use .deb instead of .rpm for installation.

---

### Post by mssever on 2007-09-19
Does LSB really specify a package format? Unless there have been some somewhat recent changes to RPM, it's missing a lot of dpkg's functionality.

---

### Post by engla on 2007-09-19
the RPM demand of the LSB is fulfilled by debian/ubuntu simply by allowing them to be installed -- and you can install them, for example with 'alien'. The LSB doesn't specify that you have to use this as the _default_ package exchange, only that it should be in some way compatible/installable.

---

### Post by pmasiar on 2007-09-19
But is .rpm hard requirement? When I played with RH, i was greatly annoyed by lack of dependency tracking: instead of installing dependencies, it just told me: "you need Y to install X". When I tried, it told: "You need Z". it was dependecy hell. is it fixed somehow? If not, why standardize on using something inferior?

---

### Post by mssever on 2007-09-19
> **pmasiar said:**
> But is .rpm hard requirement? When I played with RH, i was greatly annoyed by lack of dependency tracking: instead of installing dependencies, it just told me: "you need Y to install X". When I tried, it told: "You need Z". it was dependecy hell. is it fixed somehow? If not, why standardize on using something inferior?

That is the exact reason why I abandoned Red Hat in favor of a Debian-based distro. I understand that RH's yum does resolve and automatically install dependencies, but as far as I know, that's built into yum, not rpm files.

---

### Post by hod139 on 2007-09-19
Dapper is certified ([http://www.linux-foundation.org/en/LSB_Distribution_Status](http://www.linux-foundation.org/en/LSB_Distribution_Status)) and according to that website, feisty is unknown.

---

### Post by AlexThomson_NZ on 2007-09-19
> **mssever said:**
> That is the exact reason why I abandoned Red Hat in favor of a Debian-based distro. 

Seconded :)

---

### Post by pmasiar on 2007-09-20
> **hod139 said:**
> Dapper is certified ([http://www.linux-foundation.org/en/LSB_Distribution_Status](http://www.linux-foundation.org/en/LSB_Distribution_Status)) and according to that website, feisty is unknown.

Probably it makes sense to certify only long-time release, that's why it is only Dapper.

---

