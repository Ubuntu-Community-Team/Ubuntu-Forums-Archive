---
title: "Repository woes"
date: 2005-03-04
forum: Repositories &amp; Backports
---

### Post by lerrup on 2005-03-04
I am trying to update my hoary dist and I get these error messages:

[http://gb.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:) MD5Sum mismatch
[http://gb.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:) MD5Sum mismatch
[http://gb.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz:) MD5Sum mismatch
[http://gb.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz:) MD5Sum mismatch

Any ideas?

---

### Post by darrenadams on 2005-03-04
The repository you're trying to access most likely hasn't been fully updated yet. Wait a while before trying to access it.

---

### Post by lerrup on 2005-03-05
Thanks, but now I get the message:

E: Unable to correct missing packages

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_20050302_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_20050302_all.deb)
  Bad header line


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20050302.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_20050302.1_all.deb)
  Bad header line


I've tried different repositories and that doesn't seem to work and also I can't unmark them and update everything else.

This is starting to annoy me, any ideas any one?

---

