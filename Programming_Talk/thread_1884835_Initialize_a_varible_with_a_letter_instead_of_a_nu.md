---
title: "Initialize a varible with a letter instead of a number??"
date: 2011-11-22
forum: Programming Talk
---

### Post by ClientAlive on 2011-11-22
Hi,

In C programming language:

I've been wondering about this for a while now and even tried to do it a couple times. I was wondering if there's a way to set the values in an array to letters rather than numbers? I was trying to reduce the amount of code needed to print multiple categories of values. I had the notion that I could store single letters in the feilds of an array and then call those array feilds in my printf statement later. That way I would just have one printf statemnet that does as much work as having a printf statement for each category. It's kind of a mess right now because I'm in the process of trying to improve the code and learn how to do this, but I attached the source file that shows what I was trying to do. The problem I encounter is that gcc thinks letters ". . . = {A, B, C, D, F};" in line 53 are variables that aren't initialized. What I was trying to do is set the values in the array to those letters so I could call on them later in my printf statemnet (line 110). The first thing I though of is it had to do with what data type I'm trying to use to store the letter but I'm not sure.

Changes that were made is lines 113 - 117 were commented out to try this improvement - to try and learn to do something like this. Lines 50, 51, 53 and 108 - 111 were added. Lines 79, 85, 91, 97, and 103 were added.

I also wonder whether the scanf statements in lines 79, 85, 91, 97, and 103 will actually take the value of the counter in the line above. I'm not certain how there would be a connection unless just the fact that the pairs of lines (counter followed by scanf) are withing the same code block.

I'd appreciate the help if anyone is willing to entertain it.

---

### Post by lisati on 2011-11-22
Here's a [hint]("http://en.wikipedia.org/wiki/C_string_handling")

---

### Post by dfeltey on 2011-11-22
Characters in C must be contained in single quotes like 'A'. So a declaration for a single character should look like 

```
char a = 'A';
```

---

### Post by Mr.Pytagoras on 2011-11-22
Hi

You should inicialize the 
```
char letters[5] = {A, B, C, D, F};
```

like this:
```
char letters[5] = {'A', 'B', 'C', 'D', 'F'};
```

then gcc won't complaint about A,B,C,D,F that their are variables

---

### Post by ClientAlive on 2011-11-22
> **lisati said:**
> Here's a [hint]("http://en.wikipedia.org/wiki/C_string_handling")

Oh yeah, I remember seing that page before. I think it was you or someone pointed it out to me before. I wasn't at the point I am now in our class and it was a little beyond me then. Now this would be a great time for something like that. Thx again lisati.


dfeltey

Mr.Pytagoras

I remember something like that with switch statments but I didn't think of carying it over. I'll have to try that.

If I can get the whole letters instead of numbers thing to work there's a few cool things I've been wanting to do with it.

Thx guys.

:D

---

### Post by ClientAlive on 2011-11-22
Wow, that's the greatest! I can't believe that worked! lol.

```

./Test-Scores.bin
You will be prompted to enter 10 test scores. Please enter an appropriate score when prompted.

Please enter scrore 1: 66
Please enter scrore 2: 55
Please enter scrore 3: 77
Please enter scrore 4: 88
Please enter scrore 5: 88
Please enter scrore 6: 99
Please enter scrore 7: 77
Please enter scrore 8: 99
Please enter scrore 9: 88
Please enter scrore 10: 66

You entered the following test scores:

66
55
77
88
88
99
77
99
88
66

You scored 2 A's
You scored 3 B's
You scored 2 C's
You scored 2 D's
You scored 1 F's

```

Now to pare down that bloated middle part that filters everything into the categories then see how much I can move into functions. This is so cool. Thanks guys.

:D

---

### Post by Vaphell on 2011-11-22
your conditions can be simplified
100 > score >= 90
90 > score >= 80
80 > score >= 70
you have it in descending order so you don't have to check the upper bound. It can't be triggered because the condition above has it covered already. In other words you are golden with
score >= 90
score >= 80
score >= 70 ...

