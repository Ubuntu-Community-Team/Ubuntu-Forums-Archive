---
title: "What purposes does the keyring manager serve?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by diablo75 on 2008-06-06
I'm just looking for a general explanation of the purpose of the keyring manager.  What all does it do?  And are there alternatives?

---

### Post by sdennie on 2008-06-06
It essentially stores password type things.  It itself is password protected but, it uses pam to authenticate so, it integrates nicely into the system.  There are undoubtedly alternatives but, probably not many that integrate as well into your desktop.  Are you having a problem with it?

Edit:
More information.  It not only stores passwords to things but, it's an interface for applications to store and retrieve passwords.  A good example is network manager.  It stores and retrieves wireless network passwords in the keyring manager.  If the keyring has been unlocked, it can grab those passwords out.  If it hasn't, you'll have to unlock the keyring.

---

