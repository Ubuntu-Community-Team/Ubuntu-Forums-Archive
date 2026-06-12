---
title: "pbuilder apt-key support?"
date: 2008-02-14
forum: Packaging and Compiling Programs
---

### Post by mtron on 2008-02-14
can i  add another (external) Repository's signing key file to pbuilder?

i'm using a line like
```
OTHERMIRROR="deb http://example.com gutsy universe"
```
in my /etc/pbuilder/pbuilderrc.

The gpg key for this repository is available, but i don't know how to tell pbuilder that the signing key is at location x. How to do the trick?

i'm using [pbuilder 0.174ubuntu2~gutsy1]("http://packages.ubuntu.com/gutsy-backports/devel/pbuilder") (taken from the gutsy backports repository)

Thanks for the help ;)

---

### Post by sfp-a7x on 2008-08-15
> **mtron said:**
> can i  add another (external) Repository's signing key file to pbuilder?

Yes: ```
$ sudo pbuilder --login --save-after-login
# cat | apt-key add - <<EOF
...public key goes here...
EOF
# logout
```

(I realize it's been a while since this question was posted, but I just had the same problem and figured it out.  I thought I'd share in case it would be useful to someone else.)

---

