---
title: "PHP LDAP  authentication fails when password ends in special character"
date: 2009-03-20
forum: Programming Talk
---

### Post by apjone on 2009-03-20
Hey,

Haven't asked this on php forum yet, but google didnt seem to help ( tried phrasing it several ways). I am writing a bit of code for a php page authenticating against active directory. This works except when a user has a '!' at the end of the password. then it bombs out. The code I am using is bellow.

[PHP]ldap_bind($ad,"$user@domain.com","$pass")[/PHP]

CORRECTION = Passwords ending in numbers or symbols do not work

Any help would be appreciated.

---

### Post by apjone on 2009-03-22
Ok after reading php.net I finally found waht needs to be done, and if memory serves I have done it before. I needed to utf8 decode the password string.

```

utf8_decode($password)

```

---

