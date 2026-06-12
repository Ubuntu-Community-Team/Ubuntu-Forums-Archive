---
title: "Alternative Fdupes"
date: 2017-12-26
forum: New to Ubuntu
---

### Post by sed_faster on 2017-12-26
Hello folks,

Exist any alternative to the fdupes? I'm worried about this software use md5 signature instead sha25sum. Exist any alternative or md5 verification it is good and reliable?

> 
DESCRIPTION
       Searches  the  given  path for duplicate files. Such files are found by comparing file sizes and MD5 signatures,
       followed by a byte-by-byte comparison.



Thanks

---

### Post by litlesam on 2017-12-26
Hi, md5 verification is reliable.

---

### Post by Impavidus on 2017-12-27
MD5 is unsafe for cryptographic applications, which is not what you're doing. An attacker could create a second file with the same md5 signature. That shouldn't matter in your case, as the md5 signature comparison is followed by a byte-by-byte comparison.

---

### Post by sed_faster on 2017-12-27
Thanks to your help,

I am using this command: 
```

fdupes -rnAS -d /ptah/folder/

```
Exist any option or command to only execute this command over pdf files? I am thinking use some like this:
```

ls -r ../Desktop/test_repeat2/*.pdf -print 2>/dev/null | fdupes -rnAS -d >~/LOG

```
But didn't result. I don't know well work pipe!
Thanks

---

