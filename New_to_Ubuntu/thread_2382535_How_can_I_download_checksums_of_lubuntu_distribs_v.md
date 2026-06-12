---
title: "How can I download checksums of lubuntu distribs via https?"
date: 2018-01-14
forum: New to Ubuntu
---

### Post by alex357 on 2018-01-14
[FONT=Verdana]How can I download checksums of lubuntu distribs via https in order to be sure that the files have not been changed during the process of data transmission?[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by egeezer on 2018-01-14
Go to [http://releases.ubuntu.com/](http://releases.ubuntu.com/)  You'll find downloads for the ISOs and all their components: md5sums, manifests... all you need.

---

### Post by alex357 on 2018-01-15
> **egeezer said:**
> Go to [http://releases.ubuntu.com/](http://releases.ubuntu.com/)  You'll find downloads for the ISOs and all their components: md5sums, manifests... all you need.
This link offers downloading via http,but I would like to download lubuntu distribs via https.  How can using the software be safe if distribs of this software and it's check sums are downloaded via insecure channel,such as http,not https?

---

### Post by Holger_Gehrke on 2018-01-15
HTTPS protects **confidentiality** of transmitted data through encryption. It does not protect data transmission in the sense of protection from random changes. that is done through checksums (and requests for retransmission) at the tcp-level. The encryption of https also protects from intentionally changed-in-transit content, because an attacker would have to encrypt the data with the right keys (which he shouldn't have ...) but does not protect you from an attacker breaking the content by simply changing random bits (and either changing the packet checksums too or choosing the damage in such a way that the checksums stay the same. So for anything public, https is a waste of processing cycles unless you expect targeted attacks against your readers / downloaders. A forum like this one (readable by anyone, writing only for registered members) should protect it's login page and probably the pages for changing user data and for private messages but would not need to encrypt the traffic for not logged in readers of the forum. But setting everything to https is simpler than picking and choosing, so ...

Holger

---

### Post by alex357 on 2018-01-15
How can I be confident in authenticity of any information I have downloaded via http,not https ?

---

### Post by deadflowr on 2018-01-15
> **alex357 said:**
> How can I be confident in authenticity of any information I have downloaded via http,not https ?

Verify using the gpg keys:
[https://help.ubuntu.com/community/VerifyIsoHowto]("https://help.ubuntu.com/community/VerifyIsoHowto")

---

### Post by alex357 on 2018-01-15
How can I check lubuntu distribs for authenticity using windows desctop if I am going to migrate from windows to lubuntu?

---

### Post by deadflowr on 2018-01-15
> **alex357 said:**
> How can I check lubuntu distribs for authenticity using windows desctop if I am going to migrate from windows to lubuntu?

You need the sha256sum.exe addressed here: [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#4]("https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#4")
Sha256sum for windows:[http://www.labtestproject.com/files/win/sha256sum/sha256sum.exe]("http://www.labtestproject.com/files/win/sha256sum/sha256sum.exe")
And you can start the full tutorial here: [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0]("https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0")

---

### Post by alex357 on 2018-01-15
> **deadflowr said:**
> You need the sha256sum.exe addressed here: [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#4](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#4)
Sha256sum for windows:[http://www.labtestproject.com/files/win/sha256sum/sha256sum.exe](http://www.labtestproject.com/files/win/sha256sum/sha256sum.exe)
And you can start the full tutorial here: [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)
How can I use this way to check lubuntu distribs for authenticity if I am offered to download all tools via unsecure http,not https ?

---

