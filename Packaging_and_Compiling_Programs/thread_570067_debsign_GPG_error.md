---
title: "debsign: GPG error"
date: 2007-10-07
forum: Packaging and Compiling Programs
---

### Post by Frak on 2007-10-07
Whenever I try to do a debsign, I always get an error.

```
gpg: skipped "Matt Adams <frak10@gmail.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1174:
running debsign failed
```

Its probably a very simple error

Any ideas?

---

### Post by Stemp on 2007-10-18
Same here :(

DEBEMAIL & DEBFULLNAME are set
gpg --list-secret-keys give all my keys

I don't understand

---

### Post by dholbach on 2007-11-15
Does your name and mail address exactly match one of the User IDs on your key?

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

---

### Post by tyfius on 2007-11-23
try:
> debuild -S -rfakeroot -k<your_gpg_key_id>

---

### Post by TrioTorus on 2008-01-25
I have the same problem. When trying
```
debuild -S -rfakeroot -k<your_gpg_key_id>
```
I get:
```
debuild: fatal error at line 844:
unknown dpkg-buildpackage/debuild option: C5702A10
```

I would like to know what the difference is and why this is not working...

Thx.

---

### Post by Shapierian on 2008-01-27
> **TrioTorus said:**
> I have the same problem. When trying
```
debuild -S -rfakeroot -k<your_gpg_key_id>
```
I get:
```
debuild: fatal error at line 844:
unknown dpkg-buildpackage/debuild option: C5702A10
```

I would like to know what the difference is and why this is not working...

Thx.

Looks like you put a space between -k and your key id.

---

