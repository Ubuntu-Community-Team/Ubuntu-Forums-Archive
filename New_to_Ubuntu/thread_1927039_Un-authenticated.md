---
title: "Un-authenticated?"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by apple2user on 2012-02-17
Update Manager asking me to update my system. On the final confirmation screen I am informed that the updates are un-authenticated. This makes me cancel the update. Should I go ahead and update? Is it relevant that having problems with a previous update, I am now running a previous version from the GRUB screen?

---

### Post by 2F4U on 2012-02-17
What exactly do you mean by "unauthenticated"? Do you mean that they are not signed? It may help if you give the exact text of the message.

---

### Post by oldos2er on 2012-02-17
Run ```
sudo apt-get update
``` in a terminal, it should show you which repositories need authentication. Post the output here if you need further help.

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

