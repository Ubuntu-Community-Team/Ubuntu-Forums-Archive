---
title: "How to open and access ntfs password locked/encrypted partition on ubuntu"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by eshant_engineer on 2012-06-17
Hi,

Earlier, I had windows on my system. Now it is ubuntu. There is a problem that it is not available in the ubuntu. When I checked that drive in gparted, it is showing like in the thumbnail.

please help to open and access that drive.

Thank you in advance:)

---

### Post by HeroOfCanton on 2012-06-17
If it's encrypted and your boot partition is gone you may have a serious problem. I don't know of any open software that can undo EFS encryption. Depending on how valuable your data is, you may look into something like [Advanced EFS Data Recovery]("http://www.elcomsoft.com/aefsdr.html") or [DiskInternals EFS Recovery]("http://www.diskinternals.com/order/efs/").

Can you give more details on exactly what happened? Did you remove the Windows boot partition when installing Ubuntu?

---

### Post by Mark Phelps on 2012-06-17
If the whole partition was encrypted, and you don't know the passkey or passphrase to access it, then you're simply out of luck!

If there was a simple way to bypass partition encryption simply by mounting an NTFS partition in a Linux OS, then the encryption wouldn't be worth the effort, now would it!

---

### Post by eshant_engineer on 2012-06-18
i remember passphrase. But how could I mount it?

---

