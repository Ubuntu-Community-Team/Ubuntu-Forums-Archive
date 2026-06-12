---
title: "Question about Debian packages"
date: 2010-04-29
forum: Packaging and Compiling Programs
---

### Post by AntumDeluge on 2010-04-29
I'm trying to understand how .deb packages work.  Are there source debs?  I assumed there were, but from [http://packages.ubuntu.com](http://packages.ubuntu.com) I see that source is distributed in a GZipped file.

---

### Post by Bachstelze on 2010-04-30
Yes, source Debian packages are not in .deb files. They generally consist in a file ending in .orig.tar.gz that contains the original program source, a file ending in .diff.gz that contains the distribution-specific changes, and a .dsc file that contains various information about the package (MD5 checksums of the source tarballs, name and email address of the maintainer, etc.).

---

### Post by AntumDeluge on 2010-04-30
Thank you, that is very helpful.

---

