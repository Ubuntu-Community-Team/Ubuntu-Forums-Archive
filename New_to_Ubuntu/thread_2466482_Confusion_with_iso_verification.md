---
title: "Confusion with iso verification"
date: 2021-08-28
forum: New to Ubuntu
---

### Post by bulgin on 2021-08-28
Hello. I hope everyone is well and healthy.

Ubuntu 20.04 here and I need to rebuild machine.

Downloaded ubuntu-20.04.3-desktop-amd64.iso 
Downloaded [SHA256SUMS]("https://releases.ubuntu.com/20.04.3/SHA256SUMS") (current nautilus doens't acutally download the file so opened and pasted into text file, named SHA256SUMS)
Downloaded [SHA256SUMS.gpg]("https://releases.ubuntu.com/20.04.3/SHA256SUMS.gpg")

run commands:
gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMS
gpg: Signature made Thu 26 Aug 2021 05:52:49 AM EDT
gpg:                using RSA key 843938DF228D22F7B3742BC0D94AA3F0EFE21092
gpg: Can't check signature: No public key

The tutorial assumes there are two key ID's present in the faulty output - RSA and DSA.  Yet when I run this there is only the above and this does not match anything in the tutorial.

At this point I don't know what to do.

Any help much apprciated.

---

### Post by tea for one on 2021-08-28
Open a terminal
Navigate to the location of your ISO (probably Downloads)
```
cd Downloads
```
```
sha256sum ubuntu-20.04.3-desktop-amd64.iso 
```

Does the output match the published checksum:- [COLOR="#0000FF"]5fdebc435ded46ae99136ca875afc6f05bde217be7dd018e1841924f71db46b5[/COLOR] *ubuntu-20.04.3-desktop-amd64.iso

---

### Post by bulgin on 2021-08-28
well duh, stupid me.  Yes it does.  So what's all the fuss with the other steps suggested by the tutorial?

Thank you so much!

---

### Post by ajgreeny on 2021-08-29
It is always worth using a torrent system to download Ubuntu iso images as they automatically check each packet of the iso as it is downloading making a check after the event pointless.
It does not matter which torrent client you use, it is built in to all of them.

---

