---
title: "Back up of encrypted folder in Home"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2014-03-31
I understand that my Home folder is encrypted until I log in.
Can I back up a folder, so that it's encrypted on a USB device?
Is it very good encryption?
Can it be opened on a windows 7 machine?

---

### Post by Dave_L on 2014-03-31
The home folder encryption that Ubuntu uses (ecryptfs) is very strong, provided that your encryption passphase is strong.

The encrypted files are in ~/.Private (/home/USER/.Private), so you could put those on the USB device.

Do you *want* to be able to access the files from a Windows 7 machine?  In that case, it may be better to create a Truecrypt container on the USB device, and place the unencrypted files into that container. Truecrypt is cross-platform; it's available for both Linux and Windows.
[https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)
[http://www.truecrypt.org/](http://www.truecrypt.org/)

GnuPG is also cross-platform, and could also be used.

---

