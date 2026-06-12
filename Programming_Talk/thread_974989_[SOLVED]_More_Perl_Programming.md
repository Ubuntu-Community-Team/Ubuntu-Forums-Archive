---
title: "[SOLVED] More Perl Programming"
date: 2008-11-08
forum: Programming Talk
---

### Post by Jackp90 on 2008-11-08
I was trying to write a program that asks for a hexadecimal number and converts it to decimal. So I wrote the following Perl Script:

> 
#!/usr/bin/perl
# hexconv
use warnings;
use strict;
print "Hex input for conversion here: ";
my $hex = <STDIN>;
print hex($hex), "\n";



It seems to work but I still get the following error:

> 
robert@laptop01:~/begperl$ perl hexconv
Hex input for conversion here: 0xff
Illegal hexadecimal digit '
' ignored at hexconv line 7, <STDIN> line 1.
255




Thanks for any help

---

### Post by ghostdog74 on 2008-11-08
chomp your input

---

### Post by ZuLuuuuuu on 2008-11-08
When you get an input from terminal, the last letter is almost always the newline character. The program gives you an error because of that character and like ghostdog74 said you should use *chomp()* to delete that character:

```
#!/usr/bin/perl
# hexconv

use warnings;
use strict;

print "Hex input for conversion here: ";
my $hex = <STDIN>;
**chomp($hex);**
print hex($hex), "\n";
```

or:

```
#!/usr/bin/perl
# hexconv

use warnings;
use strict;

print "Hex input for conversion here: ";
[B]my $hex;
chomp($hex = <STDIN>);[/B]
print hex($hex), "\n";
```

More detailed information on chomp():

[http://perldoc.perl.org/functions/chomp.html](http://perldoc.perl.org/functions/chomp.html)

---

