---
title: "awk - need help comparing 2 files"
date: 2013-11-01
forum: Programming Talk
---

### Post by akhattri on 2013-11-01
My question is related to another previous thread ([http://ubuntuforums.org/showthread.php?t=1520823](http://ubuntuforums.org/showthread.php?t=1520823)) . I am having a similar situation. What I need is if col1 & 2 of file 1 matches col 1 & 2 of file 2, print that line of file 2.

File 1:
a 1 A
a 2 T
a 3 C


File 2:
a 2 Y
a 3 R
a 4 Q
b 5 R


output:
a 4 Q
b 5 R

---

### Post by tgalati4 on 2013-11-01
Could it be as simple as:

```

awk '
NR==FNR { 
    a[$1" "$2]=$3 
} 
NR>FNR { 
**    k=$2" "$1; **
    if (k in a) 
        print k,a[k]; 
    else 
        print $0
}
' file2 file1

```

---

### Post by steeldriver on 2013-11-01
:confused: The output you've shown seems to be the complement of what your description says

Another option might be to use grep -f, after cutting the 3rd column from file1, i.e.

```

$ grep -**v**f <(cut -d' ' -f-2 file1) file2
a 4 Q
b 5 R

```

```

$ grep -f <(cut -d' ' -f-2 file1) file2
a 2 Y
a 3 R

```

```

$ awk 'NR==FNR {a[$1" "$2]=$3; next} **!**a[$1" "$2] {print}' file1 file2
a 4 Q
b 5 R

```

```

$ awk 'NR==FNR {a[$1" "$2]=$3; next} a[$1" "$2] {print}' file1 file2
a 2 Y
a 3 R

```

---

### Post by drmrgd on 2013-11-01
Edit:  Nevermind....got a bug.  Gotta work on this for a minute more.  Besides, Steeldriver's example is much, much better anyway!

Edit: OK, bug fixed.  Had to take another approach, although I can't quite figure out why.  Steeldriver's solution is still a little better as it's a little less work.  But, since I had a personal vendetta against this problem, here's my solution anyway:

```

#!/usr/bin/perl


use warnings;
use strict;


my $file1 = shift;
open( my $fh1, "<", $file1 ) || die "Can't open '$file1' for reading: $!";
chomp( my @data1 = <$fh1> );
close( $fh1 );


my $file2 = shift;
open( my $fh2, "<", $file2 ) || die "Can't open '$file2' for reading: $!";
chomp( my @data2 = <$fh2> );
close( $fh2 );


my @results;
for ( @data2 ) {
    my ($match) = $_ =~ /^(\w\s+\d)/;
    if ( grep { /$match/ } @data1 ) {
            print  "$_\n";
    }
}

```

Assuming the data size is small, it's easy enough to load them up into two arrays and then compare.  My output is:

```

$ perl compare.pl file1.txt file2.txt 
a 2 Y
a 3 R

```

---

