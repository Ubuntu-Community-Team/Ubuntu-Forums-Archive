---
title: "gpg decrypts without password"
date: 2018-08-21
forum: New to Ubuntu
---

### Post by mborl on 2018-08-21
Why is it that after I encrypt a file with gpg, I can decrypt it without giving a password? Can other people do the same if I send them the encrypted file in an email or they have access to a cloud server with my file uploaded there?

---

### Post by TheFu on 2018-08-21
gpg-agent?  It is just a guess.

From the manpage:
```
       --default-cache-ttl n
              Set  the  time a cache entry is valid to n seconds.  The default
              is 600 seconds.  Each  time  a  cache  entry  is  accessed,  the
              entry's timer is reset.  To set an entry's maximum lifetime, use
              max-cache-ttl.

       --max-cache-ttl n
              Set the maximum time a cache entry is valid to n seconds.  After
              this time a cache entry will be expired  even  if  it  has  been
              accessed  recently  or has been set using gpg-preset-passphrase.
              The default is 2 hours (7200 seconds).

```

---

### Post by DuckHook on 2018-08-21
In addition to what TheFu has posted, the following may help:

*gpg* does not encrypt with passwords. That's the whole point of using *gpg*. It encrypts with keys. Since you have both the public and private key installed in your system, any file you encrypt with one key will decrypt with the other (which you already possess). This is not the case with outsiders. Since they don't possess your private key, they can only encrypt files that they send you with your public key. You are the only one who can decrypt these files because only you possess the private key. Similarly, if you send them a file encrypted with your private key, they can only open it if they have your public key.

To store files on cloud servers securely, you encrypt them all with your public key. No one can then decrypt them without your private key. It goes without saying that you must never disclose your private key ***to anyone*** and it should be kept in a properly encrypted directory in your own HD. You will also want to print out both keys and store them in a very safe place. Without the private key, any encrypted data is essentially lost and unrecoverable.

---

### Post by Dennis N on 2018-08-21
I've noticed that too. I figure its just for convenience, so when you are reading a number of encrypted messages you have received, you don't have to reenter the password for each one. But, If I restart Ubuntu, then I need to enter the password again to decrypt messages. As it should be.

---

### Post by mborl on 2018-08-21
Sorry, I should have noted I was using symmetric encryption. 
```
gpg -c [FILENAME]
```
Doesn't that mean it doesn't use public/private keys?

---