you can also use some arithmetic to sort automatically without huge case/if-else if blocks

```
#include <stdio.h>
#include <stdlib.h>

int main()
{
  int score[10]; 
  int count_grades[5] = {0}; //initialize with 0s
  char grades[] = "FDCBA"; // grade names, int -> grades[int]
  int i;

  srand((unsigned)time(NULL));  
  
// random sample of scores
  for( i=0; i<10; i++ )
    score[i]=rand()%101; //score[] in 0-100 range

// sorting  
  for( i=0; i<10; i++ )
  {
    printf( "#%d %d\n", i+1, score[i] );
    count_grades[**score[i]<50?0:(score[i]==100?4:(score[i]/10-5))**]++;
  }

// result  
  for( i=4; i>=0; i-- )
    printf( "grade %c: %d\n", grades[i], count_grades[i] );
  
  return 0;
}
```
output example
```
$ ./a.out 
#1 81
#2 11
#3 3
#4 51
#5 16
#6 78
#7 9
#8 80
#9 32
#10 0
grade A: 0
grade B: 2
grade C: 1
grade D: 0
grade F: 7

```

edit: i forgot about 100, it would make the formula fail

---

### Post by Bachstelze on 2011-11-22
Quick warning for everyone:

```
  int count_grades[5] = {0}; //initialize with 0s
```

This is correct but uses a quite obscure feature of the standard. In particular, be careful because

```
  int count_grades[5] = {2};
```

would initialize the first element to 2 and the rest with 0s, not all 2s.

---

### Post by ClientAlive on 2011-11-23
> **Vaphell said:**
> your conditions can be simplified
100 > score >= 90
90 > score >= 80
80 > score >= 70
you have it in descending order so you don't have to check the upper bound. It can't be triggered because the condition above has it covered already. In other words you are golden with
score >= 90
score >= 80
score >= 70 ...

you can also use some arithmetic to sort automatically without huge case/if-else if blocks

```
#include <stdio.h>
#include <stdlib.h>

int main()
{
  int score[10]; 
  int count_grades[5] = {0}; //initialize with 0s
  char grades[] = "FDCBA"; // grade names, int -> grades[int]
  int i;

  srand((unsigned)time(NULL));  
  
// random sample of scores
  for( i=0; i<10; i++ )
    score[i]=rand()%101; //score[] in 0-100 range

// sorting  
  for( i=0; i<10; i++ )
  {
    printf( "#%d %d\n", i+1, score[i] );
    count_grades[**score[i]<50?0:(score[i]==100?4:(score[i]/10-5))**]++;
  }

// result  
  for( i=4; i>=0; i-- )
    printf( "grade %c: %d\n", grades[i], count_grades[i] );
  
  return 0;
}
```
output example
```
$ ./a.out 
#1 81
#2 11
#3 3
#4 51
#5 16
#6 78
#7 9
#8 80
#9 32
#10 0
grade A: 0
grade B: 2
grade C: 1
grade D: 0
grade F: 7

```

edit: i forgot about 100, it would make the formula fail

Wow, that is a lot less code. I'm having some difficulty reading what's going on though. I recognize some of the things, but some of it I have never laid eyes on before. :)

For instance:

```

count_grades[**score[i]<50?0:(score[i]==100?4:(score[i]/10-5))**]++;

```

The way that's (nested?) is new. And the way  . . . errr, well I can see at least a couple things that look new to me. The ++ being at the end. I'm guessing what's going on there is

```

count_grades[/*stuff inside*/]++

```

is being incremented by one. But how that effects the stuff inside, the relation of the parts to the whole - well . . .

And the colon ":" being used in the code that's inside "count_grades[]" in that line. It reminds me of something I just read in our book last night. I don't see that they gave it a name though. The example in our book is:

> 
```

grade >= 60 ? printf( "Passed\n" ) : printf( "Failed\n" ):

 . . . is comparable to the preceeding if...else statement.

```


