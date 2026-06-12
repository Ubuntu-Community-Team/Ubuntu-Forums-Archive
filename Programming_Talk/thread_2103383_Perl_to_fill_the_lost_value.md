---
title: "Perl to fill the lost value"
date: 2013-01-10
forum: Programming Talk
---

### Post by tzeronone on 2013-01-10
I need a perl that will fill the lost value in the text file. For example
```

1 1
4 16
9 81

```
Is perl able to fill the lost value so the output will be
```

1 1
2 4
3 9
4 16
5 25
6 36
7 49
8 64
9 81

```
Anyone?

---

### Post by lisati on 2013-01-10
*Thread moved to **Programming Talk**.*

Is this homework?

---

### Post by tzeronone on 2013-01-10
No... Just want to learn perlscript in solving the problem.. I have wrote it but still fail..

---

### Post by ofnuts on 2013-01-10
> **tzeronone said:**
> I need a perl that will fill the lost value in the text file. For example
```

1 1
4 16
9 81

```Is perl able to fill the lost value so the output will be
```

1 1
2 4
3 9
4 16
5 25
6 36
7 49
8 64
9 81

```Anyone?
How do you tell there is a lost "value" and what it should be?

---

### Post by tzeronone on 2013-01-10
```

1 1
4 16
9 81

```

```

1 1
2 4
3 9
4 16
5 25
6 36
7 49
8 64
9 81

```

Look at the first code, we see the ID of 1,4,9. But the ID of 2, 3,5,6,7,8 is empty. Same goes with their square.

---

### Post by Vaphell on 2013-01-10
> **tzeronone said:**
> No... Just want to learn perlscript in solving the problem.. I have wrote it but still fail..

show your efforts

---

### Post by lisati on 2013-01-10
> **tzeronone said:**
> 
Look at the first code, we see the ID of 1,4,9. But the ID of 2, 3,5,6,7,8 is empty. Same goes with their square.

To follow on from ofnuts has asked, if you were to write a program to analyse a list of numbers, how would the program "know" that 3,5,6,7, and 8 are missing from the list in the first column?

What have you got so far in your search for a solution?

---

### Post by Vaphell on 2013-01-10
assuming ascending order, my awk solution takes like 20 characters and doesn't test for missing numbers at all. hint: for-loop using neighboring id's

---

### Post by tzeronone on 2013-01-10
Here is my code
```

#! /usr/bin/perl -w
use strict;

my $index;
my $m_square;
while (<>) {
  my ($ID, $square) = split;
  for ($index=1; $index<=9; $index++)
  {
    if ($index=$ID)
    {
      print $_;
    }
    else
    {
      $m_square = $index ** 2;
      print("$index $m_square");
    }
  }
}

```

---

### Post by Vaphell on 2013-01-10
```
awk 'BEGIN{ n=1; } { for( i=n; i<=$1; i++ ) print i, i*i; n=$1+1; }'
```
$1 = 1st column (id) obviously
n = previous id
for each line print i, i^2 where i is in previous_id+1..id range

---

### Post by tzeronone on 2013-01-10
that is awk, how about perl?

---

### Post by lisati on 2013-01-10
I'm not a Perl programmer, but will try to offer a hint here. Hopefully I've properly understood what you are hoping to achieve.

Suppose I have an [array]("http://www.tutorialspoint.com/perl/perl_arrays.htm") that has the first column of your sample data loaded. As I scan through the array, I would expect item number 1 to be 1, item number 2 to be 2, and so on through the list. As soon as I discover a situation where item # "X" isn't "X", I know that I have to fill in the gaps: this can be achieved by another loop within the main loop.

---

### Post by Vaphell on 2013-01-10
not that i know perl ;-)

trial and error:
```
#! /usr/bin/perl -w
use strict;

my $n=1;
my $i;
my $sq;
while (<>)
{
  my( $id, $sq ) = split;
  for( $i=$n; $i<=$id; $i++ )
  {
    printf( "%d %d\n", $i, $i**2 );
    $n = $id + 1;
  }
}
```
i don't need sq variable at all but i have no idea how to get rid of it :)

