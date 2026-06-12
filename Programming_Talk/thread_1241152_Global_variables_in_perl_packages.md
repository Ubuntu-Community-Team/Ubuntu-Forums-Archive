---
title: "Global variables in perl packages"
date: 2009-08-15
forum: Programming Talk
---

### Post by soltanis on 2009-08-15
This concept I don't really understand. I'm trying to write a perl package that basically maintains an array of some hashes in memory (and reads and writes them to files dynamically, etc). I want to be able to access this variable from scripts which import the package.

Checking up on the perl docs didn't really help. Anyone know how to get this done?

---

### Post by unutbu on 2009-08-15
[PHP]% cat test_utils.pm
package test_utils;
use strict;
use warnings;
use Exporter;
our @ISA = qw(Exporter);
our @EXPORT = qw();    # Symbols to be exported by default
our @EXPORT_OK = qw($test_constant); # Symbols to be exported on request


our $test_constant=2.71828;

1;
[/PHP]
[PHP]

% cat test.pl
#!/usr/bin/perl 
use strict;
use warnings;
use lib qw(/home/user/bin);
use test_utils qw($test_constant);

print "$test_constant\n";
[/PHP]
```

% test.pl
2.71828
```

---