I haven't had a chance to try that way of doing things yet though.

And this notion of:

```

[b]score . . .

```

with the "[b]" preceeding the array in brackets like that.

It might have come up somewhere along the line, thought this class has only taught us the simpler segments of the subjects we've addressed.

Thanks for turning me on to some new stuff Vaphell. Gives me stuff to play with outside of assignments.

:D


> **Bachstelze said:**
> Quick warning for everyone:

```
  int count_grades[5] = {0}; //initialize with 0s
```

This is correct but uses a quite obscure feature of the standard. In particular, be careful because

```
  int count_grades[5] = {2};
```

would initialize the first element to 2 and the rest with 0s, not all 2s.

I know this isn't what you were talking about when you wrote that but when I saw it the thing that popped into my mind was the question whether there's something in C that's like wild cards in bash. I'm guessing you can't mix things like what I did below; but, for the sake of communication, something like: 

```

int count_grades[5] = {2*}

```

where you could state for all the elements to initialize to the same value by including some symbol rather than writing everything out.

```

int count_grades[5] = {2, 2, 2, 2, 2}

```

Does C have things like that?
----------------------

---

### Post by Bachstelze on 2011-11-23
All this leads us to a very important thing. In C, every expression has a value and possibly side-effects. To put it simply, the value of an expression is what it *is*, and its side-effects are what it *does*.

An expession of the form [font=monospace](a) ? b : c[/font] has the value of [font=monospace]b[/font] if [font=monospace]a[/font] evaluates to non-zero, and the value of [font=monospace]c[/font] otherwise.

For example if I write

```
int a, b;
b = 1;
a = (b) ? 2 : 3;
```

a will get value 2, because b has a non-zero value. And as you can see, expressions can be nested to arbitrary depths. I could write

```
a = ((b) ? 0 : 1) ? 2 : 3;
```

The value of a will be 3, because since b is 1, expression ((b) ? 1 : 0) has value 0, and thus the value after the colon is taken in the second expression.

The difference between [font=monospace]a++[/font] and [font=monospace]++a[/font] also comes from this. We know what an expression like [font=monospace]a++[/font] does : it increments a by one. That's its side-effect. But since every expression also has a value, what is the value of the expression [font=monospace]a++[/font] ? That is, what do you get when you do

```
int a = 1;
int b = (a++);
printf("%d\n", b);
```

The value of the expression [font=monospace]a++[/font] is the value of a, so this code would print 1. This code however

```
int a = 1;
int b = (++a);
printf("%d\n", b);
```

will print 2, because the value of expression [font=monospace]++a[/font] is a+1. Those two operators are called post-incrementation and pre-incrementation, respectively. Intuitively, it means the incrementation is performed respectively after and before the value is "extracted". Note that if, as is often the case, you don't consider the value of the expression itself (as opposed to the value of the variable it acts on), both are equivalent:

```
int a = 1;
a++;
printf("%d\n", a);
```

and

```
int a = 1;
++a;
printf("%d\n", a);
```

will both print 2.

> **ClientAlive said:**
> 
I know this isn't what you were talking about when you wrote that but when I saw it the thing that popped into my mind was the question whether there's something in C that's like wild cards in bash. I'm guessing you can't mix things like what I did below; but, for the sake of trying to communicate, something like: 

```

int count_grades[5] = {2*}

```

where you could state for all the elements to initialize to the same value by including some symbol rather than writing everything out.

```

int count_grades[5] = {2, 2, 2, 2, 2}

```

Does C have things like that?
----------------------

No, the "shortcut" of specifying only one value only works if you want to initialize with 0s. Basically, when you give fewer elements than the size of the array, the rest is filled with 0s (for arithmetic types, null pointers for pointer types). If you want to fill an arbitrary length array with a fixed value, use a for loop:

```
int T[N];
for (int i=0; i<N; i++) {
    T[i] = 5;
}
```

