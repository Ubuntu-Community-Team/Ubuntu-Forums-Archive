---
title: "Finding packages"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by elein on 2008-11-16
I am having a terrible time finding package names.  I am currently wondering what package libperl is in.  I appear to have perl installed--can run a perl script.  Have had the same problem with libreadline.

How do you find these packages?  The installer program doesn't seem to find developer basics.  Is there an apt-get command that would help me get the right packages for the libraries and tools I need for development in various languages?

I hope this is a simple question.

--elein

---

### Post by loell on 2008-11-16
commonly, **apt-cache search [COLOR="Blue"]keyword[/COLOR]** is used.

for example libperl

```

apt-cache search libperl
libperl-dev - Perl library: development files
libperl5.8 - Shared Perl library
libperl-critic-perl - Critique Perl source code for best-practices
libperl4caml-ocaml - Use Perl code in OCaml programs, runtime library
libperl4caml-ocaml-dev - Use Perl code in OCaml programs, development files
libperl4caml-ocaml-doc - Use Perl code in OCaml programs, documentation
libperl6-export-perl - Implements the Perl 6 'is export(...)' trait
libperl6-form-perl - perl - Perl6::Form - Implements the Perl 6 'form' built-in
libperl6-junction-perl - Perl6 style Junction operators in Perl5.
libperl6-say-perl - print -- but no newline needed
libperl6-slurp-perl - Implements the Perl 6 'slurp' built-in
libperldoc-search-perl - Index and Search local Perl Documentation
libperlio-eol-perl - PerlIO layer for normalizing line endings
libperlio-via-dynamic-perl - dynamic PerlIO layers
libperlio-via-symlink-perl - PerlIO layers for create symlinks
libperlmenu-perl - Menu and Template (curses-based) UI for Perl

```

these short descriptions is usually enough to find what you're looking for. :)

---

### Post by bapoumba on 2008-11-16
Depending on what I'm looking for, I use apt-cache search, as loell described, or the web ubuntu package page
[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libperl](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libperl)

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by bodhi.zazen on 2008-11-16
You can search with any of the graphical installers (synaptic , Add/Remove, Adept, etc) as well.

You can also use aptitude

sudo aptitude search <foo>

---

