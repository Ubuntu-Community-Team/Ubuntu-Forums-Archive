---
title: "k9copy?"
date: 2005-12-24
forum: Repositories &amp; Backports
---

### Post by crispy_420 on 2005-12-24
Looking for a fast and reliable repository for k9copy. Any suggestions?
:razz:

---

### Post by Stragnagn on 2006-01-19
[http://www.czessi.net/main.php?i18n=en](http://www.czessi.net/main.php?i18n=en)

> sudo nano /etc/apt/sources.list

> ## archive.kubuntu.de / archive.czessi.net
## unofficially repository powered by Czessi.net and Kubuntu Germany
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy stable stable-updates
deb-src [http://archive.czessi.net/](http://archive.czessi.net/) breezy stable stable-updates
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy testing testing-updates
deb-src [http://archive.czessi.net/](http://archive.czessi.net/) breezy testing testing-updates
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy unstable unstable-updates
deb-src [http://archive.czessi.net/](http://archive.czessi.net/) breezy unstable unstable-updates

> 
wget [http://www.czessi.net/kczessi.gpg](http://www.czessi.net/kczessi.gpg)
sudo apt-key add kczessi.gpg
sudo apt-get update

---