If you want to fill a byte-array, you can (and probably should) also use memset() but there's nothing similar for integers.

---

### Post by Vaphell on 2011-11-23
i merely did 2 things at once. That mysterious line is an equivalent to
```

int tmp;
tmp = ( score[i]<50?0:(score[i]==100?4:(score[i]/10-5)) );
count grades[tmp]++;

```
condition?value_if_true:value_if_false (true being any non-zero)
 i stacked 2 of them so the logic is as follows:
if score<50 then 0 else ( if score==100 then 4 else (score/10-5) )
50-99 return 5-9 when divided by 10, but we want to move the result to 0-4 range (our array is indexed with 0-4), thus -5
0-49 would return 0-4, -5 moves it into negative territory and we want to group them under 0
100 would return 10, with -5 it's 5 but we want to store it under 4.

++ increments the element of count_grades[] that is indexed with the number that comes from the hardcore part inside. In other words calculate index, take the array element and add 1 to it.


[b] is forum code for 'bold' - i used it on the part inside the brackets but it shouldn't be there in the code itself :)

array init requires writing some/all values explicitly, this one was a special case. All elems not listed are initialized with 0, so setting the first elem to 0 is enough to have all 0s. But other values require typing or running in a loop
```
for( i=0; i<ARRAY_SIZE; i++)
  array*=[I]some_value*;
```


bachstelze did explain the ?: but his examples have wrong results, as if he treated 1 as 0 :-) too much bash?
```
printf( "%d\n", 1?2:3 );
printf( "%d\n", (1?1:0)?2:3 );
printf( "%d\n", 0?2:3 );
printf( "%d\n", (0?1:0)?2:3 );
-------------------------
2
2
3
3
  
```

---

### Post by Bachstelze on 2011-11-23
> **Vaphell said:**
> 
bachstelze did explain the ?: but his examples have wrong results, as if he treated 1 as 0 :-) too much bash?
```
printf( "%d\n", 1?2:3 );
printf( "%d\n", (1?1:0)?2:3 );
printf( "%d\n", 0?2:3 );
printf( "%d\n", (0?1:0)?2:3 );
-------------------------
2
2
3
3
  
```

No, I basically never code shell scripts, my brain just had a bug. ;) Thanks, I corrected.

@ClientAlive: Make sure you understand the whole "value and side-effects" thing because it's very important. A lot of beginners in C are confused when they see things like

```
int n = scanf("%d %d %d", &a, &b, &c);
```

or

```
int n = t[i++];
```

Because in their mind, scanf only reads values and ++ only increments a variable, and they don't have values in and of themselves. When you see something like that, be sure to ask yourself what exactly the value of the expression is (if it is a function, look at the "return value" section of its manual page; if it is an operator, ask here or look it up in a book or the standard document).

---

### Post by ClientAlive on 2011-11-23
> **Vaphell said:**
> i merely did 2 things at once. That mysterious line is an equivalent to
```

int tmp;
tmp = ( score[i]<50?0:(score[i]==100?4:(score[i]/10-5)) );
count grades[tmp]++;

```
condition?value_if_true:value_if_false (true being any non-zero)
 i stacked 2 of them so the logic is as follows:
if score<50 then 0 else ( if score==100 then 4 else (score/10-5) )
50-99 return 5-9 when divided by 10, but we want to move the result to 0-4 range (our array is indexed with 0-4), thus -5
0-49 would return 0-4, -5 moves it into negative territory and we want to group them under 0
100 would return 10, with -5 it's 5 but we want to store it under 4.

++ increments the element of count_grades[] that is indexed with the number that comes from the hardcore part inside. In other words calculate index, take the array element and add 1 to it.


[b] is forum code for 'bold' - i used it on the part inside the brackets but it shouldn't be there in the code itself :)

array init requires writing some/all values explicitly, this one was a special case. All elems not listed are initialized with 0, so setting the first elem to 0 is enough to have all 0s. But other values require typing or running in a loop
```
for( i=0; i<ARRAY_SIZE; i++)
  array*=[I]some_value*;
```


