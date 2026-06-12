---
title: "Encryption"
date: 2022-08-22
forum: New to Ubuntu
---

### Post by dmacpeak on 2022-08-22
I had my Ubuntu 20.04 pre o stalled, this I can't know if the encrypt option was selected at installation.

Is there a command I can run to see if my Ubuntu is encrypted?  Also, what would the response say if it is or is not encrypted?

Thank you in advance!

---

### Post by TheFu on 2022-08-22
Run:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
```
If there is anything in the output with "crypt" in it, then it is, but I doubt it if the vendor wasn't clear.  Also, you'd have to use a decryption key or passphrase or device BEFORE it would boot to unlock disk access.

You can learn more using the "cryptsetup" command and manpage.

Anyone using encryption on any OS needs to have excellent backups, since data recovery and disk-fix tools don't work on encrypted storage.  Don't use encryption if you don't have, know, and have tested the backup AND the restore capability. Too risky.

---

