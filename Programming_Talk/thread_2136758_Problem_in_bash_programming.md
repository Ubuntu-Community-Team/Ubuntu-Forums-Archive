---
title: "Problem in bash programming"
date: 2013-04-18
forum: Programming Talk
---

### Post by mixalisjoe on 2013-04-18
I use this code to do a search in a text file and print the names and ph. no of some clients

awk -F "," '$1 == R1002  {print "Name: ", $2, "\n", "Number: ", $3}' clients.txt

my text file looks like that

N1000,Emilie Hunter,6979316283
U1001,Alyx Bell,6951504175
R1002,Szymon Mackenzie,6716001426
A1003,Gerard Kelly,6762006751
N1004,Gordon Brown,6710625818
F1005,Rohan Munro,6757315398
K1006,Tilly Dickson,6855237991
L1007,Mackenzie Macleod,6071988765
K1008,Ali Gray,6752682532

but i get nothing. Can you help?
Can you also tell me if you know a way to set the ID number to a variable
and compare it with the $1?
Thanks in advance

---

### Post by mixalisjoe on 2013-04-18
?

---

### Post by steeldriver on 2013-04-18
You need to quote the RT1002 string I think:
```
$ awk -F "," '$1 == [COLOR=#0000ff]**"**[/COLOR]R1002[COLOR=#0000ff]**"**[/COLOR] {print "Name: ", $2, "\n", "Number: ", $3}' clients.txt
Name:  Szymon Mackenzie
 Number:  6716001426
$
```

You can pass variables in using the -v command line switch:
```

$ awk -F "," [COLOR=#0000ff]**-v id="R1002"**[/COLOR] '[COLOR=#0000ff]**$1 == id**[/COLOR] {print "Name: ", $2, "\n", "Number: ", $3}' clients.txt
Name:  Szymon Mackenzie
 Number:  6716001426
$ awk -F "," [COLOR=#0000ff]**-v id="F1005"**[/COLOR] '[COLOR=#0000ff]**$1 == id**[/COLOR] {print "Name: ", $2, "\n", "Number: ", $3}' clients.txt
Name:  Rohan Munro
 Number:  6757315398
$
```

---

### Post by sisco311 on 2013-04-18
Sounds like homework. :-k

If you want to see how to solve it in pure bash, then check out BashFAQ 001 (link in my signature).

---

### Post by drmrgd on 2013-04-19
Sounds like a job for perl:

```
#!/usr/bin/perl
# Read in phone list and print out the name and phone number matching the input ID (hardcoded but can be 
# read in as user input if desired).  Added sub for standard number formatting if desired.  Run the script
# as script.pl <inputfile.txt>

use warnings;
use strict;

my $number;
my %phoneList;

my $id = "R1002";

while (<>) {
        chomp;
        my @line = split( ",", $_ );
        push( @{$phoneList{$line[0]}}, @line );
}

# Added extra check for erroneous IDs
if ( $id ~~ %phoneList ) {
        print "Name: $phoneList{$id}->[1]\nNumber: $phoneList{$id}->[2]\n";
} else {
        print "'$id' not found in list\n";
}

# Alternative natural formatting of the phone number.  Comment out if not wanted.
$number = number_format( $phoneList{$id}->[2] );
print "Formatted Number: $number\n";

sub number_format {
        my $in = shift;
        ( my $out =  $in ) =~ s/(\d{3})(\d{3})(\d{4})/$1-$2-$3/;
        return $out;
}
```

Not bash, but might be useful for flexibility parsing your lists in future.  If you want, you can set it up so that the $id is read in from the command line (user input), and then we can check the %phoneList hash to see if it's a valid entry.

---

