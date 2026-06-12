---
title: "python-gnupg digitalocean.com notworking"
date: 2018-06-25
forum: Programming Talk
---

### Post by lance bermudez on 2018-06-25
using the guide from https://www.digitalocean.com/community/tutorials/how-to-verify-code-and-encrypt-data-with-python-gnupg-and-python-3?utm_medium=email&utm_source=IaaN&utm_campaign=06212018
copied pasted code in the guide can some one point out what is wrong please.
getting errors
```

$ signdetach
Signatures directory already created
Traceback (most recent call last):
  File "/usr/local/bin/signdetach", line 26, in <module>
    os.rename(files_dir[files_dir.index(x)]+".sig", "signatures/"+files_dir[files_dir.index(x)]+".sig")
FileNotFoundError: [Errno 2] No such file or directory: 'test5.txt.sig' -> 'signatures/test5.txt.sig'

```

more errors
```

$ encryptfiles
Encrypt directory exists
ok:  False
status:  invalid recipient
stderr:  gpg: Efile: skipped: public key not found
[GNUPG:] INV_RECP 1 Efile
gpg: [stdin]: encryption failed: public key not found

Traceback (most recent call last):
  File "/usr/local/bin/encryptfiles", line 29, in <module>
    os.rename(files_dir[files_dir.index(x)] + ".gpg", 'encrypted/' +files_dir[files_dir.index(x)] + ".gpg")
FileNotFoundError: [Errno 2] No such file or directory: 'test5.txt.gpg' -> 'encrypted/test5.txt.gpg'

```

---

### Post by spjackson on 2018-06-25
A few thoughts...
1. Did you do the bit of the tutorial that says :    "Create a GnuPG key pair, following this GnuPG tutorial.

Step 1 — Retrieving Key Pair Information"?

2. Did you change the line
```

gpg = gnupg.GPG(gnupghome="/home/sammy/.gnupg")


```
to something appropriate from your setup?

3. Did you create a key-pair for the email address(es) that you are using in the following bit?
```

        status = gpg.encrypt_file(f,recipients=["sammy@example.com"],output= files_dir[files_dir.index(x)]+".gpg")

```

---

### Post by lance bermudez on 2018-06-25
Yes I have created the keys and I am using them
pub   rsa4096/919DDE3B 2017-07-14 [SC]
uid         [ultimate] Efile (Encryption Keys) <first.last@lamarcc.edu>
sub   rsa4096/A5C41DCC 2017-07-14 [E]
sub   rsa4096/4062F0C2 2017-07-14 [S]

need this to use gpg2
gpg = gnupg.GPG(gpgbinary='/usr/bin/gpg2', gnupghome="/home/sammy/.gnupg")

---

