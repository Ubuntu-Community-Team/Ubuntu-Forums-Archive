---
title: "Installing Updates"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by pkj on 2012-04-05
Hi,

Having problems with updates..

About 88 updates are required to be installed on my PC...Hoever, when attempting to install (via Update Manager) i get a message (when Applying Updates ---  'Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Help requested on what to do next....

pkj

---

### Post by philinux on 2012-04-05
> **pkj said:**
> Hi,

Having problems with updates..

About 88 updates are required to be installed on my PC...Hoever, when attempting to install (via Update Manager) i get a message (when Applying Updates ---  'Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Help requested on what to do next....

pkj

[http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

---

### Post by Cheesemill on 2012-04-05
Can you type the following into a terminal and post the results please:
```
sudo apt-get update && sudo apt-get upgrade
```

Edit - Beaten to it. Follow the steps in philinux's post.

---

