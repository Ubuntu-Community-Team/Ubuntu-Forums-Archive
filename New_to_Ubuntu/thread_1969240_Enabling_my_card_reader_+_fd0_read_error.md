---
title: "Enabling my card reader + fd0: read error"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by ClientAlive on 2012-04-29
I've seen information on the web for either of these respectively but not sure how to connect the dot's between the two things. Let me explain...

My internal card reader (a [.jpg"]Rosewill RCR-AK-IM5002]("http://www.rosewill.com/products/1610/ProductDetail_Overview.htm#/Mgnt/Uploads/ImagesForProduct/ImgPrd-1610-Cm[c55febcb3c884c11a90d972f8c6db975)) seems to show up in my firmware as a floppy device. I've seen information in a bug report about the fd0: read error where people are saying disable floppy support in your firmware and it goes away. Well I'm not sure if doing that would clobber my internal card reader. Actually, I've not done anything to verify whether it even works (I just assume as much because it shows up in my firmware's splash screen during POST. And there's another detail...  Actually, the fd errros I get when computer is booting is not just "fd0: read error" but...

```

fd0: read error
fd1: read error
fd0: read error
fd1: read error

```

then it proceeds to show me the grub menu for a moment, then boots up. It's annoying and it causes a delay.

Can someone help me out on this compound issue (making sure my card reader works and fixing the fd error)?

---

### Post by Belfry on 2012-10-23
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568720](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568720)

comment #19 might be helpful

---

