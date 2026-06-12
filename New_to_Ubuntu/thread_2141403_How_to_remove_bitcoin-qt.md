---
title: "How to remove bitcoin-qt?"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by Gnutron on 2013-05-02
From Ubuntu 12.04 how do I completely remove or uninstall bitcoin-qt, the bitcoin wallet and all the blocks that are slowly consuming my entire disk drive?

---

### Post by kostkon on 2013-05-02
Remove the application using the software centre, or in the terminal:
```
sudo apt-get remove bitcoin-qt
```
then, in your home, press CTRL+H to view hidden files, find and delete the *.bitcoin* folder.

---

### Post by Gnutron on 2013-05-02
Thank you. This resolves the issue very simply.

---

