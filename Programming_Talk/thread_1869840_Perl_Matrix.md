---
title: "Perl Matrix"
date: 2011-10-26
forum: Programming Talk
---

### Post by hailholyghost on 2011-10-26
Hey Linux experts,

I am trying to build a comparison matrix.  I have 1,404 files like so:

```

      0.10 -31.562261
      0.20 -39.978555
      0.30 -37.591921
      0.40 -29.438210
      0.50 -29.701931
      ....
      1999.90 87.763189
      2000.00 72.684833
```

I want to build a 20,000x20,000 comparison matrix, where each element in the matrix represents the difference in values from other elements in the matrix.

For example, element i,j would represent the difference in values of i and j.  Only half of the matrix is necessary (i.e. i>=j, j<i is redundant because the matrix is symmetric).

I am trying to make a "compare" matrix with elements [i,j] but I'm a newb with Perl, unfortunately.

I have tried the following but it doesn't work:

```
#!/usr/bin/perl

use strict;
use warnings;

my $pi = 3.142; #define pi

open(FILE, "<alpha2.99"); #open file for FILE
	while (<FILE>)
	{
		my @a = split;
		my $phi = $a[1];
		my($i,$j);
		for ($i=1; $i < 20000; $i++)
		{
		my @compare;
			for ($j=$i; $j<20000; $j++)
			{
				@compare[$i,$j]=$a[$i]-$a[$j]
			}
		}
	}
close(FILE);
```

Your expertise is greatly appreciated ):P

---

### Post by 11jmb on 2011-10-26
I'm not understanding what you're trying to do here. Will each file have its own 20000x20000 matrix?

can you please be a bit more clear about your expected input and results?

---

### Post by karlson on 2011-10-26
> **hailholyghost said:**
> Hey Linux experts,

I am trying to build a comparison matrix.  I have 1,404 files like so:

```

      0.10 -31.562261
      0.20 -39.978555
      0.30 -37.591921
      0.40 -29.438210
      0.50 -29.701931
      ....
      1999.90 87.763189
      2000.00 72.684833
```

I want to build a 20,000x20,000 comparison matrix, where each element in the matrix represents the difference in values from other elements in the matrix.


You might want to consider doing something other then perl for this, like R, S, Matlab.

In addition I still don't understand the problem.  Are you trying  for each file to create a difference matrix of the differences of element 1 with each of the 20000 elements in the vector you are reading?

---

### Post by hailholyghost on 2011-10-26
> I'm not understanding what you're trying to do here. Will each file have its own 20000x20000 matrix?


Yes, sir!  Each of the 1,404 files will have its own 20,000x20,000 matrix.

---

### Post by karlson on 2011-10-26
> **hailholyghost said:**
> Yes, sir!  Each of the 1,404 files will have its own 20,000x20,000 matrix.

```

my @data = ();
my $i = 0;
while(<FILE>)
{
    chomp;
    my ($param, $value) = split;
    $data[$i++] = $value;
}

my @matrix[$#data+1][$#data+1];
for($i = 0 ; i <= $#data; ++$i )
{
    for($j = 0 ; $j <= $#data ; ++$j )
    {
        $matrix[$i][$j] = $data[$i] - $data[$j];
    }
}

```

This code has bugs in it but the gist is clear.  Even though I would still use R or S for this.

P.S. Just curious as to why would someone require Perl for a linear algebra program?

---

### Post by hailholyghost on 2011-10-26
> **karlson said:**
> 
P.S. Just curious as to why would someone require Perl for a linear algebra program?

Programming is a new thing for me; I have ~55 GB of simulations to process.  I'm a chemist so programming wasn't a skill-set I got in college.  Whether I do this in Perl or any other language doesn't matter to me.  I wasn't aware that Perl wasn't optimized for linear algebra.

One curious thing though, I think I've worked out the bugs in your program, and I've got:

```
#!/usr/bin/perl -w

open(FILE, "<alpha2.99"); #open test file
my @data = (); #declare arrays 'matrix' and 'data'
while(<FILE>) #read the file
{
	chomp;
	my ($time, $value) = split;
	$data[$i++] = $value;
}
my @matrix;
for($i = 0; $i <= 20000; ++$i)
{
	for($j = 0; $j <= 20000; ++$j)
	{
		$matrix[$i][$j] = $data[$i]-$data[$j];
		print "$matrix[$i][$j] ";
	}
}
close(FILE);
```

To be able to read this file, do you know how I could get Perl to write this as a true Matrix so I could read [row,column]?


I appreciate your time!  Thank you so much karlson!

---

### Post by karlson on 2011-10-26
> **hailholyghost said:**
> Programming is a new thing for me; I have ~55 GB of simulations to process.  I'm a chemist so programming wasn't a skill-set I got in college.  Whether I do this in Perl or any other language doesn't matter to me.  I wasn't aware that Perl wasn't optimized for linear algebra.

Wasn't designed for it.

Learn and use R it is designed for statistical analysis, which is exactly what you are trying to do.

> 

To be able to read this file, do you know how I could get Perl to write this as a true Matrix so I could read [row,column]?


Not sure I understand the question.  If you want to address something as a mathematical matrix I suggest looking at CPAN for a module to do this.

Although my original suggestion still stands.  I'd use R for this.  Don't have access to one right now but the code would be much simpler.

---