bachstelze did explain the ?: but his examples have wrong results, as if he treated 1 as 0 :-) too much bash?
```
printf( "%d\n", 1?2:3 );
printf( "%d\n", (1?1:0)?2:3 );
printf( "%d\n", 0?2:3 );
printf( "%d\n", (0?1:0)?2:3 );
-------------------------
2
2
3
3
  
```


The more I see and experience this stuff the more obvious it becomes that there's a real heavy importance on a good understanding 0f logic and how to use it in programming. It's not just knowing some key words and slapping stuff together - there's real, **hard-core** logic behind what you do when you write a program.

> 
i stacked 2 of them so the logic is as follows:
**if** score<50 then 0 **else** ( **if** score==100 then 4 **else** (score/10-5) )


So it looks like you can incorporate multiple selection with ternary code. It's in the way you use the parenthesis? I was experimenting with that last night but I don't think I had the syntax right. I'll have to try that again.

I was trying to use letters instead of numbers as conditions for selection statements too (in a different, small program) but ran into a little trouble with that. I'm not sure if the problem didn't lie in some other part of my code though, since it was working before but a different part wasn't - fixed the 'different part' and using letters for my conditions stopped working. [sigh].

I was trying to pull off something like:

```

if(input == "p")
   {
   //code to execute
   }

else if(input == 'f')
   {
   //code to execute
   }

else
   {
   printf("Please enter an appropriate value\n");
   }

```

Well, when I used the single quotes to initialize a varible to a letter (like dfeltey  and Mr.Pytagoras reminded me) there was no problem. And doing this w/ letter values did seem to work at first, then I changed something and it didn't but the other part that wasn't right did. Strange.

Just seems more intuitive for a user to enter a letter choice in some cases than a number choice. You know?

Ah well, I still have a lot to learn about this stuff guys.  :P

---

### Post by Vaphell on 2011-11-23
CA, cool excercise for you, that will exploit the concept of values and side effects B. talked about
what will the following code print out? :-)

```
int x=0, y=0, z=0;
x++ && ++y && ++z;
--x && ++y && ++z;
x++ || y++ && z++;
x++ && y++ || z++;
x++ || y++ || z++;
printf( "x=%d y=%d z=%d\n", x, y, z );
```

> It's not just knowing some key words and slapping stuff together - there's real, hard-core logic behind what you do when you write a program.

slapping stuff together will lead you nowhere. Good programmers don't leave anything to coincidence and a good grasp of logic helps to plan the structure and the flow of your program. Also the attention to detail is crucial because it allows to predict and cover all these corner cases that will make your algorithm blow up.

---

### Post by Bachstelze on 2011-11-23
> **ClientAlive said:**
> 
Well, when I used the single quotes to initialize a varible to a letter (like dfeltey  and Mr.Pytagoras reminded me) there was no problem. And doing this w/ letter values did seem to work at first, then I changed something and it didn't but the other part that wasn't right did. Strange.

There is no such thing as "letter values". Constants enclosed in single quotes are *character constants*, and believe it or not, they are of type int! When you use character constants, the value stored internally is always an integer, which corresponds to the ASCII code of the character in question. For example, those four notations are equivalent:

```
char c = 'a'; /* Character constant */
char c = 97; /* Decimal */
char c = 0141; /* Octal */
char c = 0x61; /* Hexadecimal */
```

---

### Post by ClientAlive on 2011-11-23
> **Bachstelze said:**
> No, I basically never code shell scripts, my brain just had a bug. ;) Thanks, I corrected.

@ClientAlive: Make sure you understand the whole "value and side-effects" thing because it's very important. A lot of beginners in C are confused when they see things like

```
int n = scanf("%d %d %d", &a, &b, &c);
```

or

```
int n = t[i++];
```

Because in their mind, scanf only reads values and ++ only increments a variable, and they don't have values in and of themselves. When you see something like that, be sure to ask yourself what exactly the value of the expression is (if it is a function, look at the "return value" section of its manual page; if it is an operator, ask here or look it up in a book or the standard document).


