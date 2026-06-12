---
title: "Perl Script: Anyone interested?"
date: 2009-12-12
forum: Programming Talk
---

### Post by Puzzled Guy on 2009-12-12
I have developed a Perl script that will
read a text file, remove all punctuation and unnecessary symbols, remove duplicate words, sort them alphabetically, print the sorted list in the terminal, and finally write the list to a text file.

I am looking for ways to improve it (speed it up or improve the structure).

It uses the Time::HiRes module to check the execution time (rough estimate), you might have to install that first.

So, anyone experienced/interested enough to help?

The script, input file, and output file are in the attachment. Put some text (a wikipedia article, for example) in "data.txt" before running it, though.:P[ATTACH]139627[/ATTACH]

The name means UNIque WORDs

---

### Post by ghostdog74 on 2009-12-13
```

while(<INPUT>) {
    $TheFile = $_; 

```
shorter form
```

while(my $TheFile = <INPUT>) {
 ..    
}

```
Also Perl people would ask you to use warning and strict.
For regex, you can use POSIX style character class, such as [[:space:]] , [[:punct:]] instead of typing them out.

---

### Post by myrtle1908 on 2009-12-13
[PHP]use strict;
use warnings;
use Time::HiRes qw(gettimeofday tv_interval);

my $st = [gettimeofday];
my %words;

open IN, 'data.txt' or die $!;
open OUT, '>dictionary.txt' or die $!;

while (<IN>) {
  tr/A-Za-z/ /cs;
  $words{$_}++ foreach split(' ', lc $_);
}

close IN;

foreach my $word (sort (keys %words)) {
  print OUT $word, "\n";
}

close OUT;

print "Time to finish: ", tv_interval($st), " seconds.\n";[/PHP]

Approximately 4x faster.  Also, you should normalise your words ie. The vs the, And vs and etc ... same word but different ;)  I've done this with the 'lc' (lowercase) function.

---

### Post by Puzzled Guy on 2009-12-13
Thanks! The fastest runtime so far is "Time to finish: 0.000731 seconds."

The original one couldn't get below 0.001000!

And that part about using strict, I'll try it. I didn't use it in the original because I wasn't that used to it. That's gonna change;)

---

### Post by Puzzled Guy on 2009-12-13
> **ghostdog74 said:**
> [code]
Also Perl people would ask you to use warning and strict

I thought that use warnings is the same as using -w on the shebang line. Is there a difference between the two?

---

### Post by jpkotta on 2009-12-13
> **Puzzled Guy said:**
> I thought that use warnings is the same as using -w on the shebang line. Is there a difference between the two?

[http://perldoc.perl.org/warnings.html](http://perldoc.perl.org/warnings.html)

I've heard the recommendation to "use warnings;" rather than the -w switch.  The use pragma is more obvious to someone reading the code, and is a bit more flexible (see the docs).

---

### Post by ghostdog74 on 2009-12-13
please see perldoc warnings for the differences

---

