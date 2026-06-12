---
title: "ldd-perl"
date: 2007-03-20
forum: Programming Talk
---

### Post by Xyhthyx on 2007-03-20
I wanted to try writing a useful perl script and get familiar with perl at the same time, so I wrote a perl counterpart to ldd. It searches through a given perl script for the use of external modules and checks if they are installed and prints a simple apt-cache search result for missing modules if aplicable.

It's not fail proof, looking for perl gurus to give me any suggestions on improving it or just any coments are welcome.


Save as ldd-perl.pl
chmod +x ldd-perl.pl
./ldd-perl /full/path/perl-script.pl

```

#!/usr/bin/perl -w

# ldd-perl
# Checks a perl script for missing modules and tries
# to suggest missing module packages in apt

# by Xyhthyx

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or (at
# your option) any later version. 
# 
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Public License for more details. 
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 
# USA

use strict;
use warnings;

my $file = "@ARGV";
if ($file !~ /^\//) {
	$file = "$ENV{PWD}\/@ARGV";
}

open FILE, $file or die "Cannot open $file for reading: $!";

while (<FILE>) {
	
	if ($_ =~ /(^[\s*]use|^use|^[\s*]require|^require)[\s]/i && $_ !~ /(^[\s*]use|^use|^[\s*]require|^require)[\s](strict|warnings)/i) {
			eval $_;
			my $package = $2 if /^[\s*](use|require)[\s](.*)\;/;
			my $suggest = `apt-cache search $package`;
			if ($@) {
				print "\t $package => Not installed\n";
				print "\t \t Try installing the following packages:\n \t \t $suggest" if $? == 0;
			} else {
				print "\t $package => OK!\n";
			}
	}
	
}
close FILE;

```

---

