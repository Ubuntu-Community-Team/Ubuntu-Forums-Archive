---
title: "Conky Script - WifiScan"
date: 2010-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by webislands on 2010-12-15
run under linux need perl and iwlist installed

wifiscan.pl
```

#!/usr/bin/perl
use strict;

die "[-]Veuillez entrer une interface en argument\012" unless (@ARGV == 1);

my $iface = shift;

my @apz = split(/(.*\n.*\n.*\n.*\n)/, do{local($/); qx{iwlist $iface scanning |grep -E 'Address:|Channel:|ESSID:|Quality' |cut -c21-55}});

map {$_ =~ s{(.*)\n(.*)\n(.*)\n(.*)\n} {$4\n$1\n$2\n$3}} @apz;

foreach my $network (@apz)
{
    print $network, "\n";
}

```
if you need root rule for running iwlist
```
chmod 6755 /usr/sbin/iwlist  
```
change rules for wifiscan.pl
```
chmod 755 -x wifiscan.pl
```
in console using
```
wifiscan.pl wlan0
```
conky using
```
${iexecute 300 wifiscan.pl wlan0}
```

if you have bug check is
[noparse]my @apz = split(/(.*\n.*\n.*\n.*\n)/, do{local($/); qx{iwlist $iface  scanning |grep -E 'Address:|Channel:|ESSID:|Quality' |cut -c21-55}});[/noparse]
is in ONE line

---

