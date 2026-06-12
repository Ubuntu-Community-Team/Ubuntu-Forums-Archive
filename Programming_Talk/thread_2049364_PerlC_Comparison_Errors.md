---
title: "Perl/C Comparison Errors"
date: 2012-08-28
forum: Programming Talk
---

### Post by hailholyghost on 2012-08-28
Hello everyone,

I wrote a C program to produce an output file which is 29,800 lines long which looks like:
```

  20.0 27
  20.1 27
  20.2 27
  20.3 27
  20.4 27
...
3000.1 10
3000.2 10
3000.3 10
3000.4 10
3000.5 10
```

29,800 is the correct number of lines.  However, (3000.5-20.0)*10 = 29805.  That is, there are five skips in the program.  It should end at 3000.0 but it contines beyond.

I wrote a Perl program to find the skipped lines:
```
#!/usr/bin/perl

use strict;
use warnings;

open (FH,"<tmp") or die "tmp: $!";
my $previous = 19.9;
while (<FH>) {
   my $should = $previous+0.1;
   my @tmp = split;
   print "Previous = $previous, tmp[0] = $tmp[0], should = $should\n";
   if ($tmp[0] != $should) {
      print "$tmp[0] does not equal $should\n";
   }
   $previous = $tmp[0];
}
close FH;
```

but this produces anomalous results:
```

Previous = 19.9, time = 20.0, should = 20
Previous = 20.0, time = 20.1, should = 20.1
Previous = 20.1, time = 20.2, should = 20.2
20.2 does not equal 20.2
Previous = 20.2, time = 20.3, should = 20.3
Previous = 20.3, time = 20.4, should = 20.4
20.4 does not equal 20.4
Previous = 20.4, time = 20.5, should = 20.5
Previous = 20.5, time = 20.6, should = 20.6
Previous = 20.6, time = 20.7, should = 20.7
20.7 does not equal 20.7
Previous = 20.7, time = 20.8, should = 20.8
Previous = 20.8, time = 20.9, should = 20.9
20.9 does not equal 20.9
```

and a C program produces the same error (formatting written so output is identical):
```
#include <stdlib.h>
#include <stdio.h>

int main() {
 FILE *ftmp;
 ftmp = fopen("tmp","r");
 if (ftmp != NULL) {
    double time, score, previous = 19.9;
    while(!feof(ftmp)) {
       if (fscanf(ftmp,"%lf %lf",&time,&score) != 2) {
          continue;
       }
       double should = previous+0.1;
       printf("Previous = %3.1f, time = %3.1f, should = %3.1f\n",previous,time,should);
       if (should != time) {
          printf("%3.1f does not equal %3.1f\n",should,time);
       }
       previous = time;
    }
    fclose(ftmp);
 }
 return 0;
}
```

Why do these comparisons fail?  I feel like this is a noobish error and I'll be embarrassed when I hear the answer, but I really don't see the mistake.

Thanks so much!

-D

---

### Post by Bachstelze on 2012-08-28
Whenever floating-point numbers behave weirdly, it's probably a rounding error. Use integers.

---

### Post by trent.josephsen on 2012-08-28
Bachstelze is correct, but I'd also like to observe that when calculating the number of skips you have an off-by-one error: 20.0 to 3000.5 inclusive in steps of 0.1 is 29806, not 29805. You should be looking for 6 skipped values.

If the number of lines should be 29800, then you will need to end the (non-skipped) sequence at 2999.9.

---

### Post by Vaphell on 2012-08-28
there are 2 ways one can tackle such a problem
- change the condition of equality to one checking if the difference of compared values is within a safe threshold (eg. |x-y| < 0.001)
- assuming fixed precision, translate data to integers (eg 0.1 -> 1, 1->10) for logic and reverse translation only for presentation purposes and for final output, eg. printf(..., x/10.0, y/10.0)

---

### Post by hailholyghost on 2012-08-28
> **Bachstelze said:**
> Whenever floating-point numbers behave weirdly, it's probably a rounding error. Use integers.

yep!  I took what you said, and now the comparisons work.  The problem is that there is some foreknowledge of the values required with the way I did it.  However, this does allow more accurate counting in for loops.

[QUOTE=Vaphell] there are 2 ways one can tackle such a problem
- change the condition of equality to one checking if the difference of compared values is within a safe threshold (eg. |x-y| < 0.001)
- assuming fixed precision, translate data to integers (eg 0.1 -> 1, 1->10) for logic and reverse translation only for presentation purposes and for final output, eg. printf(..., x/10.0, y/10.0) [/QUOTE]

Vaphell, I think the way you did it is way better!  I would rewrite the program to do that but I have many other things to do :-(

[QUOTE=trent.josephsen] Bachstelze is correct, but I'd also like to observe that when calculating the number of skips you have an off-by-one error: 20.0 to 3000.5 inclusive in steps of 0.1 is 29806, not 29805. You should be looking for 6 skipped values.

If the number of lines should be 29800, then you will need to end the (non-skipped) sequence at 2999.9. [/QUOTE]

Yea I should've noticed that ](*,)

The solution I used was to have an integer count incremented (previous_int), and each step take a temporary double (tmp), which preserves accuracy.  Here is the program which worked:

```
#include <stdlib.h>
#include <stdio.h>

int main() {
 FILE *ftmp;
 ftmp = fopen("tmp","r");
 if (ftmp != NULL) {
    double time, score;
    unsigned int previous_int = 199;
    while(!feof(ftmp)) {
       if (fscanf(ftmp,"%lf %lf",&time,&score) != 2) {
          continue;
       }
       double previous = previous_int;
       previous /= 10;
       double tmp = previous_int+1;
       double should = tmp/10;
       printf("Previous = %3.1f, time = %3.1f, should = %3.1f\n",previous,time,should);
       if (should != time) {
          printf("%3.1f does not equal %3.1f\n",should,time);
       }
       previous_int++;
    }
    fclose(ftmp);
 } else {
    printf("Could not open tmp\n");
 }
 return 0;
}
```

My only concern is that this solution does not work with Perl.  However, Vaphell's comparison idea would have worked.

many thanks to Vaphell, trent.josephsen, and Bachstelze!

---

### Post by Tony Flury on 2012-08-29
Note : doubles do not preserve accuracy - all they do is reduce the inaccuracy window.

Using any sort of fixed length representation there will always be some values which are impossible to represent accurately, the best you can hope for is accuracy within certain limits, and as suggested by Vaphell you should always compare floating point numbers using some sorrt of ranging mechanism.

If you are really interested have a looking at how floating point numbers are represented in binary - just as integers are represented by a conditional sum of values of the power of 2 - i.e. 5 is 101 (1x2^2 + 1x2^0), decimal parts are represented by the conditional sum of values of the power of 1/2 - i.e. 0.75 is 0.11 (1x(1/2)^1 + 1x(1/2)^2: i.e. 1/2 + 1/4).

So how do you represent 1/3 - the answer is you can't not accurately - you can get close, but not exactly - the representation of 1/3 is 0.01001100110001... (1/4 + 1/32 + 1/64 + 1/512 + 1/1024 + 1/8192 ..... = 0.2999267578125 - and you can keep going as long as you want you will never get to exactly 1/3)

---

