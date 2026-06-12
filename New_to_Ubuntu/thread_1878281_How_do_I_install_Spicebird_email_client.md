---
title: "How do I install Spicebird email client?"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by nauru on 2011-11-09
I read that it's not good to try to install tarballs directly downloaded, and preferable to get new software from synaptic or ubuntu software centre.

But Spicebird is apparently a really well-known email client yet isn't available at these locations...

So how do I install it?  Is there a non-commandline way to install tarballs?

Thanks.

---

### Post by sanderd17 on 2011-11-09
Are you sure you want spacebird? The verion number (0.8 ) notes it's still in Beta fase, and it hasn't recieved updates since summer 2010.

There is a ppa for it, but the ppa only offers version 0.7.

[https://launchpad.net/~spicebird/+archive/ppa](https://launchpad.net/~spicebird/+archive/ppa)

Installation of a tarball might be possible without command line, but it's easier with the command line.

The general steps are:
[LIST]
[*]unpack the archive (via Cli with the tar program or via GUI)
[*]execute "./configure" inside the unpacked directory
[*]execute "make" inside that directory
[*]execute "sudo make install" as last step.
[/LIST]

But I don't know the package, normally there is a README available in the archive. Be sure to read it before you proceed.

If you need a short tutorial on the CLI, read this: [http://linuxcommand.org](http://linuxcommand.org)

---

### Post by dniMretsaM on 2011-11-09
> **nauru said:**
> I read that it's not good to try to install tarballs directly downloaded, and preferable to get new software from synaptic or ubuntu software centre.

But Spicebird is apparently a really well-known email client yet isn't available at these locations...

So how do I install it?  Is there a non-commandline way to install tarballs?

Thanks.

Use [this PPA]("https://launchpad.net/%7Elil.wk/+archive/ppa") (instructions on the page). The PPA only has 0.7.1 though. Not 0.8 as on the Web site. It might be updated soon though. And is it really that common? I've never heard of it.

Also, there is no way to install tarballs without using the command line.

EDIT: Ninja'd by three minutes...

---

### Post by sanderd17 on 2011-11-09
> **dniMretsaM said:**
> Use [this PPA](https://launchpad.net/~lil.wk/+archive/ppa) (instructions on the page). And is it really that common? I've never heard of it.

Again, it's only version 0.7

---

