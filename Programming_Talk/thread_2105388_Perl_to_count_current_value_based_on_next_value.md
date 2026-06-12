---
title: "Perl to count current value based on next value"
date: 2013-01-15
forum: Programming Talk
---

### Post by tzeronone on 2013-01-15
Currently I'm learning Perl and gnuplot. I would like to know how to count certain value based on the next value. For example:
```

#ID(X) Y
1 1
3 9
5 11

```

The output should show the value of the unknown ID as well. So, the output should show:
```

#ID(X) Y
1 1
(2) (5)
3 9
(4) (10)
5 11

```

The Y of ID#2 is based on the following:
((2-3)/(1-3))*1 + ((2-1)/(3-1))*9 which is
((X2-X3)/(X1-X3))*Y1 + ((X2-X1)/(X3-X1)) * Y3
Same goes to ID#5.

---

### Post by trent.josephsen on 2013-01-15
I suggest you write some Perl code to do it for you.

You have a formula, you know how to apply it to an input to get the desired output -- write an algorithm! It's not that hard, really. If you get stuck, post what you have.

---

### Post by tzeronone on 2013-01-15
I'm wondering how to get the next ID

---

### Post by tzeronone on 2013-01-15
This is what I have for current 
[I]#! /usr/bin/perl -w
use strict;

my $prev_id = 0;
my $prev_val = 0;
my $next_id;
my $next_val;

while (<>)
{
     my ($id, $val) = split;
     for (my $i = $prev_id + 1; $i < $id; $i++)
     {
          $val = (($id - $next_id) / ($prev_id - $next_id)) * $prev_val + (($id - $prev_id) / ($next_id - $prev_id)) * $next_val;
          printf ("%d %s\n", $i, $val);
     }
     printf ("%d %s\n", $id, $val);
     ($prev_val, $prev_id) = ($val, $id);
}[/I]

But how to declare the next value???

---

### Post by Vaphell on 2013-01-16
aren't you overwriting $val there inside the loop, just after reading from file? sloppiness doesn't have place in programming

---

### Post by tzeronone on 2013-01-16
Any idea to solve it?

---

### Post by Vaphell on 2013-01-16
don't overwrite $val and use separate variable to calculate in-between values?
you seem to not understand the purpose of your own variables.

have you tried:
- using seperate var for this line: *$val = (($id - $next_id) / ($prev_id - $next_id)) * $prev_val + (($id - $prev_id) / ($next_id - $prev_id)) * $next_val;* or even plugging the expression directly into printf() so you don't overwrite actual $val needed later?
- cleaning up the mess with variables that are used but never get any value, like $prev_id, $next_val, $next_id, and vice versa - $i not used anywhere? Your code doesn't use $i at all and it's the only thing that changes in the for-loop scope, you have to use it.
Decide if you want to use $i or $temporary_intermediary_id as the loop controller or whatever and stick to it.


```
#! /usr/bin/perl -w
use strict;

my ($prev_id, $prev_val) = (0,0);

while (<>)
{
  my ($id, $val) = split;
  for( my $temp_id=$prev_id+1; $prev_id>0 && $temp_id<$id; $temp_id++ )
  {
    printf( "*%s is between %s(%s) and %s(%s) <- all numbers required to generate value, use them!\n", $temp_id, $prev_id, $prev_val, $id, $val );
  }
  printf( "%d %s\n", $id, $val );
  ($prev_id, $prev_val) = ($id, $val);
}

```
```
$ ./num2.pl <<< $'1 1\n5 17\n9 25'
1 1
*2 is between 1(1) and 5(17) <- all numbers required to generate value, use them!
*3 is between 1(1) and 5(17) <- all numbers required to generate value, use them!
*4 is between 1(1) and 5(17) <- all numbers required to generate value, use them!
5 17
*6 is between 5(17) and 9(25) <- all numbers required to generate value, use them!
*7 is between 5(17) and 9(25) <- all numbers required to generate value, use them!
*8 is between 5(17) and 9(25) <- all numbers required to generate value, use them!
9 25

```

---

### Post by tzeronone on 2013-01-17
> **Vaphell said:**
> don't overwrite $val and use separate variable to calculate in-between values?
you seem to not understand the purpose of your own variables.

have you tried:
- using seperate var for this line: *$val = (($id - $next_id) / ($prev_id - $next_id)) * $prev_val + (($id - $prev_id) / ($next_id - $prev_id)) * $next_val;* or even plugging the expression directly into printf() so you don't overwrite actual $val needed later?
- cleaning up the mess with variables that are used but never get any value, like $prev_id, $next_val, $next_id, and vice versa - $i not used anywhere? Your code doesn't use $i at all and it's the only thing that changes in the for-loop scope, you have to use it.
Decide if you want to use $i or $temporary_intermediary_id as the loop controller or whatever and stick to it.


