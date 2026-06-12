---
title: "Scripting GPG Decryption"
date: 2009-04-10
forum: Programming Talk
---

### Post by akvino on 2009-04-10
Hello all!

I have a little problem with scripting GPG decryption. To explain the process:
GPG -d filename #decrypts the file
but then it asks me for a passphrase. My problem is, how to pass passphrase at that prompt in order to completely automate the process of decryption.

Any ideas?

---

### Post by akvino on 2009-04-10
Got it..


cat passphrase.file | gpg --passphrase-fd 0 --output file.name -d encrypted.file

---

