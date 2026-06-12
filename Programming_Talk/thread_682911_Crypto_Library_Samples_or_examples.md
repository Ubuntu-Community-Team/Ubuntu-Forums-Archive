---
title: "Crypto Library Samples or examples?"
date: 2008-01-30
forum: Programming Talk
---

### Post by windyweather on 2008-01-30
I would like to build a signed file verifier for settings files for a program.

General outline would be to:
[LIST=1]
[*]Create pub key pair.
[*]Utility to Sign settings file [probably XML] using private key.
[*] have a public key built into program.
[*]When program reads the file, it verifies the signature to make sure it's authentic.
[/LIST]

Looks like Crypto Library has what I need, but
[LIST=1]
[*]I don't see Crypto Lib functions to create the certificates. Do I use OpenSSL functions to create X.509 certificates?
[*]Does CryptoLib consume X.509 certs?
[*]Can someone point me to samples of code that uses Crypto Lib to sign documents?
[/LIST]

Thanks much,
Windy

---