```
#! /usr/bin/perl -w
use strict;

my ($prev_id, $prev_val) = (0,0);

while (<>)
{
  my ($id, $val) = split;
  for( my $temp_id=$prev_id+1; $prev_id>0 && $temp_id<$id; $temp_id++ )
  {
    printf( "*%s is between %s(%s) and %s(%s) <- all numbers required to generate value, use them!\n", $temp_id, $prev_id, $prev_val, $id, $val );
  }
  printf( "%d %s\n", $id, $val );
  ($prev_id, $prev_val) = ($id, $val);
}

```
```
$ ./num2.pl <<< $'1 1\n5 17\n9 25'
1 1
*2 is between 1(1) and 5(17) <- all numbers required to generate value, use them!
*3 is between 1(1) and 5(17) <- all numbers required to generate value, use them!
*4 is between 1(1) and 5(17) <- all numbers required to generate value, use them!
5 17
*6 is between 5(17) and 9(25) <- all numbers required to generate value, use them!
*7 is between 5(17) and 9(25) <- all numbers required to generate value, use them!
*8 is between 5(17) and 9(25) <- all numbers required to generate value, use them!
9 25

```

How about the interpolation part? Any idea?

---

### Post by Tony Flury on 2013-01-17
This is almost exactly the same problem as this thread : 

[http://ubuntuforums.org/showthread.php?t=2103750](http://ubuntuforums.org/showthread.php?t=2103750)

and this one :

[http://ubuntuforums.org/showthread.php?t=2103383](http://ubuntuforums.org/showthread.php?t=2103383)

The first one is marked as solved.

One of the arts of programming is re-use - so adapt the solution previously provided.

---

### Post by Vaphell on 2013-01-17
cheesus, do you really need the expression spelled out?
```
*6 is between 5(17) and 9(25)
```
you have 5(17) < 6(x) < 9(25), assuming linear interpolation find x.
hint: prev_id(prev_val) < temp_id(???) < id(val)

---

### Post by iMac71 on 2013-01-17
> **Vaphell said:**
> assuming linear interpolationI think that the point be exactly this one: is the interpolation linear or not?
I guess not, because otherwise the algorithm would be very simple; but if the interpolation isn't linear, the unknown values would be unpredictable without more informations about their sequence.

---

### Post by trent.josephsen on 2013-01-17
The formula OP gave is just linear interpolation when you know y[n-1] and y[n+1] and have to find y[n]. (Actually in that particular case it simplifies greatly, but you need the general formula to interpolate with a gap of 2 or more.)

---

### Post by tzeronone on 2013-01-17
> **Tony Flury said:**
> This is almost exactly the same problem as this thread : 

[http://ubuntuforums.org/showthread.php?t=2103750](http://ubuntuforums.org/showthread.php?t=2103750)

and this one :

[http://ubuntuforums.org/showthread.php?t=2103383](http://ubuntuforums.org/showthread.php?t=2103383)

The first one is marked as solved.

One of the arts of programming is re-use - so adapt the solution previously provided.

They are not the same...

---

### Post by tzeronone on 2013-01-17
> **iMac71 said:**
> I think that the point be exactly this one: is the interpolation linear or not?
I guess not, because otherwise the algorithm would be very simple; but if the interpolation isn't linear, the unknown values would be unpredictable without more informations about their sequence.

It is linear which based on two points.

---

### Post by tzeronone on 2013-01-17
> **trent.josephsen said:**
> The formula OP gave is just linear interpolation when you know y[n-1] and y[n+1] and have to find y[n]. (Actually in that particular case it simplifies greatly, but you need the general formula to interpolate with a gap of 2 or more.)

Correct

---

### Post by iMac71 on 2013-01-18
the following script might be what you're looking for:[PHP]my $loop = 1;

while (<>)
{
    my $delta_x, $x_i, $y_i, $x_k, $y_k;
    if ($loop == 1) {
        ($x_i, $y_i, $x_k, $y_k) = split
    }
    else {
        ($x_i, $y_i) = ($x_k, $y_k);
        ($x_k, $y_k) = split
    }
    $delta_x = ($x_k - $x_i) / 2;
    my $x_j = $x_i + $delta_x;
    my $y_j = (($x_j - $x_k) / ($x_i - $x_k)) * $y_i + (($x_j - $x_i) / ($x_k - $x_i)) * $y_k;
    print $x_i,"\t",$y_i,"\n(",$x_j,")\t(",$y_j,")\n";
    $loop++;
}[/PHP]when you run the script, the data should be entered as follows:
- first input line: two couples of coordinates (i.e. two points);
- next input lines: a couple of coordinates (i.e. one point).

---

