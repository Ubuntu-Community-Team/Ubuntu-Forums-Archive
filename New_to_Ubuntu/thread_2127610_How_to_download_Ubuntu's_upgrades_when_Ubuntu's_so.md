---
title: "How to download Ubuntu's upgrades when Ubuntu's software prevents me from doing so?"
date: 2013-03-20
forum: New to Ubuntu
---

### Post by doved on 2013-03-20
Today, 20 March 2013, XUbuntu has sent me several upgrades, but when I clicked INSTALL, I got this message: "Requires installation of untrusted packages from not authenticated sources." Since I was unable to find any way of overriding or cancelling that message, I have been unable to download the updates. How can Ubuntu consider itself a "not authenticated source"? More important, how can I download the upgrades?

---

### Post by ManamiVixen on 2013-03-20
Did you enable other repos? Starting 13.04, Ubuntu will have a validation system to protect users and the system. But you are supposed to be able to override with your consent. Can you give more details?

---

### Post by Cheesemill on 2013-03-20
Can you please post the output of...
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

