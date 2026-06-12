---
title: "PERL: Foreach loop not ending"
date: 2009-10-27
forum: Programming Talk
---

### Post by MiniStephan on 2009-10-27
I'm starting to learn perl and I figured an interesting program to make would be a quicksort algorithm.  I haven't even gotten to the actual algorithm and I'm having issues.  This is what I have:

```
#!/usr/bin/perl

@array;

print "Enter 10 numbers:\n";

foreach (0..9) {
    print ($_ + 1);
    print ": ";
    $array[$_] = <>;
    chomp($array[$_]);
}

print "Done"; # to be printed when ended

```

It never gets to the Done part and simply keeps asking for input once it gets the last value.  What am I doing wrong?

---

### Post by diesch on 2009-10-27
"<>" reads a whole line, so it asks 10 times for the numbers and then prints "Done".

If you want it to read a line containing 10 numbers you have to read the line using "<>" and then split it to get the numbers.

---

### Post by nvteighen on 2009-10-27
I fail to see what's wrong with your code. It works as it should.

The only stylistic issue is that instead of **$array[$_] = <>;** would be usually written **push @array, <>;** (push inserts stuff at an array's tail).

---

### Post by MiniStephan on 2009-10-27
Okay, so I figured out that my problem was later on (for some strange reason).  Anyway, Now my problem is that I'm stuck in an infinite loop, and I can't figure out where.  Here's my complete code:

```
#!/usr/bin/perl

@array;

print "Enter 10 numbers:\n";

foreach (0..9) {
    print ($_ + 1);
    print ": ";
    $array[$_] = <>;
    chomp($array[$_]);
}

@array = &quicksort;

foreach (@array) { print "$_\n"; }



sub quicksort {
    if (scalar(@array) <= 1) {
        return @array; }

    local(@less, @greater, @sorted, $pivot);
    $pivot = $array[scalar(@array) - 1];

    foreach(@array) {
        if ($_ < $pivot) { push @less, $_; }
        else { push @greater, $_; }
    }

    push @sorted, &quicksort(@less), $pivot, &quicksort(@greater);
    return @sorted;
}
```

---

### Post by nvteighen on 2009-10-27
There are multiple problems in your code.

1. You're effectively using globals because you seem to not know how to pass arguments to a Perl sub. Well... the "shift" operator is used to shift across @_, which takes the values of the argument's list. What I did is to divide the thing into two subs and call main.

2. You don't use the & operator to call functions. If you know any C, & in Perl takes exactly the same meaning as in C: "get the address of something"... (well, in Perl this is not that exactly, but...).

3. A problem in Perl is that you can't pass @lists directly as arguments because they get interleaved with the whole argument list. The way to "preserve" the list is using a reference...

4. Your algorithm lacks the step in which you delete the pivot from the array.

Here's my code:
```

#!/usr/bin/perl


sub main {
    my @array = ();

    print "Enter 10 numbers:\n";

    foreach (0..2) {
        print ($_ + 1);
        print ": ";
        $array[$_] = <STDIN>;
        chomp($array[$_]);
    }
    
    @array = quicksort(\@array);

    print "@array\n";
}

sub quicksort {
    my $array = shift;

    if (scalar(@$array) <= 1) {
        return @$array; }

    my $less = [];
    my $greater = [];
    my $sorted = [];
    my $pivot = pop @$array; # pivot has to be removed from array

    foreach(@$array) {
        if ($_ <= $pivot) { push @$less, $_; }
        else { push @$greater, $_; }
    }

    push @$sorted, quicksort($less), $pivot, quicksort($greater);
    return @$sorted;
}

main;

```

---

### Post by myrtle1908 on 2009-10-27
As an aside, it is good practice to use the warnings and strict modules in your scripts ie.

```
use strict;
use warnings;
```

These help to identify problem with your code.

Also, re. the use of ampersand to call functions ... this used to be the way (eg. perl4) but has been discouraged since perl5.  Nowadays the & sigil is correct when you're referring to the subroutine, but not calling it.

---

### Post by MiniStephan on 2009-10-28
Oh, it's working wonderfully now.  Thank you all so much for your help!  nvteighen and myrtle1908, your insights have helped me understand perl the little bit i needed for this to work.  Hopefully I can get my programs to work on my own in the future!

---

