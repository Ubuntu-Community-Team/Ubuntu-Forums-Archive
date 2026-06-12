---
title: "awk question: grouping  3 columns"
date: 2013-02-27
forum: Programming Talk
---

### Post by fluxi on 2013-02-27
Hi to all,
I am new to this forum. I have an awk problem:
The input data looks something like that 
 
a1 b1 c1 
a1 b2 c2 
a2 b2 c3 
a3 b4 c1 
a1 b1 c10 
a2 b5 c5 
a3 b1 c4 
a4 b2 c3 
a1 b2 c2 
a2 b2 c3 
a1 b1 c1 
a1 b2 c2 
a1 b2 c2 
a2 b2 c3 
a2 b2 c3 
 b1 c1: 2
The output should look like that: 
a1 b1 c1: 2 times
                       ______c10:1 time
      ___b2 c2: 3 times
a2 b2 c3: 3 times
and so on.
      
It should count the groups for all $i.
I have allready done some easy awk-programming, but I can't get this one right.

Maybe you can help me
yours
Petra

---

### Post by r-senior on 2013-02-27
Is this a homework problem? What do you have so far?

If you are completely stuck, you might want to read up about associative arrays:

[https://www.gnu.org/software/gawk/manual/html_node/Array-Basics.html#Array-Basics](https://www.gnu.org/software/gawk/manual/html_node/Array-Basics.html#Array-Basics)

---

### Post by fluxi on 2013-02-27
Hi,
no,no homework. These years are long gone ;-) Allas....
I have: awk -F" " '{if(k[$1])k[$1]=k[$1]":"$2 ":" $3; else k[$1]=$2;}END{for (j in k)print j, k[j];}' test

this gives:
a1 b1:b2:c2:b3:c10:b2:c2:b1:c1:b2:c2:b2:c2
a2 b2:b5:c5:b2:c3:b2:c3:b2:c3
a3 b4:b1:c4 but there are strange signs in the output... I can't copy past them.  But they are not in the input file, but in the output. I tried to change  the character encoding of the terminal, but they remain... 
a4 b2

The first set is allways wrong. And I can't get the counting right ;-)


I now tried something slightly different:
awk -F":" '{coli[$1,$2,$3]++} END {for (i in coli) print i,":" col[i]}' test.txt |sort 

This gives
a1 b1 c1 :2
a1 b2 c2 :4
a1 b3 c10 :1
a2 b2 c3 :4
a2 b5 c5 :1
a3 b1 c4 :1
a3 b4 c1 :1
a4 b2 c3 :1


Everything seems fine, but this seems too easy to me. I will have to test it on the real data tomorrow...
Yours Petra

---

### Post by greenpeace on 2013-02-27
Hi!

Maybe I'm oversimplifying it, but it almost seems like you might be able to do it by using the commands:

```
sort file.txt | uniq -c
```

Which will tell you the count of each unique line in file.txt

Would that work?

Cheers, 
Gp

---

### Post by r-senior on 2013-02-27
I think this does it in awk, if you want control over the output:

```
awk '{++count[$0]} END {for (pattern in count) printf("%-12s: %d times\n", pattern, count[pattern])}'
```

For example:

```
$ cat input
a1 b1 c1 
a1 b2 c2 
a2 b2 c3 
a3 b4 c1 
a1 b1 c10 
a2 b5 c5 
a3 b1 c4 
a4 b2 c3 
a1 b2 c2 
a2 b2 c3 
a1 b1 c1 
a1 b2 c2 
a1 b2 c2 
a2 b2 c3 
a2 b2 c3 
$ awk '{++count[$0]} END {for (pattern in count) printf("%-12s: %d times\n", pattern, count[pattern])}' input
a2 b5 c5    : 1 times
a3 b1 c4    : 1 times
a2 b2 c3    : 4 times
a1 b1 c10   : 1 times
a1 b2 c2    : 4 times
a1 b1 c1    : 2 times
a3 b4 c1    : 1 times
a4 b2 c3    : 1 times

```

So it makes an associative array 'count' using the whole input line as the key, incrementing the value in the associative array on each occurrence. Then the end pattern iterates over the array and prints the key and value.

EDIT: That's basically what you have in your second attempt. I just didn't read it properly.

---

### Post by drmrgd on 2013-02-27
If you're not fixed on using Awk for this, you could do it fairly easily in Perl (with the same exact strategy, I should point out):

```
#!/usr/bin/perl

use warnings;
use strict;

my %lineCount;

while(<>) {
        chomp;
        $lineCount{$_}++;
}

foreach my $key ( keys %lineCount ) {
        my $count = $lineCount{$key};
        print "$key: $count times\n";
}
```

Assuming your input file is called 'file.txt' just run it like so:

```
 perl count.pl file.txt 
```

---

### Post by ofnuts on 2013-02-28
> **greenpeace said:**
> Hi!

Maybe I'm oversimplifying it, but it almost seems like you might be able to do it by using the commands:

```
sort file.txt | uniq -c
```

Which will tell you the count of each unique line in file.txt

Would that work?

Cheers, 
Gp
I was going to suggest the same...

---

