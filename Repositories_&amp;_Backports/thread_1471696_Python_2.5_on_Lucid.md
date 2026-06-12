---
title: "Python 2.5 on Lucid"
date: 2010-05-03
forum: Repositories &amp; Backports
---

### Post by foxylad on 2010-05-03
I develop on Google Appengine, which uses python 2.5. To ensure no incompatibility, I need python2.5, but Lucid seems not to have it in the repositories.

I'm concerned that if I do a non-official install it will become the default and break lucid apps. Has anyone got any advice on how to best do this?

---

### Post by foxylad on 2010-05-04
Unofficial packages for python 2.4 and 2.5 here:

[https://launchpad.net/~fkrull/+archive/deadsnakes](https://launchpad.net/~fkrull/+archive/deadsnakes)

---

### Post by somepalli on 2010-07-24
I am not getting the PGP Key on Lucid 

sudo add-apt-repository ppa:fkrull/deadsnakes

I am getting following message.

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv FF3997E83CD969B409FB24BC5BB92C09DB82666C
gpg: requesting key DB82666C from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

---

### Post by tehmasp on 2010-07-31
Felix Krull's PPA is working as of July 31st 2010.

---

