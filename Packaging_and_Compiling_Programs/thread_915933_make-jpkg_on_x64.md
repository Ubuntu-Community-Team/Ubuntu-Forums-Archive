---
title: "make-jpkg on x64"
date: 2008-09-10
forum: Packaging and Compiling Programs
---

### Post by eyelessfade on 2008-09-10
I'm trying to make a deb package of java 7 b34, but I only get an error from make-jpkg.

```
$ fakeroot make-jpkg jdk-7-ea-bin-b34-linux-x64-28_aug_2008.bin
Creating temporary directory: /tmp/make-jpkg.uzEBI28615
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: amd64
Detected Debian GNU type: x86_64-linux-gnu

No matching plugin was found.
Removing temporary directory: done

```

---

### Post by Sef on 2008-09-25
Moved to Packaging and Compiling Programs.

---

### Post by jafar2057 on 2008-10-03
I have the same problem. Any solution?
Which plugin is concerned?

---

