---
title: "Perl: illegal division by 0 (not as simple as you think)"
date: 2011-02-20
forum: Programming Talk
---

### Post by hailholyghost on 2011-02-20
Hey all,

I have 88 text files, two columns each, named 02-89. A sample is shown below:

0.10 5.563218
0.20 5.122440
0.30 4.901420
0.40 5.098015

This goes down to 250.0, totaling 2500 lines altogether for each file. I have checked that they are all the same.

I wrote a shell script to process them:
"#!/bin/tcsh -f

foreach i ($argv)
cat $i | field 2 | pca '1/$1**6' | avg | grep Mean | field 2 | pca '$1**(-1/6)'
end"

The "field" command just grabs the 2nd column, "pca" is an arithmetic script, "avg" gives statistical data.

When I execute the script on my lab's Red Hat Linux desktop (I use Lucid Lynx), I use:

"$ ./noe2.sh ?? > distances.99"

I get the error:

"Illegal division by zero at /malatya02b/con/bin/avg line 16, <> line 2500"

The really perplexing problem is that this works FINE for individual files. I only get the above error when I run the shell command "$ ./noe2.sh ?? > distances.99".  There could be a connection between 2500 and that there are 2500 lines per file.

The "avg" file I mentioned is presented here, with line 16 (presumably the source of the problem is "$mean = $sum / $n;"). I don't understand why $n is 0, all of the files are almost exactly the same size so they should all work the same.

#!/usr/bin/perl -w

$num = '(\-?\d+(?:\.\d+)?(?:[eE]\-?\d+)?)';

while(<>) {
push(@b,$1) if /$num/;
}

$n = $sum = 0;

foreach (@b) {
$n++;
$sum += $_;
}

$mean = $sum / $n;

@a = sort numerically @b;

$high = $a[$n-1];
$median = $a[$n/2];
$low = $a[0];

foreach (@a) {
$sumsqdev += ($_ - $mean) ** 2;
}

$variance = $sumsqdev/$n;
$stddev = sqrt($variance);
$err = sqrt($variance/$n);

print <<EOF;
N: $n
Sum: $sum
High: $high
Low: $low
Mean: $mean
Median: $median
Variance: $variance
Standard Deviation: $stddev
Error: $err

EOF

sub numerically { $a <=> $b; }"

Any help is greatly appreciated :popcorn:
If I need to provide more info, please let me know.

Much appreciated!

---

### Post by sanderj on 2011-02-20
$n stays 0 (thus giving division error) if @b stays empty ... so set an alert/debug on an empty @b.

@b can stay empty if the while is not entered or if the 'if /$num/' does never match. So set alerts/debugs on that too.

HTH

---

### Post by hailholyghost on 2011-02-22
Hi sanderj,

I fixed the problem, it was actually due to an error in the generation of the files... though I'm still not sure what it was...

Thanks for your efforts!!

Have a great day!

---

