---
title: "Perl display length  of arrays in the array"
date: 2010-10-05
forum: Programming Talk
---

### Post by Dwood15 on 2010-10-05
Hey I'm having a problem with the following code:
```

my $length_of_array = @matrix;
print "Number of rows $length_of_array \n";

for my $i (0..$#matrix) {
            my $length = $matrix[$i];
            print "$length\n";
            }

print "Hey this shows not what I want it to! \n";

```

I've googled around and it seems that people's answers to my questions were basically the exact same however it does not work for me! :confused:

Instead of displaying the length of my 2 array(s) it returns references to the arrays inside the array in memory!

I am running perl 5.10.1

---

### Post by Some Penguin on 2010-10-05
References are scalars, that's why.  Dereference the list and then take the scalar of it.

> 
my $lref= +[ 1, 2, 3];
my $len_of_lref = scalar @$lref;

print $len_of_lref, "\n";


---

### Post by Dwood15 on 2010-10-05
> **Some Penguin said:**
> References are scalars, that's why.  Dereference the list and then take the scalar of it.

That did not work, sadly :( 

When you said to dereference I did what you were telling me, and I even looked around but did not get what I was looking for.

here's the full code:

```
sub array

{

#Shows how to get a multi-dimensional array's values
my @matrix = (

    [0, 1, 1, 0, 0],

    [0, 0, 1, 1, 0],

    [1, 0, 1, 0, 0],

    [1, 0, 0, 0, 1]
    );
    my  $completed = 0 ;
    
for($row = 0; $row < 4; $row++) {
  for( $col = 0; $col < 5; $col++) {
      print "$matrix[$row][$col]";
   }
   print "\n";
   
}


my $length_of_array = @matrix;
print "Number of rows $length_of_array \n";

for my $i (0..$#matrix) {
      #      my @length = @$matrix[$i];
      $length = ${@$matrix->[$i]};
            print "$length";
            }

}

```

---

### Post by Some Penguin on 2010-10-05
You're being very inconsistent with how you're using sigils and variables.  

Better:

```

my @matrix = ( +[ 1, 2, 3 ], +[ 4, 5, 6], +[ 7, 8, 9] );

my $row0col1 = $matrix[0]->[1];
my $row0aslist = @{$matrix[0]};
my $length_of_row0 = scalar @{$matrix[0]};
my @col0aslist = map { $_->[0] } @matrix;

```

---

### Post by Dwood15 on 2010-10-05
Thanks for helping me get the values I wanted, I was being inconsistent because I was trying everything I possibly could to get it to work! xD

And as a note, $row0aslist only gives the value of the number of items in the row, not the actual items in the row if you were trying to get that, as it seems.

---

### Post by Some Penguin on 2010-10-05
Good catch.  Should have been @row0aslist, of course -- otherwise, it's triggering implicit conversion.

---

### Post by Dwood15 on 2010-10-06
> **Some Penguin said:**
> Good catch.  Should have been @row0aslist, of course -- otherwise, it's triggering implicit conversion.

I checked that out in my perl to see if that worked, and it still only returned the number of values in the first row! 

At that point, however you could set @row0aslist = @matrix[0] couldn't you?

Also, since you seem to be knowledgeable i'm running a personal project to traverse the arrays using a DFS... (basically, following the 0's from 0,0 to the right side)

I saw that there was a module for that here: [http://search.cpan.org/~friedo/Data-Traverse-0.03/lib/Data/Traverse.pm](http://search.cpan.org/~friedo/Data-Traverse-0.03/lib/Data/Traverse.pm)

Think that would be useful for what i'm going for? (obviously because of my newness I don't entirely understand what's going on there...)

---

### Post by Some Penguin on 2010-10-06
> **Dwood15 said:**
> I checked that out in my perl to see if that worked, and it still only returned the number of values in the first row!

If you try to print a list using "print @listvariable", you're again risking automatic conversion.

This --
```

#!/usr/bin/perl -w
use strict;
my @matrix = ( +[ 1, 2, 3 ], +[ 4, 5, 6], +[ 7, 8, 9] );
my @row0aslist = @{$matrix[0]};

print join("\t", @row0aslist), "\n";
exit 0;

```
works for me, printing 1 2 3 (tab-sep).


> At that point, however you could set @row0aslist = @matrix[0] couldn't you?

I prefer to frequently err on the side of extra braces, just so I (or any other reader) doesn't have to pause even momentarily to remember the order of precedence, and to make it clear what's intended.   Seems safer in a non-strongly-typed language with a lot of automatic conversion going on.


> 
Also, since you seem to be knowledgeable i'm running a personal project to traverse the arrays using a DFS... (basically, following the 0's from 0,0 to the right side)

I saw that there was a module for that here: [http://search.cpan.org/~friedo/Data-Traverse-0.03/lib/Data/Traverse.pm](http://search.cpan.org/~friedo/Data-Traverse-0.03/lib/Data/Traverse.pm)

Think that would be useful for what i'm going for? (obviously because of my newness I don't entirely understand what's going on there...)

*shrug*  Probably overkill -- that would seem more useful for something with deeper structure like a trie or other tree-like structure.  To iterate over a matrix as you're setting them up, e.g.

```

# could be 'cols', Perl doesn't care, just make sure your 
# matrix operation code interprets it consistently...
my @rows = ( +[ 1, 2, 3], +[ 4, 5, 6], +[ 7, 8, 9] );
my $number_of_rows = scalar(@rows);
foreach my $row_lref (@rows) {
  # could print out a row
  print join("\t", @$row_lref), "\n";    

  # or iterate over each column in the row
  for my $datum (@$row_lref) {   
     # do whatever
  }
}

```


Incidentally, depending on what you intend to actually do with the matrixes, PDL might be useful.  If you're not doing anything fancy, PDL is probably overkill, but if having a matrix library is only a means to an end and not your actual objective, it's quite possibly useful.
[http://pdl.perl.org/]("http://pdl.perl.org/")
[http://pdl.perl.org/?docs=MatrixOps&title=PDL::MatrixOps]("http://pdl.perl.org/?docs=MatrixOps&title=PDL::MatrixOps")

---

### Post by shawnhcorey on 2010-10-06
Try:

```

my $length_of_array = @matrix;
print "Number of rows $length_of_array \n";

for my $i (0..$#matrix) {
            my $length = @{ $matrix[$i] };
            print "$length\n";
            }

```


> **Dwood15 said:**
> At that point, however you could set @row0aslist = @matrix[0] couldn't you?

No, that's a slice; see `perldoc perldata` and search for /Slices/.

I think you want:
```
@row0aslist = @{ $matrix[0] }
```

---

### Post by Dwood15 on 2010-10-07
All right, I'll take a look at that, and PDL is overkill lol. I'm just trying to do a simple Pathfinding algo and will whip it up later tonight. 

On another note, I have a file that I know the layouts of (in C/CPP), and want to use those in perl... does anyone have any suggestions to go along with that?

I know I can use C in perl since perl is written in C but if possible i'd like to avoid that. Oh and I know the layout as in I know their struct formats.

---

