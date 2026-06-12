---
title: "Can't find clamtk in synaptic"
date: 2005-12-08
forum: Repositories &amp; Backports
---

### Post by cy218 on 2005-12-08
I think my repositories are up to date, am I missing something obvious?

This is a copy of my /etc/apt/sources.list:

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse


Any ideas?

If not, where do I go and how do I download manually (tar.gz and all that).

Thank you

Cy

---

### Post by aysiu on 2005-12-09
It's in Breezy Universe, not Hoary.

---

### Post by cy218 on 2005-12-10
Thanks aysiu. I suppose that means I can't use it with Hoary, does it?

---

### Post by thezerogroup on 2005-12-16
No with apt, but you can download the tarball:

[http://clamtk.sourceforge.net/]("http://clamtk.sourceforge.net/")

---

### Post by cy218 on 2005-12-16
Thanks -will it be alright to use with Hoary, or am I in danger of breaking something!

If the answer is not just a simple 'yes' or 'no' (is it ever -that's where the fun lies), could you point me towards a howto or something that will help me learn.

Thanks again

Cy :-k

---

### Post by daschl on 2005-12-19
[QUOTE=cy218]Thanks -will it be alright to use with Hoary, or am I in danger of breaking something!

If the answer is not just a simple 'yes' or 'no' (is it ever -that's where the fun lies), could you point me towards a howto or something that will help me learn.

Thanks again

Cy :-k[/QUOTE]

well, normally your are not in danger to break something ;) (you are right - its better if you install it with apt-get but compiling from source wont be a problem at all. dont forget to apt-get build-essential :))

i am sure that there will be a README-file or something which guides you through the installation process.

---

