---
title: "Why can't i update anymore my Kubuntu Dapper?"
date: 2006-05-01
forum: Repositories &amp; Backports
---

### Post by mibadt on 2006-05-01
Hi,
About a week ago, I installed Kubuntu Dapper (6.0.6) Beta.
Initially, I could update and install new packages both graphically (Adept)
and by using apt-get.
However, after a few days, I can't do that anymore. Whenever I run apt-get
it hangs out without connecting till I stop it. Here is a copy of what I
get:
----------
apt-get update
0% [Connecting to it.archive.ubuntu.com (1.0.0.0)] [Connecting to
security.ubuntu.com (1.0.0.0)] [
root@Atlantis:/home/miki# 
----------

What's bothring me is the 1.0.0.0 IP address that appears in the message and
probably isn't right.

I would like to add 2 points:
a. While that happens, I'm connected to the Internet (I can browse,
ping ...)
b. My network architecture: Kubuntu PC connected to a 10.0.0.x LAN
containing an ADSL modem/router which acts as the gateway to my ISP.

Following please find a copy of my /etc/apt/source.list.

TIA
Michael Badt
;) 

------------------copy of my /etc/apt/source.list----------
root@Atlantis:/home/miki# cat /etc/apt/sources.list
# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) dapper-updates universe
multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

------------end----------------

---

