---
title: "Installing Enlightenment Desktop"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by jhazard112 on 2013-04-13
Hey All,

I am trying to install the Enlightenment desktop.  I am currently running Ubuntu 10.04 64-bit.  The following are the commands that I type into terminal, and what is returned:

sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn

gpg: keyring `/tmp/tmpIjRh1N/secring.gpg' created
gpg: keyring `/tmp/tmpIjRh1N/pubring.gpg' created
gpg: requesting key 31248878 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpIjRh1N/trustdb.gpg: trustdb created
gpg: key 31248878: public key "Launchpad PPA for Hannes Janetzek" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

sudo apt-get update

It then goes through the normal updating process

sudo apt-get install e17

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package e17

Am I doing something wrong, or does anyone have any idea why it won't install?  Any help is much appreciated.

Thanks in advance.

Justin

---

### Post by steeldriver on 2013-04-13
Maybe the ppa doesn't have an install candidate for 10.04? the earliest e17 package mentioned on the launchpad page appears to be for precise

---

### Post by Frogs Hair on 2013-04-13
I would find out if there is Lucid support for that PPA which I have used from 11.10 + . 10.04 is EOL on May 9th and may not have PPA support.

---

