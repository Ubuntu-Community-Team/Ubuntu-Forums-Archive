---
title: "Perl: help with string comparison."
date: 2011-10-19
forum: Programming Talk
---

### Post by Amblikai on 2011-10-19
Hi folks, i'm having trouble trying to get a snippet of code working. This is part of a larger program but it's my test case and i still can't get it working.

Could anyone help explain why it won't work?
Essentially my code is as follows:

```
#! /usr/bin/perl
use strict;

my $single=0;
my @single=0;
my $and=0;
my $ina=0;
my $xor=0;
my $xor2=0;

$single=<STDIN>;
chomp($single);
@single=split(/ /, $single); 
print "@single\n";
$single=join('', @single); 
print "$single\n";

$and=0001;
$ina=0011;
$xor=0110;
$xor2=0110;

print "XOR\n", if ($single == $xor);
print "AND\n", if ($single == $and);
print "INA\n", if ($single == $ina);
print "MATCH\n", if ($xor == $xor2);
~                                                                         
```

if i run the program and type "0 1 1 0"
my output is:
```
0 1 1 0
0 1 1 0
0110
MATCH

```

The first line is my input. Note that i'm expecting the word "XOR" above the "MATCH". This is the part i don't understand why it won't display "XOR".

However if i type "0 0 0 1"
I get the following output:
```
0 0 0 1
0 0 0 1
0001
AND
MATCH

```

It will explain AND but not XOR. Can anyone help me understand this?
Thanks in advance.

---

### Post by Arndt on 2011-10-19
> **Amblikai said:**
> Hi folks, i'm having trouble trying to get a snippet of code working. This is part of a larger program but it's my test case and i still can't get it working.

Could anyone help explain why it won't work?
Essentially my code is as follows:

```
#! /usr/bin/perl
use strict;

my $single=0;
my @single=0;
my $and=0;
my $ina=0;
my $xor=0;
my $xor2=0;

$single=<STDIN>;
chomp($single);
@single=split(/ /, $single); 
print "@single\n";
$single=join('', @single); 
print "$single\n";

$and=0001;
$ina=0011;
$xor=0110;
$xor2=0110;

print "XOR\n", if ($single == $xor);
print "AND\n", if ($single == $and);
print "INA\n", if ($single == $ina);
print "MATCH\n", if ($xor == $xor2);
~                                                                         
```

if i run the program and type "0 1 1 0"
my output is:
```
0 1 1 0
0 1 1 0
0110
MATCH

```

The first line is my input. Note that i'm expecting the word "XOR" above the "MATCH". This is the part i don't understand why it won't display "XOR".

However if i type "0 0 0 1"
I get the following output:
```
0 0 0 1
0 0 0 1
0001
AND
MATCH

```

It will explain AND but not XOR. Can anyone help me understand this?
Thanks in advance.

0110 is not the string "0110", but the number 72. This is because numbers beginning with a zero are treated as octal, and 64+8 = 72. This is the case in many languages.

If you say $xor="0110";, things will work.

---

### Post by Amblikai on 2011-10-19
Oh i can't believe i didn't see that! I've spent ages trying to get this to work! Thank you very much. Much appreciated!

---

