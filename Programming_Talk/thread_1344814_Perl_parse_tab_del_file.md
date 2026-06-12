---
title: "Perl parse tab del file"
date: 2009-12-03
forum: Programming Talk
---

### Post by daveli on 2009-12-03
Dear experts:

I can´t find information on how to remove a heading from a tab_del text file after having read it in a Perl script. An example will be something like:

head -10 mydata.txt

plate_number: 1123479
user: jpt
scanner: 13_A

Obs    d1    d2    d3    d4
1    13    12    9    17
2    4    0    -2    15
3    12    9    9    15
4    14    7    9    14
5    9    11    8    14

Notice the heading made of three lines of text plus a white line. How can I get the data in the columns into variables to do some stats with them?

Thanks very much for your help!

dave

---

### Post by myrtle1908 on 2009-12-03
You can create a hash of arrays where each data row is an array in the hash.  There were no tabs in your data so I assumed space delimiter.

```
use strict;
use warnings;

my %dat;
while (<DATA>) {
  next if $. < 5; # skip first 4 lines
  next unless s/^(.*?)\s//; # grab the row number, i assumed this given it was incremental
  $dat{$1} = [split]; # split remainder of line on space into an array
}

# do something with the data eg. print it
for my $row (sort keys %dat) {
  print "Row $row: @{$dat{$row}}[0..3]\n";
}

__DATA__
plate_number: 1123479
user: jpt
scanner: 13_A

Obs d1 d2 d3 d4
1 13 12 9 17
2 4 0 -2 15
3 12 9 9 15
4 14 7 9 14
5 9 11 8 14
```

Yields

```

Row 1: 13 12 9 17
Row 2: 4 0 -2 15
Row 3: 12 9 9 15
Row 4: 14 7 9 14
Row 5: 9 11 8 14
Row Obs: d1 d2 d3 d4
```

You may not want the 'Obs' row in the data but you were not specific about this so it is there.

---

### Post by daveli on 2009-12-04
Thanks a lot[COLOR=Black] myrtle1908. Nearly there!
So that is a hash of arrays, right? I have to read into that deeper. 
I get the idea of removing the heading, looking for the line of DATA that has 5 fields or columns (or more depending on the data). But then you store "rows" in the hash of arrays, and not "columns". That is my goal since I would like to do some statistics with the columns, for example mean(d1) or even see if d1 is statistically different from d4.

By the way, can you explain a bit further the substitution you make to get the row number? The Obs column is incremental this time, but it could be plain text, like names if it was a collection of data for patients for example.
next unless s/^(.*?)\s//

I would really appreciate your help here.

Best
[/COLOR]

---

### Post by ghostdog74 on 2009-12-04
since your header is always before the first blank line, 

```

#!/usr/bin/perl
while(<>){
  if ( $_=~ /^$/ ){ $f=1 ;next}
  print  if $f ; 
}


```

---

### Post by myrtle1908 on 2009-12-04
> **daveli said:**
> I would like to do some statistics with the columns, for example mean(d1) or even see if d1 is statistically different from d4.

Given your data is basic tabular/csv I would use the DBD::CSV module.  It allows you to query the data with SQL.  Fairly certain the Perl SQL::Statement module supports some math functions although it has been a while since I got my hands dirty with this.

[http://search.cpan.org/~hmbrand/DBD-CSV-0.26/lib/DBD/CSV.pm](http://search.cpan.org/~hmbrand/DBD-CSV-0.26/lib/DBD/CSV.pm)

> **daveli said:**
> By the way, can you explain a bit further the substitution you make to get the row number? The Obs column is incremental this time, but it could be plain text, like names if it was a collection of data for patients for example.
next unless s/^(.*?)\s//

Here we are simply grabbing (then removing) everything up until the first space character and using the resulting match ($1) as the hash key eg. 'Obs', '1', '2' etc.

---

