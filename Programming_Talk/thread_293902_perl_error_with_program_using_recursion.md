---
title: "perl error with program using recursion"
date: 2006-11-05
forum: Programming Talk
---

### Post by baldy1324 on 2006-11-05
hi i have a program that i tweaked from python (which i know) to perl (changed syntax). here is the program.```
#!/usr/bin/perl

sub fib($n)
{
        if ($n<2)
        {
                return 1;
        }
        else
        {
                return fib($n-1) + fib($n-2);
        }
}

$n = 1;
while ($n < 42)
{
        print fib($n);
        print " ";
        $n = $n + 1;
}

```

when i run the program i get the following. ```
Not enough arguments for main::fib at fibrecursion.pl line 18, near "$n)"
Execution of fibrecursion.pl aborted due to compilation errors.

```
any help would be appreciated
thanks

---

### Post by DaveBorealis on 2006-11-05
I made two changes.  I added the '&' to the function call so the argument $n is fed into it, and I changed $n to $i within the function itself ($i receives the argument $n) to limit the scope of $n to only the while loop as its value alone is passed to the function.
```
#!/usr/bin/perl

sub fib()
{
        $i = shift;
        if ($i<2)
        {
                return 1;
        }
        else
        {
                return fib($i-1) + fib($i-2);
        }
}

$n = 1;
while ($n < 42)
{
        print &fib($n);
        print " ";
        $n = $n + 1;

```
Don't know if this is what it's supposed to do as I didn't look that closely at the code logic, but maybe this'll get you started.

HTH,
Dave

---

### Post by Houman on 2006-11-05
hi there, 

I was able to get the program runnig correctly but i dont know why your version didnt work, hopefulyl an expert will come and tell us. But here is the working version of your Fibonacci function:

```

#!/usr/bin/perl

use strict;

my $n = 1;
while ($n < 42)
{
        print &fib($n) . "    for n=" . $n  . "\n";
        
        $n = $n + 1;
}

sub fib()
{
        my $i = shift;
	if ($i==0)
        {
                return 0;
        }
        if ($i==1)
        {
                return 1;
        }
        else
        {
                return fib($i-1) + fib($i-2);
        }
}

```

try to use use strict, this will force you to adopt some good perl programming practices, such as using "my" for variables (basically making them local variables)

regards

Houman

---

