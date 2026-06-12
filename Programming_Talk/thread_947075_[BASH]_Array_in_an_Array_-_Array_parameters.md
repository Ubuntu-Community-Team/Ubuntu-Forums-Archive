---
title: "[BASH] Array in an Array - Array parameters"
date: 2008-10-13
forum: Programming Talk
---

### Post by Anathema0 on 2008-10-13
Hello,

First off, I have been searching for an answer for the past 3 days, and I have come to the conclusion, for the most part: Impossible

Is there a way in bash to have an element of an array be a reference of anther array.

In perl, it would look like
@L2 = ("B", 1, 5);
@R1 = ("B", 1, 20);

@L3 = ("B", 1, 3);
@R3 = ("B", 1, 2);

@R2 = ("S", 1, 4, 6, \@L3, \@R3);
@L1 = ("S", 1, 5, 5, \@L2, \@R2);

@base1 = ("S", 2, 20, 10, \@L1, \@R1);

And I'm sure it is pretty obvious what I want to do... 

A similar question.  Is it possible for an array to be passed as a parameter?

I am very new to bash, but I have programmed in about six other languages, and I've never had this problem.

Thank you very much
~Anathema

---

### Post by ghostdog74 on 2008-10-14
what is the actual problem you are going to solve?

---

### Post by Anathema0 on 2008-10-14
The programming problem is for mobiles.
     
   ```
 
                              |
                              |
          --------------------+----------
          |                             |
    ------+------                      20
    |           |
    5       ----+------
            |         |
            3         2

A strut is 

        |
   -----------
   X         X 

A ball is

    | 
    5

```
That is an example of one.  

Have to check if it's balanced, the total height and the total weight.  
I declare my own way of representing the mobile, and the way I chose was an array

if it's a strut:

array=( "S" [height] [left length] [right length] [left array] [right array] )

if it's a ball:

array=( "B" [height] [weight] )

To find the total weight, I add up all the weights from each of the balls in the mobile.  To find the length, I add up all the possible heights, a value for each ball.  Put them in a list or something similar, find the largest value, and that is the maximum height.

If it's balanced, I check if the left length * left array = right length * right array.  If at any point in the mobile that is not true, it is not balanced.

It is an extremely easy problem (I think), but the way I have done it looks quite difficult to do in BASH.  

I hope that explains more.

I have solved this problem in two different langauges (PERL and Scheme).  And I am pretty sure I am going to have to find a different way of representing the strut and ball besides and array.  I just wanted to make sure I can rule out referencing an array as an element of another array before I decided to do that.

~Anathema> [QUOTE][/QUOTE]

---

### Post by ghostdog74 on 2008-10-14
so you have to definitely do it in bash/shell? you can give Awk a try. It has associative arrays which you can simulate your "array in arrays".

---

### Post by geirha on 2008-10-14
> **Anathema0 said:**
> 
In perl, it would look like
@L2 = ("B", 1, 5);
@R1 = ("B", 1, 20);

@L3 = ("B", 1, 3);
@R3 = ("B", 1, 2);

@R2 = ("S", 1, 4, 6, \@L3, \@R3);
@L1 = ("S", 1, 5, 5, \@L2, \@R2);

@base1 = ("S", 2, 20, 10, \@L1, \@R1);

And I'm sure it is pretty obvious what I want to do... 

A similar question.  Is it possible for an array to be passed as a parameter?


There's no pretty way that I know of to do this in bash. There's an ugly way though, by using eval. Your above code could look something like this:
```

L2=( B 1 5 )
R1=( B 1 20 )

L3=( B 1 3 )
R3=( B 1 2 )

R2=( S 1 4 6 L3 R3 )
L1=( S 1 5 5 L2 R2 )

base1=( S 2 20 10 L1 R2 )

eval echo \$\{${base1[4]}\[@\]\}   # Will list L1 ...
eval echo \$\{${base1[5]}\[@\]\}   # Will list R2 ...

```
Did I mention ugly? :)

---

### Post by Anathema0 on 2008-10-14
Thank you very much.  That does work, but my god... that is just painful on the eyes.

Now, due that syntax... and me being fairly new to bash, I am just mind boggled at what is going on..

I learn by example, so if you can help me with a few more things, then I'll be fine.

I see that you can easily access the array L1 with 
Temp=${main1[4]}
Now, lets say with that Temp variable, I want to access the first element and store it in another variable..  how would I do that...

Thank you again.

---

### Post by Anathema0 on 2008-10-14
Temp=${base1[4]}
echo $Temp
eval echo \$\{$Temp\[2\]\} 


I believe I understand how it works.

L1
5
is the output of that

But.. is there any way I can store that value into a variable? 

Back to basically my previous post.



Please excuse my multi post

Also, I figured out the problem.  I just did a very small search on eval and I figured it out

eval temp2=\$\{$Temp\[2\]\} 

Thank you so much for your help.

~Anathema

---

### Post by geirha on 2008-10-14
> **Anathema0 said:**
> 
eval temp2=\$\{$Temp\[2\]\} 


BTW, instead of the backslashes, you can use single-quotes (also known as hard quotes) which inhibit variable expansion. 
```
eval temp2='${'$Temp'[2]}'
```
Slightly more pleasing to the eyes perhaps. :)

---

