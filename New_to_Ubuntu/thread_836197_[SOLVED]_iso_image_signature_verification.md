---
title: "[SOLVED] iso image signature verification"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Gwasanaethau on 2008-06-21
Hi all!

I was wondering, I've just downloaded the 8.04 iso image from the main Ubuntu site. Whilst doing so, I noticed that there was an 'MD5SUMS' file available to verify the integrity (and security) of the iso file, and a detached signature ('MD5SUMS.gpg') to verify the authenticity of the 'MD5SUMS' file. However, I do not have the public key perform the aforementioned verification.

My question is: does anyone know where I can find a copy of said public key?

Thanks and regards.

---

### Post by the_doc on 2008-06-21
You don't need a public key.  Just get an MD5 digest calculator from the repos and calculate the signature on the iso file.

---

### Post by drs305 on 2008-06-21
Just run the following and check it against the correct value:
```
md5sum </path/filename>

```

[https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by Gwasanaethau on 2008-06-21
Forgive me, I'm not sure I understand. Do you mean using the terminal command 'md5sum' to compare the md5 string generated from the iso file with that provided on the website? I've done that and the iso file works out OK. I was wondering if there was any way to get a public key to verify the signature in the 'MD5SUMS.gpg' file.

---

### Post by the_doc on 2008-06-21
Hope this helps.

[https://help.ubuntu.com/community/VerifyIsoHowto]("https://help.ubuntu.com/community/VerifyIsoHowto")

---

### Post by Gwasanaethau on 2008-06-21
Perfect, that's exactly what I'm looking for! Thanks a mill!

Take care now!

---

### Post by the_doc on 2008-06-21
No worries, I misinterpreted you original request!

---

