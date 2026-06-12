---
title: "python encrypt/decrypt plain text document"
date: 2010-06-24
forum: Programming Talk
---

### Post by giuspen on 2010-06-24
Hi,
I need to encrypt/decrypt a text document using a password, is there a simple python way to do this?
I looked at the module [hashlib]("http://docs.python.org/library/hashlib.html") but cannot understand how to use a password.
Thanks in advance.

---

### Post by doas777 on 2010-06-24
hashing and ciphering are two differant kinds of algorithm. a hash is a one way function, so as long as the hash algorithm remains secure, there is no way to "de-hash" hashed data. a hash is only working if there is no way to determine the original value that was hashed, the original value will always produce the same hash, no two differant data values can create the same hash, and if the value cannot be changed without the hash being changed as well.

usually folks hash passwords, then check the resultant hashed value against a prior hashing stored in the database.

actual encryption is a somewhat more complex animal. here are some python samples on encryption.  [http://www.example-code.com/python/encryption.asp](http://www.example-code.com/python/encryption.asp)

---

