---
title: "Security of ubuntu login password?"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by abexman on 2014-03-15
Dumb question: how secure is the ubuntu login password? It's not stored in a file somewhere for example easily accesible if someone stole my harddrive? I know it can be reset, but I was more worried about the actual password being revealed. Is there little danger aside from a keylogger capturing?

---

### Post by raja.genupula on 2014-03-15
Ubuntu password will store in Directory where root only can access it. The password will store in a encrypted manner so it will not be in a direct readable text. Even harddisk stolen due to bad luck unless they dont know the encrypted key they cant decrypt text.

---

### Post by steeldriver on 2014-03-15
The passwords in /etc/shadow are **hashed** not encrypted - there is no "encrypted key" that decrypts them - see [http://en.wikipedia.org/wiki/Cryptographic_hash_function#Password_verification](http://en.wikipedia.org/wiki/Cryptographic_hash_function#Password_verification) for example

AFAIK the default is salted SHA-512 - see [https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

---

### Post by sammiev on 2014-03-15
Still it's easy to by-pass the main account and create a new one.

When you boot, hold down the Shift key until you get the Grub menu.

Choose the item (usually the second one) that reads, "Ubuntu, with Linux ... (recovery mode)".

When it boots, select the option "root -- Drop to root shell prompt".

You will see a flashing cursor. Type the following and press Enter:

```
passwd user
``` 

but replace "user" with your username. Type the new password when prompted (twice).

Then press Ctrl-Alt-Delete to reboot normally.

---

### Post by whitesmith on 2014-03-15
> **abexman said:**
> Dumb question: how secure is the ubuntu login password? It's not stored in a file somewhere for example easily accesible if someone stole my harddrive? I know it can be reset, but I was more worried about the actual password being revealed. Is there little danger aside from a keylogger capturing?Passwords are hashed according to the equate in **ENCRYPT_METHOD** in the file **/etc/login_defs**. Ubuntu 12.04 uses SHA512, which is is regarded as safe in the security community, although no perfect cypher exists except for the one-time pad. Keyloggers are always a threat.

---

### Post by whitesmith on 2014-03-15
@abexman: If these responses answer your question, please use thread tools to close the thread. Thanks!

---

