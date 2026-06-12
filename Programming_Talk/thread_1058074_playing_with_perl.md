---
title: "playing with perl"
date: 2009-02-02
forum: Programming Talk
---

### Post by v1nsai on 2009-02-02
Just started trying to teach myself perl, and I'm trying to write a program that will add up the number of letters in each day of the week (monday = 6 tuesday = 7 etc) from keys in a hash, but it just won't compile.  Can anyone nudge me in the right direction I've been googling but haven't found what I'm doing wrong yet.

```
my %month = ( "July" => 31, "August" =>, February => 28 );

for $int ( keys %month{ February } )
{
   $day = $int % 7;

   if ( $day == 0 ) { $sum += 8; }
   if ( $day == 1 ) { $sum += 6; }
   if ( $day == 2 ) { $sum += 8; }
   if ( $day == 3 ) { $sum += 9; }
   if ( $day == 4 ) { $sum += 7; }
   if ( $day == 5 ) { $sum += 6; }
}
print "There are $sum letters in the month of February.\n"
```

---

### Post by Martin Witte on 2009-02-02
This doesn't do what you want, but it compiles, and gives some output. Maybe it helps you to enhance your algorithm. Maybe [this]("http://hell.org.ua/Docs/oreilly/perl2/prog/index.htm") book can help you improving your perl skills. 
```
#!/usr/bin/perl

# these two lines give a lot of information on errors
use strict;
use warnings;

# your hash was a bit sloppy
# key 'August' doesn have a value
# key 'February' wasn a string beween quotes
my %month = ( "July" => 31, "August" => 31, 'February' => 28 );

# alays declare your variables with strict
my $int;
my $sum;

#keys takes the keys of a hash
#so keys %month yields list "July", "August", 'February'
for $int ( keys %month )
{
   my $day = $month{$int} % 7;

   if ( $day == 0 ) { $sum += 8; }
   if ( $day == 1 ) { $sum += 6; }
   if ( $day == 2 ) { $sum += 8; }
   if ( $day == 3 ) { $sum += 9; }
   if ( $day == 4 ) { $sum += 7; }
   if ( $day == 5 ) { $sum += 6; }
	print "There are $sum letters in the month of ".  $int . ".\n"
}

```

---

### Post by mozkill on 2009-02-02
when I started with Perl there were 2 really important things that took me a while to learn :

1.  learn how to enable debug in your scripts by adding the proper directives at the beginning of your script

2.  learn how to use the command line perl package manager.  its awesome and important to understand.

---

