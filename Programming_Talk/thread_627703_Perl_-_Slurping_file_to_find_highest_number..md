---
title: "Perl - Slurping file to find highest number."
date: 2007-11-30
forum: Programming Talk
---

### Post by misconfiguration on 2007-11-30
All,

I'm in the process of automating our printer add process on some AIX and HP-UX machines. I'm running into some issues after I parse info in our printer queues text file. We reference printers by numbers, we can't have duplicate numbers because each printer has to have a unique identifier.

My problem lies here; I'd like to slurp the file and have Perl figure out which is the highest number used, then add one to it and store it as a variable to complete the rest of the script process. 

Is this an unpractical approach? I'm not asking anyone to write code, maybe some of the experts around here would be able to point me in the right direction.

Thanks again!

---

### Post by misconfiguration on 2007-11-30
Nevermind.

use strict;
use warnings;
use List::Util qw(max);

my %prns;

while (<DATA>)
{
    my ( $printer, $num, $cmd ) = split /:/;
    $prns{$num} = $printer;
}

print "Highest numbered printer is $prns{max (keys %prns) }\n";

---

