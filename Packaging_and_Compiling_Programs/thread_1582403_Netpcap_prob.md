---
title: "Net::pcap prob"
date: 2010-09-26
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2010-09-26
Why am i getting this error for?

Running install for module 'Net::Pcap'
Running make for S/SA/SAPER/Net-Pcap-0.16.tar.gz
  Has already been unwrapped into directory /home/perlsyntax/.cpan/build/Net-Pcap-0.16-pmdF84
  Has already been made
Running make test
PERL_DL_NONLAZY=1 /usr/local/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/00-load.t ................ 1/1 # Testing Net::Pcap 0.16 under Perl 5.012002
t/00-load.t ................ ok   
t/01-api.t ................. ok       
t/02-lookup.t .............. ok     
t/03-openlive.t ............ ok     
t/04-loop.t ................ 1/195 

Then it just hang there and does nouthing.odd

---

### Post by pythonsyntax on 2010-09-26
You need to force install Net::Pcap to get it to install.

---

### Post by gmargo on 2010-09-27
Net::Pcap is available in the **libnet-pcap-perl** package.

[http://packages.ubuntu.com/lucid/libnet-pcap-perl](http://packages.ubuntu.com/lucid/libnet-pcap-perl)

---

