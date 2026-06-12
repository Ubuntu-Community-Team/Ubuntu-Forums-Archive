---
title: "Ubuntu keeps freezing"
date: 2020-02-11
forum: New to Ubuntu
---

### Post by spiderderp on 2020-02-11
I just redownloaded ubuntu after a year and for some reason, it just keeps randomly freezing. What's wrong and what should I do?

---

### Post by oldrocker99 on 2020-02-11
Go to the page from which you downloaded he image and look for the SHA256sum code. Then, do this:
```
sha256sum nameof.iso
```

sha256sum is already installed. If the two checksums are the same, the download is good. You can try booting with the USB and select "Check Disk For Errors." If an error is found, try a different thumb drive.

---

