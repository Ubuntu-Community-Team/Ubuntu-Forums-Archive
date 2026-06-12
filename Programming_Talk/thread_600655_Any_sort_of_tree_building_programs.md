---
title: "Any sort of tree building programs?"
date: 2007-11-02
forum: Programming Talk
---

### Post by CryptiniteDemon on 2007-11-02
Does anyone know of any programs that will generate trees easily?  It would be nice to have a 2-3 tree generator, but a binary tree generator is great too.

I'm just sick of having to constantly draw the stupid things using open office's shapes toolbar.  They take way too long to make.

---

### Post by stylishpants on 2007-11-02
I haven't tried it but...
```

fhanson@roch:$ apt-cache search tree | grep draw
njplot - [Biology] A tree drawing program

fhanson@roch:$ apt-cache show njplot
Package: njplot
Priority: optional
Section: universe/science
Installed-Size: 208
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Andreas Tille <tille@debian.org>
Architecture: i386
Version: 0.20060606-3
Depends: lesstif2, libc6 (>= 2.5-0ubuntu1), libncbi6 (>= 6.1.20061015), libvibrant6a (>= 6.1.20061015), libx11-6, libxmu6, libxt6
Filename: pool/universe/n/njplot/njplot_0.20060606-3_i386.deb
Size: 50078
MD5sum: a4d07fb7955c4bebfbb3adc3b759d103
SHA1: 0053d9063065ae8100bfeb47502ed353afaad6a0
SHA256: 2505ef55236907f05d5d0e6fa787d61869a7a5cf06d6465b5e1387755e946174
Description: [Biology] A tree drawing program
 NJplot is able to draw any tree expressed  in the standard
 phylogenetic tree format (e.g., the format used by the Phylip package).
 NJplot is especially convenient for rooting the unrooted trees
 obtained from parsimony, distance or maximum likelihood tree-building
 methods.
 .
 Homepage: http://pbil.univ-lyon1.fr/software/njplot.html
Url: http://pbil.univ-lyon1.fr/software/njplot.html
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


```

---

### Post by Vadi on 2007-11-02
Semantik?

---

### Post by NathanB on 2007-11-03
> **CryptiniteDemon said:**
> Does anyone know of any programs that will generate trees easily?  It would be nice to have a 2-3 tree generator, but a binary tree generator is great too.

I'm just sick of having to constantly draw the stupid things using open office's shapes toolbar.  They take way too long to make.

That's right, Booboo!  After I grab the pic-a-nic basket, we cut down the tree to construct a log table.  :)

For the lurking young grasshoppers:

[http://www.sosmath.com/tables/logtable/logtable.html](http://www.sosmath.com/tables/logtable/logtable.html)
[http://en.wikipedia.org/wiki/Log_table](http://en.wikipedia.org/wiki/Log_table)

Back to those binary trees:

[http://en.wikipedia.org/wiki/Binary_tree](http://en.wikipedia.org/wiki/Binary_tree)
[http://en.wikipedia.org/wiki/Binary_search_tree](http://en.wikipedia.org/wiki/Binary_search_tree)

Used for fast indexing of flat-file databases:

[http://en.wikipedia.org/wiki/Clipper_%28programming_language%29](http://en.wikipedia.org/wiki/Clipper_%28programming_language%29)
[http://en.wikipedia.org/wiki/B-tree](http://en.wikipedia.org/wiki/B-tree)

---

### Post by adrien214 on 2008-03-13
I would forget njplot, forget phylip and forget tree-puzzle...
I have tried all of them and they either crash as soon as I want to open a file or they dont recognize file formats...
I am using *jalview* for now... (get it via apt, possibly in restricted universe or somewhere else)

---

