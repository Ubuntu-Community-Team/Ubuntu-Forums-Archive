---
title: "Enabling Repositories"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by madrobber23 on 2008-04-28
I am trying to add a few applications and when I try to enable the repositories an odd error occurs.  

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Any ideas?

-Evan

---

### Post by hyper_ch on 2008-04-28
You have to import their GPG key for the repository.

Have a read at their page, it says how to do that.

---

### Post by zvacet on 2008-04-28
For all gpg keys 

[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -[/B]

so in your case 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -

for specific (Medibuntu)

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

