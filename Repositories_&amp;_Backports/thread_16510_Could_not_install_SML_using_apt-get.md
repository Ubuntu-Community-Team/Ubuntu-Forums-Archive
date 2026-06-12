---
title: "Could not install SML using apt-get"
date: 2005-02-22
forum: Repositories &amp; Backports
---

### Post by nanaban on 2005-02-22
apt-get install smlnj

The following packages have unmet dependencies:
  smlnj: Depends: smlnj-runtime (>= 110.42-3) but it is not installable
E: Broken packages

apt-get install sml-nj

The following packages have unmet dependencies:
  sml-nj: Depends: smlnj but it is not going to be installed
E: Broken packages

---

### Post by kassetra on 2005-02-22
[QUOTE=nanaban]apt-get install smlnj

The following packages have unmet dependencies:
  smlnj: Depends: smlnj-runtime (>= 110.42-3) but it is not installable
E: Broken packages

apt-get install sml-nj

The following packages have unmet dependencies:
  sml-nj: Depends: smlnj but it is not going to be installed
E: Broken packages[/QUOTE]

You probably need to add some repositories to your sources.list file in order to meet those dependencies.

[See here]("http://ubuntuguide.org/").

---

### Post by Vesperan on 2005-02-22
Nanaban,
I made a big post saying how I had your exact same problem (save different files), and that I had already updated my sources.list file as according to the Ubuntu Guide.

Then I checked my own sources.list file, and found I hadn't uncommented two of the repositories - now everything works fine. So, moral is: double check sources.list!

---

### Post by nanaban on 2005-02-22
I update everyday and I think I have all the repositories added (12 in total?).

Would be helpful if someone can confirm this by actually trying it.

Or, is there a particular reason why smlnj-runtime is not in the repository?

---

### Post by wrwills on 2005-05-16
Hello,

I've had the same problem.  I have the following two lines in my sources.list
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) hoary universe

which should mean that I would get
[http://uk.archive.ubuntu.com/ubuntu/pool/universe/s/smlnj-runtime/](http://uk.archive.ubuntu.com/ubuntu/pool/universe/s/smlnj-runtime/)

but smlnj-runtime doesn't show up in Synaptic.

The problem seems to be that smlnj-runtime doesn't show up in
[http://uk.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.bz2](http://uk.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.bz2)

-Rob

---

