---
title: "how can i deflate/uncompress files keeping them in the container?"
date: 2014-10-29
forum: New to Ubuntu
---

### Post by cosmoshell on 2014-10-29
How can I deflate compressed files preserving the container, with these being held in the container? zip, 7zip, rar?

Its not imporant if I need to extract them, I want the container deflated.

---

### Post by Impavidus on 2014-10-29
It depends on the archive format used. Very common on Linux is .tar.gz (or .tar.bz2, using different compression) format, which is an archive (the .tar file) that as been compressed (to a .gz file). So you can just use gunzip to uncompress it back to a .tar file and you've got an uncompressed archive. .zip files are different. .zip is not a compressed archive of files, but an archive of compressed files, so that means unpacking and uncompressing the archive and then repacking as an uncompressed archive. There may be tools that can do these steps at once.

---