Well you sure have me thinking. After staring at that first code sample I though, "well that's a way to assign the value of n to multiple, other variables." I tried that code sample to see if that's what it would do but the program hangs either before or after requesting the value of n. I run into a lot of dumb little things I do wrong though so I'm sure I had the lines out of order or something.

```

#include <stdio.h>

int main (void)

{
int a, b, c;
**int n = scanf("%d %d %d", &a, &b, &c);**

printf("Enter a value for n: \n");
scanf("%d", &n);

printf("The value of a is %d\n", a);
printf("The value of b is %d\n", b);
printf("The value of c is %d\n", c);

return 0;
}

```

Your second code example, I'm wondering if that isn't a way you can have the user define variables w/in the program. I'm just guessing here though.

You mentioned a bigger issue though - one of understanding how the value of an expression effects things. I'm not sure I've experienced that much excecpt for an example someone told me last week. They said, given -

b = 3
a = b

that b would end being equal to a. Which just illustrated how the value of the variable changes I guess. I gather you're talking about something much deeper than that thouhg.

:)

---

### Post by Bachstelze on 2011-11-23
> **ClientAlive said:**
> Well you sure have me thinking. After staring at that first code sample I though, "well that's a way to assign the value of n to multiple, other variables." I tried that code sample to see if that's what it would do but the program hangs either before or after requesting the value of n. I run into a lot of dumb little things I do wrong though so I'm sure I had the lines out of order or something.

No. ;) If you have

```
scanf("%d %d %d", &a, &b, &c);
```

and

```
n = scanf("%d %d %d", &a, &b, &c);
```

the *side-effects* of scanf() (i.e. what it does) will be the same thing: it will wait for you to enter three integers, and store them in a, b and c. The difference is that in the second case, it will also store something in the variable n. That something is the *value* of the expression, which is the value returned by scanf, in exactly the same way that

```
n = abs(-2);
```

will store in n the return value of function abs(), which is the absolute value of its parameter (here it will be 2). In order to know what the return value of scanf() is, you check its manual page (it is *not* related to the values of the integers you enter!).

*EDIT: I might have come up as harsh last time, but this is really important. DO NOT try to guess what things do. Often it's not obvious, and you will waste valuable time for nothing because the information is readily available.*

```
n = t[i++];
```

is equivalent to

```
n = t[i];
i++;
```

since expression (i++) has value i and increments i after the value is obtained, or

```
n = t[i];
++i;
```

which are the same because i++ and ++i by themselves are equivalent, but NOT

```
n = t[++i];
```

that one is equivalent to either

```
i++;
n = t[i];
```

or

```
++i;
n = t[i];
```

---

### Post by Vaphell on 2011-11-23
> "well that's a way to assign the value of n to multiple, other variables." I tried that code sample to see if that's what it would do but the program hangs either before or after requesting the value of n.

well duh, scanf waits for input :D
also forget about such crazy ideas like n propagated to other variables in that form ;-)
**something = something_else;** always assigns the value of right side expression to the left side variable, left side going to right side is not going to happen

int n = scanf(...); is simple - scanf is a function that happens to return integer
[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)
> On success, the function returns the number of items successfully read. This count can match the expected number of readings or fewer, even zero, if a matching failure happens. That integer is the value that n gets. Side effect of scanf is putting values into the variables listed as parameters and that side effect is why scanf is used, but it does have value you may use if you want.

you can even do something like this
```
scanf("%d %d %d", &a, &b, &c) ? printf( "more than one value\n" ) : printf( "0 values\n" );
```
on a side note - printf also has a value. Pretty much all functions have, even those not dealing with numbers, because their result is often used to signal success or error (value being the error code/exit status)

as for pre- and postincrementation check that excercise from post #14 :)

---

