---
title: "Eliminating junk data from a text file"
date: 2010-03-11
forum: Programming Talk
---

### Post by jamefarm on 2010-03-11
I've attached a sample file I'm working with, the lines include a stock symbol, company name, some earnings data(3 fields), and a date. What I need to do is remove any lines where the symbol has a number in it or has a '.' in it. Also need to remove any lines that don't have a symbol, company name etc

Good Lines:

AVCA  ,Advocat,0.14 ,n/a ,0.21 ,9-Mar AMC
AVAV  ,AeroVironment, Inc.,0.32 ,n/a ,0.21 ,9-Mar AMC


Bad Lines:

A036550.KS  ,ACE DIGITECH CO LTD,n/a ,n/a ,n/a ,9-Mar 1:40 AM
AMS.L  ,ADVANCED MEDICAL SOLUTIONS GROUP,n/a ,n/a ,n/a ,9-Mar BMO
,,,,,
,,,,,
***Earnings Releases - Proposed,,,,,


(* = space.  The forum kept ignoring the spaces I put there)

Any ideas?

---

### Post by myrtle1908 on 2010-03-11
You first need to normalize your data eg. remove commas from company names or quote them or something.  Make sure it is a valid CSV file.  Otherwise it is very difficult to parse.

Anyways, you can do this in a number of languages/utilities eg. bash/awk, Perl etc.

Here's one way in Perl.

```
use strict;
use warnings;

my @p;
while (<DATA>) {
  chomp;
  @p = split(/,/);
  next if !$p[0] || !$p[1] || $p[0] =~ m/\d|\./;
  print "$_\n";
}

__DATA__
AVCA ,Advocat,0.14 ,n/a ,0.21 ,9-Mar AMC
AVAV ,AeroVironment Inc.,0.32 ,n/a ,0.21 ,9-Mar AMC
A036550.KS ,ACE DIGITECH CO LTD,n/a ,n/a ,n/a ,9-Mar 1:40 AM
AMS.L ,ADVANCED MEDICAL SOLUTIONS GROUP,n/a ,n/a ,n/a ,9-Mar BMO
,,,,,
,,,,,
```

Yields

```
AVCA ,Advocat,0.14 ,n/a ,0.21 ,9-Mar AMC
AVAV ,AeroVironment Inc.,0.32 ,n/a ,0.21 ,9-Mar AMC
```

Note that I manually removed the comma from: "AeroVironment, Inc" in __DATA__.

I'll leave it as an exercise for you to read from a file instead of inline __DATA__.

---

### Post by jamefarm on 2010-03-11
Thanks for the reply!  I was able to remove the unwanted data by refining my awk command which generates the file thereby improving a previous step instead of adding another.  I also hadn't noticed the commas in the name fields which is now my next task.  Thanks again

---

