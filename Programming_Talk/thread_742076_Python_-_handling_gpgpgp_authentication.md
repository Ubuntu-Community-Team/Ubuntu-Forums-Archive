---
title: "Python - handling gpg/pgp authentication"
date: 2008-04-01
forum: Programming Talk
---

### Post by aashay on 2008-04-01
I am trying to develop a small module in python which can use gpg to authenticate a user. I am planning to store the public and private keys as separate asc files which I can import. The client - server can then perform the authentication using a simple challenge-response method. Can anyone get me started with the modules I need to import to handle encryption and decryption using gpg. 
Will the Crypto.PublicKeyl.DSA work?

---

### Post by aashay on 2008-04-02
Okay, so i figured out that running external commands might be the best way.
However, i am having trouble encrypting text without actually importing the keys
I have a .asc ASCII public key file that I have exported.
Converting it to binary using ```
gpg --enarmor < aashay.asc > aashay.binary
```
Then trying to encrypt somethig:
```
cat plaintext | gpg --no-dufault-keyring --keyring aashay.binary --ear 'aashay@scrubbed.com'
```
I get the following error:```
gpg: aashays@scrubbed.com: skipped: public key not found
gpg: [stdin]: encryption failed: public key not found
```

Edit:
Nevermind, got it to work using a temporary keyring:
```
gpg --no-default-keyring --keyring temp --import aashay.asc
```

---

### Post by engla on 2008-04-02
Hello, have you seen and tried the package python-gnupginterface? I haven't, but I found it with a simple package search.

---

### Post by aashay on 2008-04-02
It looks almost similar to what I ended up doing. Actaully, I had seen this before. I didn't notice any way of importing .asc files, so gave up on it
Anyway, the code is working well with the os.system and subprocess.Popen calls

---