### Post by Bachstelze on 2011-11-23
> **Vaphell said:**
> 
also forget about such crazy ideas like n propagated to other variables in that form ;-)
**something = something_else;** always assigns the value of right side expression to the left side variable, left side going to right side is not going to happen

I couldn't have said it better. :)

---

### Post by ClientAlive on 2011-11-24
I know what you mean about wasting time. I seem to spend a lot of time trying to figure things out. Overly arrogant and pridefull sometimes too. I know that if I listen better and am humble I'll learn more. Sometimes it's just that knee jerk reaction though.

Thanks for taking the time to show me good things Bachstelze and Vaphell. It didn't occur to me that there might be man pages for these things. Now that's valuable to know about. Sometimes I feel like I struggle so hard to learn, what seems to me, ought to be very very simple and easy to grasp. Sometimes I question myself whether I have the aptitude to do programming. The problems is I like it so much. A lot of things I've been challenged by in the past I just let go of (guess those one's didn't matter as much). This, I find myself up all hours of the night messing with and I feel such a sense of accomplishment when I do get it.

Anyhoo . . . enough of that.

Bachstelze, I couldn't help myself. Based on your last post I modified that code and ran it to see what came up. It wasn't what I expected but does seem to indcate what you were saying (if the code I used was correct in the first place). It doesn't matter what values I enter I get the same result. Again, if the code I used was ok to begin with, a result like that tells me that scanf itself has a definite value associated with it.

```

/*Test piece of code given on ubunto forums by Bachstelze  Post# 12 @ Link:
http://ubuntuforums.org/showthread.php?p=11484487&posted=1#post11484487*/

#include <stdio.h>

int main (void)

{
int a, b, c;
int n = scanf("%d %d %d", &a, &b, &c);

printf("The value of n is %d\n", n);

return 0;
}


[CODE]
 ./Test-Scanf.bin12 24 36
The value of n is 3
shine@BashBox ~/ProgrammingPlayground/Miscellaneous > ./Test-Scanf.bin
10 20 30
The value of n is 3
shine@BashBox ~/ProgrammingPlayground/Miscellaneous > ./Test-Scanf.bin
5 10 15
The value of n is 3

```
[/CODE]


Vaphell, that was very inforamtive to hear about which side of the equal sign is assigned to which. It probably mentioned it in our book. What happened is I'd asked our instructor before the semester started and was told we would only use the book as a reference, that there was no reading in it to do. I'm such an idiot! I took that to heart and screwed myself. I let it get to a month away from the end of the semester before I started studying on that book's content. When I did I realy saw what I'd been missing. Shoulda never listened to that to begin with.
---------------------------

Edit:

Yeah

```

int n = scanf("...", ...);

```

just yeilds the nuber of variable used in it as output. If I vary the nuber of variables in the statement the output always corresponds to the number of vaiables in the statment regardless of what input is placed in them.

---

### Post by Vaphell on 2011-11-24
> It didn't occur to me that there might be man pages for these things. Now that's valuable to know about.

C is standarized. When there is a standard, there are certain things set in stone and described in documentation :) Google a bit and you will find plenty of info about what is inside the standard library.

> Sometimes I feel like I struggle so hard to learn, what seems to me, ought to be very very simple and easy to grasp. Sometimes I question myself whether I have the aptitude to do programming. The problems is I like it so much. A lot of things I've been challenged by in the past I just let go of (guess those one's didn't matter as much). This, I find myself up all hours of the night messing with and I feel such a sense of accomplishment when I do get it.

don't worry, you need to train your brain to think in a certain way and it takes time. Also you need to get familiar with the tools available. The fact that C is one of the more hardcore in the category of mainstream programming languages is not without meaning either. It's close to the metal, it's powerful but gives you plenty of rope to hang yourself with. Everything needs to be micromanaged and taken care of by the programmer.
Other languages (like python often recommended to newcomers) offer huge libraries of tools that allow to achieve similar effect in 1 or 2 lines of code.
I think that fun and sense of accomplishment are crucial on the road to programming mastery, if you feel that way you are golden :)

