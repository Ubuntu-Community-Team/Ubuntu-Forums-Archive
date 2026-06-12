---
title: "Ho can I do manual packaging/deb? What's wrong?"
date: 2009-12-16
forum: Packaging and Compiling Programs
---

### Post by Emanuele_Z on 2009-12-16
Hi all,

I'm trying to package a simple program (binary only, no libs, no config files).
I create the *control* file, tar+gzip.
Then I do the same for the data, *usr/bin/my_exec* then tar and gzip.
Then I have the *debian-binary* set to proper version.
Finally I use *ar -r mypackage-2.0_amd64.deb control.tar.gz data.tar.gz debian-binary* and I have the deb file.

When I double click GDebi says all is ok.
If I browse the files all is ok but then when I try to test install all I get is:
```

dpkg-deb: file `/home/ema/TEST/packages/TEST-0.2_amd64.deb' is not a debian binary archive (try dpkg-split?)
dpkg: error processing /home/ema/TEST/packages/TEST-0.2_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /home/ema/TEST/packages/TEST-0.2_amd64.deb

```

Any ideas?
Thanks in advance,

Cheers,

---

### Post by Emanuele_Z on 2009-12-17
That is fixed. The issue is related to the following:
**When using ar to create the deb file, first insert *debian-binary* then *control.tar.gz* finally *data.tar.gz***

Cheers,

Ps. I managed to spot this issue because I debugged dpkg...

---

