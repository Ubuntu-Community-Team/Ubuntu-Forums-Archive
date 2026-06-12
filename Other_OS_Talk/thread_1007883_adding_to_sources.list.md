---
title: "adding to sources.list"
date: 2008-12-10
forum: Other OS Talk
---

### Post by adobrakic on 2008-12-10
I can never get this to work. I have Linux Mint, and the adding of repos isnt the same as it is in synaptic of Ubuntu (which is a lot easier). So I have to add repos using /etc/apt/sources.list. I tried adding the experimental repo, and I get this error:

```
Reading package lists... Done
W: GPG error: ftp://ftp.debian.org experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1
W: You may want to run apt-get update to correct these problems

```

and this is how I've added it:

```
## -----------------------
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Linux Mint 6 Felicia (stable) +++
deb http://packages.linuxmint.com/ felicia main upstream import 

## +++ Backports (not as stable) +++
# deb http://packages.linuxmint.com/ felicia backport 

## +++ Community (not as stable) +++
# deb http://packages.linuxmint.com/ felicia community 

## +++ Romeo (unstable) +++
# deb http://packages.linuxmint.com/ felicia romeo 

## +++ Source Repositories +++
# deb-src http://packages.linuxmint.com/ felicia main upstream import 
# deb-src http://packages.linuxmint.com/ felicia community 
# deb-src http://packages.linuxmint.com/ felicia backport 
# deb-src http://packages.linuxmint.com/ felicia romeo 

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 8.10 Intrepid (stable) +++
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse 
deb http://security.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse 

## +++ Backports & Proposed (not as stable) +++
## deb http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse 
## deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted universe multiverse 



## +++ Source Repositories +++
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse 
deb-src http://security.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted universe multiverse 


## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ intrepid partner 

## +++ Medibuntu (stable) +++
deb http://packages.medibuntu.org/ intrepid free non-free 

[B]## +++ Experimental +++
deb ftp://ftp.debian.org/debian experimental main[/B]


```

???

---

### Post by ohzopants on 2008-12-11
Check out this website:
[http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt)

I'm pretty sure you need to import the key to eliminate that error message.

---

### Post by zvacet on 2008-12-11
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  A70DAF536070D3A1
gpg --export --armor  A70DAF536070D3A1 | sudo apt-key add -
```

---

### Post by bapoumba on 2008-12-11
Moved to Other OS Talk.

---

### Post by smartboyathome on 2008-12-11
Its recommended NOT to mix debian's repo with Ubuntu's, as that just asks for trouble.

---

