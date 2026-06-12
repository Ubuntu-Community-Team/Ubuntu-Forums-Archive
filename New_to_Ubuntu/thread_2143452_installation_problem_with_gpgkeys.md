---
title: "installation problem with gpgkeys"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by lab12b on 2013-05-09
Hi there,

I'm having some problems getting gpg keys when installing NeuroDebian for Ubuntu 12.04 LTS.

I followed exactly these instructions: [http://neuro.debian.net/index.html#how-to-use-this-repository](http://neuro.debian.net/index.html#how-to-use-this-repository)
but I get stuck, when I type the following command:

*sudo apt-key adv --recv-keys --keyserver pgp.mit.edu 2649A5A9*

I get the following error message:

[I]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.KLoK8fMAXJ --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver pgp.mit.edu 2649A5A9
gpg: requesting key 2649A5A9 from hkp server pgp.mit.edu
?: pgp.mit.edu: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


[/I]Has anyone a solution?? :confused:

Many thanks!

---

### Post by willcurran on 2013-07-10
> **lab12b said:**
> Hi there,

I'm having some problems getting gpg keys when installing NeuroDebian for Ubuntu 12.04 LTS.

I followed exactly these instructions: [http://neuro.debian.net/index.html#how-to-use-this-repository](http://neuro.debian.net/index.html#how-to-use-this-repository)
but I get stuck, when I type the following command:

*sudo apt-key adv --recv-keys --keyserver pgp.mit.edu 2649A5A9*

I get the following error message:

[I]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.KLoK8fMAXJ --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver pgp.mit.edu 2649A5A9
gpg: requesting key 2649A5A9 from hkp server pgp.mit.edu
?: pgp.mit.edu: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


[/I]Has anyone a solution?? :confused:

Many thanks!

Hi there,
I'm also having the same problem.  Did you find a resolution for it?
Thanks,

Will Curran

---

### Post by msarslan on 2013-09-09
I'm having the same problem on a Ubuntu 13.04 machine. It looks like nobody is interested in providing an answer for this.

---

