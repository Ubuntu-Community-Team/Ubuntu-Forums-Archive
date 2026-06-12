---
title: "Perl newbie stuck"
date: 2009-06-16
forum: Programming Talk
---

### Post by dellwood on 2009-06-16
Hi, 

I am currently learning Perl for my summer job.  One of the "exercises" I am supposed to complete is making this converter:

```

#!/usr/bin/perl
use warnings;
use strict;
print "Currency converter\n\nPlease enter the exchange rate: ";
my $yen = <STDIN>;
print "49518 Yen is ", (49_518/$yen), " pounds\n";
print "360 Yen is ", (360/$yen), " pounds\n";
print "30510 Yen is ", (30_510/$yen), " pounds\n";

```

So that you are asked for the exchange rate as well as the three prices to be converted, so I wrote this:

```

#!/usr/bin/perl
use warnings;
use strict;

print "Currency converter\n\nPlease enter the exchange rate: ";
my $yen = <STDIN>;
print "Please enter the first price to be converted: ";
my $price_1 = <STDIN>;
print "Please enter the second price to be converted: ";
my $price_2 = <STDIN>;
print "Please enter the third price to be converted: ";
my $price_3 = <STDIN>,;

print "$price_1  Yen is ", ($price_1/$yen), " pounds\n";
print "$price_2  Yen is ", ($price_2/$yen), " pounds\n";
print "$price_3  Yen is ", ($price_3/$yen), " pounds\n";

```

Which produces this:

```
josh@josh-desktop:~/perl/19$ perl main.plx
Currency converter

Please enter the exchange rate: 2
Please enter the first price to be converted: 2
Please enter the second price to be converted: 4
Please enter the third price to be converted: 6
2
  Yen is 1 pounds
4
  Yen is 2 pounds
6
  Yen is 3 pounds

```

Which is fine (no errors), but I can't understand why the first variable in the last three lines ($yen) is on its own line.

Any help is greatly appreciated :)

-jhl

---

### Post by unutbu on 2009-06-16
Hi dellwood, welcome to the forums.
When you write
```

my $price_1 = <STDIN>;
```

$price_1 gets set to everything the user types into the terminal -- including the line feed character (\n) at the end.

To strip off the line feed character, use chomp:
```

my $price_1 = <STDIN>; 
chomp($price_1);
```

---

### Post by dellwood on 2009-06-16
That did the trick :).  Thanks for the quick reply!

-jhl

---

