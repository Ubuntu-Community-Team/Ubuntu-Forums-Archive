---
title: "libpcap perl error"
date: 2011-08-12
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2011-08-12
If you install the pcap library using a system package, make sure to also 
install the corresponding -devel package, which contains the C headers needed 
to compile this module. 
        - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
No 'Makefile' created'YAML' not installed, will not store persistent state
  SAPER/Net-Pcap-0.16.tar.gz
  /usr/local/bin/perl Makefile.PL -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read metadata file. Falling back to other methods to determine prerequisites
Failed during this command:
 SAPER/Net-Pcap-0.16.tar.gz                   : writemakefile NO -- No 'Makefile' created


I get this error on cpan but i got libpcap-devel install but not sure why i get this error for?

---