---

### Post by tzeronone on 2013-01-10
Vaphell, it doesn't do any lost number checking...

---

### Post by lisati on 2013-01-10
> **tzeronone said:**
> Vaphell, it doesn't do any lost number checking...

Most programming and scripting languages have an "if" statement (or similar) that can be used for that sort of thing. Have a look here: [http://perl.about.com/od/gettingstartedwithperl/a/Comparing-Values-In-Perl.htm](http://perl.about.com/od/gettingstartedwithperl/a/Comparing-Values-In-Perl.htm)

---

### Post by ofnuts on 2013-01-10
> **tzeronone said:**
> Vaphell, it doesn't do any lost number checking...
Well, you have not told us how you consider a number 'lost'/'missing'. If you have an incomplete sequence of numbers, and for each number a computed value that you know how to recompute easily if necessary, checking the original sequence for "holes" doesn't do you any good, it's easier to regenerate the whole sequence form scratch as Vaphell does.

If your existing values are more like exceptions to the computed values (3 values out of 9), then generate the default sequence and replace by the exceptions where needed.

---

### Post by Vaphell on 2013-01-10
> **tzeronone said:**
> Vaphell, it doesn't do any lost number checking...

if the order is ascending, you can assume that any number between previous_id and current_id is missing. You only need to modify loop a bit to ignore ids themselves

```
#! /usr/bin/perl -w
use strict;

my $n=0;
my $i;
my $sq;
while (<>)
{
  my( $id, $sq ) = split;
  for( $i=$n+1; $i<$id; $i++ ) { printf( "%d %d\n", $i, $i**2 ); }
  $n = $id;
}
--------------
$ ./test.pl <<< $'2 2\n5 25\n9 81'
1 1
3 9
4 16
6 36
7 49
8 64

```

---

### Post by tzeronone on 2013-01-10
Ok. seems like many people misunderstand my question. let's see this code
```

1
5
9

```

i would like to have a perl that will check the sequence number 1 to 9. if the number is exist, it will print the number, else it will print "not exist number". It is a kind of if else inside for loop. The output will be
```

1
2
3
4
5
6
7
8
9

```
Here is my temporary code
```

#! /usr/bin/perl -w
use strict;
while (<>){
  my ($ID) = split;
  for ($index=1; $index<=9; $index++)
  {
    if ($index == $ID)
    {
      print $ID;
      printf("\n");
    }
    elsif ($index != $ID)
    {
      print $index;
    }
    else
    {
      printf ("\n");
    }
  }
}

```
but the output is
```

1
234567891234
56789123456789

```
Any Idea???

---

### Post by Vaphell on 2013-01-11
> Ok. seems like many people misunderstand my question. let's see this code...

Your initial post was about finding/restoring missing values and that's it. There are many ways to skin the cat and you didn't explicitly say 'check each id against the fixed range of possibilities and print out each number with a flag indicating success/failure next to it'.
Taking a shortcut exploiting properties of the input is called 'being smart'.

> but the output is
```

1
234567891234
56789123456789

Any Idea???
```

without the full set of ids at hand you won't get anywhere. The act of checking a single id against 1-9 range will tell you only what you already know - that it exists in that range. To know what's missing, you need to compile data for all id's (missing numbers must fail the test in case of ALL id's)

```
#! /usr/bin/perl -w
use strict;

my @a = (('!') x 10);

while (<>)
{
  my( $id ) = split;
  $a[$id] = '';
}

for my $i (1..$#a) { printf( "%d %s\n", $i, $a[$i] ); }
```
array of '!'
for each id mark id-th element as ok (''). After processing all ids, the elements still having value of '!' indicate missing number.
that will work in any case.

If you have sorted data, you can take advantage of that. You can start from 1 and increment until you get id match. Every number preceding that event is missing. Read next id, start incrementing where you left it, wash, rinse, repeat. Coincidentally it's more or less the approach i used earlier.
In case of unsorted input it might be worthwhile to sort it and use this method instead of more general one with array.

---

