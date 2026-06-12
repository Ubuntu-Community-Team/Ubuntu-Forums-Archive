---
title: "cpan question"
date: 2010-04-25
forum: Programming Talk
---

### Post by pythonsyntax on 2010-04-25
I useing the cpan command line for my cpan but i get this error.

No 'Makefile' created  SAPER/Net-Pcap-0.16.tar.gz
  /usr/local/bin/perl Makefile.PL -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Failed during this command:
 SAPER/Net-Pcap-0.16.tar.gz                   : writemakefile NO -- No 'Makefile' created

I hope someone can help me.:)

---

### Post by slavik on 2010-04-25
looks like a bad package to me ...

---

### Post by pythonsyntax on 2010-04-25
is any way to fix it?

---

### Post by gmargo on 2010-04-25
No need to compile it; just install the **libnet-pcap-perl** package, from the "universe" repository.

---

### Post by pythonsyntax on 2010-04-26
I did compile perl 5.12.o and i found out i need the liblib-devel lib.

---

