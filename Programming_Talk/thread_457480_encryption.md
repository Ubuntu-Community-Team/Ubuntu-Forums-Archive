---
title: "encryption"
date: 2007-05-28
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2007-05-28
Hello there,
I encrypted a text file in vim.  I can open it in vim and decrypt it.  But I want to do this via shell script.  Is it possible.??

Thanks,

---

### Post by Jussi Kukkonen on 2007-05-28
Possibly, but vim encryption is its own it -- it doesn't use a system wide encryption system like gpg.

Something you should know: Vim encryption is quite weak . A semi-knowledged attacker could probably break a typical password in an hour or two... To get real protection, use gpg.

---

### Post by vijayanand_sodadasi on 2007-05-29
Thanks Jussi,

Can I use gpg to encrypt text files and can I write a shell script to decrypt it.

---

