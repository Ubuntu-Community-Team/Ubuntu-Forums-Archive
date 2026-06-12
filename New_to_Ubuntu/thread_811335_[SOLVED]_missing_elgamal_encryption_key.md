---
title: "[SOLVED] missing elgamal encryption key"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by noorez on 2008-05-29
in Applications->Accessories->Passwords and Encryption Keys, I created an DSA/Elgamal key........when i viewed the properties, I saw a DSA primary key, a DSA subkey but only one Elgamal subkey....as I understand it Elgamal should have a pubic and private key...why is there only one?

---

### Post by master5o1 on 2008-05-29
I don't know much about the keys but I think maybe the private keys aren't shown in the GUI (i'm probably wrong).

anyway, in terminal you can list the keys by using the commands:

gpg --list-keys
and
gpg --list-secret-keys

---

### Post by noorez on 2008-05-30
hmm....my bad....i guess i just misread some of the numbers!

i was only looking at two keys. The DSA primary key's information (fingerprint, ID, strength..) was given under the Properties->Details, and it was listed under the subkeys, along with the Elgamal key. I guess the private keys are not listed.

---

