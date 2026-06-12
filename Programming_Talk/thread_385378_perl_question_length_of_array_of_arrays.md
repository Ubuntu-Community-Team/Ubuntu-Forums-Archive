---
title: "perl question: length of array of arrays"
date: 2007-03-15
forum: Programming Talk
---

### Post by LotsOfPhil on 2007-03-15
In perl, say you have an MxN array, @array. How do you get the length of each "dimension"?

What I mean is the equivalent of $#array in multiple dimensions.

If I do $#array, I will get the number MxN.

If I do $#{$array[0]} I will get N (the number of columns in row 0).

How do I get the number of rows? What about a 3d array, etc?

Thanks in advance. I am treading water here, so feel free to correct any falsehoods in my post :)

---

### Post by Arby on 2007-03-15
I'm not completely certain but I think you'd have to check the length of each dimension seperately. If you have an array M x N then $#array would just give you M. The following is untested and (this being perl) probably not the only or best way but it should get you going

```

my $length_of_array = @array; #this will give you M

#this should give you the length of each of the N elements in N
for my $i (0..$#array) {
            my $length = $array[$i];
            print "$length\n";
            }

```
You may also want to investigate the scalar() function as a more explicit way to get the length of an array. What you do next depends on what you want to do with those values once you have them. If you explain what your trying to do we'll see what we can come up with.

Hope that helps.
Arby

---

### Post by Mr. C. on 2007-03-15
Arby is correct - you need to evaluate the size of each sub-array.

Multi-dimensional arrays are implemented as an array of references, each reference pointing to either an array, or another reference for further dimensions.  Since refs are scalars, it should be clear that each dimension must be evaluated for array length.

Both scalar @array and $#array produce the same result.

MrC

---

### Post by pmasiar on 2007-03-15
Trick is - array in scalar context returns its length. so value of scalar(@array) is length of an @array. This is how I do remember it - the other way ($#array) is too cryptic for me :-)

---

### Post by Mr. C. on 2007-03-15
As they say in perl "TMTOWTDI".

btw.  the $# syntax comes from the shell.

MrC

---

### Post by LotsOfPhil on 2007-03-16
I don't know the answer to my question yet. (Note: I'm not saying you haven't answered it yet :))

If I have an array that is A x B x C x D x E in dimension, how do I get those values?

If I type scalar(@array[0][0][0][0]) I'll get E. 

What if I want to get D? scalar(@array[0][0][0][][0]) ??

I am only putting zero in there to compress those dimensions/rows/columns.

---

### Post by pmasiar on 2007-03-16
> **LotsOfPhil said:**
> IIf I have an array that is A x B x C x D x E in dimension, how do I get those values?

What if I want to get D? scalar(@array[0][0][0][][0]) ??

Because they are just list of lists, dimensions my have different size for different rows - they are not "meta-cubes"

value of scalar(@array[0][0][0][1]) might be different from scalar(@array[0][0][0][2]). They are just pointers to lists, and they are not aware of each other. IOW programmer needs to make they are equal lengths.

---

### Post by Mr. C. on 2007-03-16
You can access into the multi-dimensional arrays as you are for single, multiple elements, or slices.

There is no reason to make all arrays be of equal length, but the programmer needs to be away of the data structure created.

Your scalar @array ... doesn't get you E - it gives you the length of E.   To access one or more values in E, you'd need $array[0][0][0][0][x];

If you're serious about doing more complicated things in Perl, get the Programming Perl book.  It has a very good section on how to create and use more complicated data structures.

MrC

---

### Post by jeblinux on 2007-11-06
I suggest reading the perl documentation. There is a lot of good introductory information in the tutorials. Start with perllol, then perlreftut, perlref, and perldsc. You need to have the perldoc package installed an then you can type

> $ perldoc perllol

Also, note that there is a perl debugger that can help you understand arrays and arrays of arrays. Just use the -d option when you run you script like this

> $ perl -d myscript.pl

See perldebtut and perldebug for more information on the perl debugger.

**OK. Now for the straight answer.** Multidimensional arrays in perl are actually arrays of references to arrays. This is because arrays can only contain scalars and an array is not a scalar. To get the length of an inner dimension you can use this notation

```
$#{$myarray[0]}
```

where @myarray is a two dimensional array. It will return the number of columns in the first row. This is actually the highest index in the array that is pointed to by the first reference element in @myarray.

Here is a complete example. Copy it, study it, change it, and debug it until you understand. As mentioned earlier, because multidimensional arrays are really arrays of references they are not constrained to have consistent depth.

```

#!/usr/bin/perl -w

use strict;

my @array = ( 1, 2, 3, 4 );

# $aoa[i][j][k]
my @aoa = ( [ [ 0,  1,  2] ],
            [ [10, 11], [13, 14, 15] ],
            [ [20], [23, 24], [26, 27, 28] ] );

print "$#array\n"; # prints 3
print "$#aoa\n"; # prints 2

# dereference with curly brace
print "$#{$aoa[0]}\n"; # prints 0
print "$#{$aoa[0][0]}\n"; # prints 2
print "$#{$aoa[1]}\n"; # prints 1
print "$#{$aoa[1][0]}\n"; # prints 1
print "$#{$aoa[1][1]}\n"; # prints 2
print "$#{$aoa[2]}\n"; # prints 2
print "$#{$aoa[2][0]}\n"; # prints 0
print "$#{$aoa[2][1]}\n"; # prints 1
print "$#{$aoa[2][2]}\n"; # prints 2

```

---

### Post by slavik on 2007-11-07
umm, technically $#array returns the last valid (created) index in @array. :)

pmasiar, you perl hacker, you. :D

---