now back to business :-)

> ```
int n = scanf("...", ...);
```
just yeilds the nuber of variable used in it as output. If I vary the nuber of variables in the statement the output always corresponds to the number of vaiables in the statment regardless of what input is placed in them.

close,  but no cigar :)

```
int a, b, c, n;
n = scanf( "%d %d %d", &a, &b, &c );
printf( "n=%d\n", n );
-----------------------------------------
$ ./a.out 
1 a 2
n=1
$ ./a.out 
a 1 2
n=0
$ ./a.out 
1 2 c
n=2

```

'successful' is the key here, always have in mind that the user input may not be as pretty as you'd like it to be ;-)

---

### Post by ClientAlive on 2011-11-25
> **Vaphell said:**
> C is standarized. When there is a standard, there are certain things set in stone and described in documentation :) Google a bit and you will find plenty of info about what is inside the standard library.



don't worry, you need to train your brain to think in a certain way and it takes time. Also you need to get familiar with the tools available. The fact that C is one of the more hardcore in the category of mainstream programming languages is not without meaning either. It's close to the metal, it's powerful but gives you plenty of rope to hang yourself with. Everything needs to be micromanaged and taken care of by the programmer.
Other languages (like python often recommended to newcomers) offer huge libraries of tools that allow to achieve similar effect in 1 or 2 lines of code.
I think that fun and sense of accomplishment are crucial on the road to programming mastery, if you feel that way you are golden :)

now back to business :-)



close,  but no cigar :)

```
int a, b, c, n;
n = scanf( "%d %d %d", &a, &b, &c );
printf( "n=%d\n", n );
-----------------------------------------
$ ./a.out 
1 a 2
n=1
$ ./a.out 
a 1 2
n=0
$ ./a.out 
1 2 c
n=2

```

'successful' is the key here, always have in mind that the user input may not be as pretty as you'd like it to be ;-)


Is there a way to see what these, well... they're functions right? Is there a way to see behind the curtain and see the code the functions are made of? It makes me wonder what the language is really made of, what any programming language is made of. To see under the hood as it were. Do we have access to see that?

---

### Post by Bachstelze on 2011-11-25
> **ClientAlive said:**
> Is there a way to see what these, well... they're functions right? Is there a way to see behind the curtain and see the code the functions are made of? It makes me wonder what the language is really made of, what any programming language is made of. To see under the hood as it were. Do we have access to see that?

Of course

```
apt-get source libc6
```

IMO it's not really interesting, but have fun. :p

---

### Post by ClientAlive on 2011-11-26
> **Bachstelze said:**
> Of course

```
apt-get source libc6
```

IMO it's not really interesting, but have fun. :p


I tried to find a download that's something like a text document, something you can just read the code. I did find the Ubuntu libc6 deb package but I haven't had the chance to look at it much - not sure if it's what I was hoping.

Anyway though...

I was on #programming last night asking ppl about functions in C. That's what were currently on in class right now and it's been hell. Well, it had been until last night. I was having trouble understanding something much more fundamental to C and didn't know what it was or even how to describe my problem very well. Someone there must have picked up on something because they told me to look at something called scope. OmG!!! Thank goodness for scope!! Wowww! When I saw what scope is and how it works in C I realized exacly where I'd made my mistake. All this time I've been using the variable names to imagine these connections between different parts of the program. That's what it was too - a figment of my imagination. It worked for a little while (a few weeks in the beginning of the class maybe) but very quickly broke down after that and I couldn't understand why nothing was working. Scope, as I understood it, is defined by the brackets and has more to do with the location of variables than the names. This is HUGE guys! After reading about that I had working functions all over the place.  :popcorn:

Now I'm on wikipedia looking at all kind of conceptual stuff to do w/ programming and it's amazing. I had no idea just how deep this stuff is. Stacks, namespace, closure and information hiding; lock and semaphore; name resolution and binding; subroutines! HOO HOO!


:D

---

