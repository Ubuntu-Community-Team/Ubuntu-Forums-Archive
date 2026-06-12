---
title: "Beginner's Challenge 1"
date: 2011-07-13
forum: Programming Talk
---

### Post by Randy Flagg on 2011-07-13
I know this thread is closed but I am beginning to love doing these challenges while I learn python.  I am also doing the pythonchallenge (first three done).

I was hoping some of you could critique my first attempt.  Please keep in mind I have been learning python for two weeks (after finally installing ubunut and loving it!).  I haven't coded anything for about 15 years.  Previous experience is with Pascal and C.

Please let me know what you think.

Thanks.

[PHP]
#Ubuntu Forums Beginners Challenge 1
#Code outputs lyrics to 99 bottles of beer on the wall

i = 99            #Total number of bottles and condition for loop
while i != 1:    #It's never going to get to one but this get's the job done
    if i == 2:    #2 is when the basically static text starts
        print "2 bottles of beer on the wall, 2 bottles of beer.\nTake one down and pass it around.  1 bottle of beer on the wall.\n\n1 bottle of beer on the wall.  1 bottle of beer.\nTake one down and pass it around.  No bottles of beer on the wall.\n\nNo more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall."
    else:          #main loop for 99-3
        print "%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottles of beer on the wall.\n" % (i, i, i -1)
    i -= 1
[/PHP]

---

### Post by JupiterV2 on 2011-07-13
The code runs without error, so that's a great start!

I don't have any experience with Python so I can't critique that aspect of your code. However, my first observation is one of personal taste when trying to read long lines. For legibility, it's common to keep line length anywhere between 80 and 120 characters, depending on the width of your screen or personal preference. I don't care much to have to scroll horizontally to read the whole line.

My other observation is your use of so much static code. As a continuation of this exercise try and find a way to reduce your dependence on it. For an extra challenge, also look at trying to change the numbers (99 bottles) to alpha (ninety-nine bottles). There are some creative ways to do this in a language like Python I think.

---

### Post by Randy Flagg on 2011-07-13
Thanks for the comments.  I wanted to get feedback before why I did the programming the way I did.

First off the, column  in my editor had those long lines broken up.  I am not sure why they didn't break up when I cut and pasted.

Second, the use of static code was a deliberate decision.  I understand that I could done more with string replacement but my past experience has lead to believe that you shouldn't "code just for code".  Plus I think the original challenge requirement were not to be a "code monkey".  So, i said I am going to stick with simple is better.

I am working on the other challenges now but turning the numerals into phrase would be a good exercise.

---

### Post by TwoEars on 2011-07-13
> **Randy Flagg said:**
> I know this thread is closed but I am beginning to love doing these challenges while I learn python.  I am also doing the pythonchallenge (first three done).

I was hoping some of you could critique my first attempt.  Please keep in mind I have been learning python for two weeks (after finally installing ubunut and loving it!).  I haven't coded anything for about 15 years.  Previous experience is with Pascal and C.

Please let me know what you think.

Thanks.

[PHP]
#Ubuntu Forums Beginners Challenge 1
#Code outputs lyrics to 99 bottles of beer on the wall

i = 99            #Total number of bottles and condition for loop
while i != 1:    #It's never going to get to one but this get's the job done
    if i == 2:    #2 is when the basically static text starts
        print "2 bottles of beer on the wall, 2 bottles of beer.\nTake one down and pass it around.  1 bottle of beer on the wall.\n\n1 bottle of beer on the wall.  1 bottle of beer.\nTake one down and pass it around.  No bottles of beer on the wall.\n\nNo more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall."
    else:          #main loop for 99-3
        print "%d bottles of beer on the wall, %d bottles of beer.\nTake one down and pass it around, %d bottles of beer on the wall.\n" % (i, i, i -1)
    i -= 1
[/PHP]

Alright, well firstly -

Your lines are too long. Python code is self-documenting when done correctly, so there's no need for massive amounts of comments, especially not in-line. Try splitting up the text you're printing over several lines too. Look into triple-quoting for Python.

```

while i != 1:    #It's never going to get to one but this get's the job done
```
This isn't true ;) If it never got to 1, then the loop would continue forever. You can test this if you'd like, by adding "print i" to the end of the script.

While I'm on it, Python convention here would to not use while, but instead use a for loop, for example ```

for x in xrange(99,1,-1):
    stuff

``` 

```
else:          #main loop for 99-3
```
Again, not true. if..else is not a loop structure, it's a conditional.

---

### Post by Tony Flury on 2011-07-14
For the sake of a few more lines of code - I would have had one loop and had 1 and 0 bottles as special cases within that loop - rather than combine the 2,1 and 0 case into one condition.

I would have also used the parameterised output - using {0} and {1} (rather than %d), this would save you repeating the same parameter multiple times - uneccessary repetition can lead to errors.

The %d is termed in the documentation is refered to "Old style" - I find that the positional formatting to be more flexible.

[http://docs.python.org/tutorial/inputoutput.html#fancier-output-formatting](http://docs.python.org/tutorial/inputoutput.html#fancier-output-formatting)

---

### Post by Randy Flagg on 2011-07-14
I really appreciate the feedback guys.  This is the kind of stuff I am not getting from following howtos and reading books.

Please see the updates code below which reflects your suggestions.  I am not happy with the formatting of the strings in the code but I don't know if there is a convention as to how this should be done.

Also, I am still sticking to having the last three verses as static text.  I am open to comments on this but I don't see how including this data in loops and conditions benefits anything but the beauty of the code.  It is never, ever going to change so why throw those additional pieces of code in there.

[PHP]
#Ubuntu Forums Beginners Challenge 1
#Code outputs lyrics to 99 bottles of beer on the wall
# Version 2

i = 99    
for i in range(99,1,-1):
    if i == 2:    
        print """2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around.  1 bottle of beer on the wall.\n"""

        print """1 bottle of beer on the wall.  1 bottle of beer.
Take one down and pass it around.  No bottles of beer on the wall.\n"""

        print """No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."""

    else:          
        print """{0} bottles of beer on the wall, {1} bottles of beer.
Take one down and pass it around, {2} bottles of beer on the wall.\n""".format(i, i, i -1)

    i -= 1
[/PHP]

---

### Post by Tony Flury on 2011-07-14
Adding the extra conditions arguably makes the code more obvious - you are right that in this case the output wont change - but making the code "obvious" and self documenting are good habits to get into.

Your print line could simplified to : 

```

print """{0} bottles of beer on the wall, {0} bottles of beer.
Take one down and pass it around, {1} bottles of beer on the wall.\n""".format(i, i-1)

```
One less parameter - one less potential error.

and you don't need the 
```

i=-1

```
You already have i in the for loop.

---

### Post by TwoEars on 2011-07-14
> **Randy Flagg said:**
> I really appreciate the feedback guys.  This is the kind of stuff I am not getting from following howtos and reading books.

Please see the updates code below which reflects your suggestions.  I am not happy with the formatting of the strings in the code but I don't know if there is a convention as to how this should be done.

Also, I am still sticking to having the last three verses as static text.  I am open to comments on this but I don't see how including this data in loops and conditions benefits anything but the beauty of the code.  It is never, ever going to change so why throw those additional pieces of code in there.

[PHP]
#Ubuntu Forums Beginners Challenge 1
#Code outputs lyrics to 99 bottles of beer on the wall
# Version 2

i = 99    
for i in range(99,1,-1):
    if i == 2:    
        print """2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around.  1 bottle of beer on the wall.\n"""

        print """1 bottle of beer on the wall.  1 bottle of beer.
Take one down and pass it around.  No bottles of beer on the wall.\n"""

        print """No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."""

    else:          
        print """{0} bottles of beer on the wall, {1} bottles of beer.
Take one down and pass it around, {2} bottles of beer on the wall.\n""".format(i, i, i -1)

    i -= 1
[/PHP]

Alright, let's take this bit by bit - 

```
i = 99    
for i in range(99,1,-1):
```

Here, there's no need to set i as 99. What the for statement in Python does is iterate over an object. The range function returns an iterable, and the for loop will go through each value in the iterable. If you want to find out more, try ```
print range(99,1,-1)
``` and see what you get.

Now to show you why you don't need to assign it in more detail -
When broken down to bytecode, those two lines produce the following - 
```

 3           0 LOAD_CONST               1 (99)
              3 STORE_FAST               0 (i)

  4           6 SETUP_LOOP              90 (to 99)
              9 LOAD_GLOBAL              0 (range)
             12 LOAD_CONST               1 (99)
             15 LOAD_CONST               2 (1)
             18 LOAD_CONST               3 (-1)
             21 CALL_FUNCTION            3
             24 GET_ITER            
        >>   25 FOR_ITER                70 (to 98)
             28 STORE_FAST               0 (i)
```
Notice how the constant 99 is loaded twice without need, and STORE_FAST is called before the for loop, making it pointless?

The same applies for the line 
```

i -= 1

```
It's simply not needed, the for statement does that all for you.

On the line 
```
print """{0} bottles of beer on the wall, {1} bottles of beer.
    Take one down and pass it around, {2} bottles of beer on the wall.\n""".format(i, i, i -1)
```
You've used string formatting, but got it slightly wrong - if you use {0} twice here, instead of {0} and {1}, as you have two placeholders that take the same value, you can instead have -

```
print """{0} bottles of beer on the wall, {0} bottles of beer.
    Take one down and pass it around, {1} bottles of beer on the wall.\n""".format(i, i -1)
```
which avoids the horrible looking clutter of (i, i, i-1)


Another alternative for the for loop is to do something like - 

```



"""Adjustment here, so that the for loop only runs through when i is at least 3"""
for i in range(99,2,-1):
           
        print """{0} bottles of beer on the wall, {1} bottles of beer.
Take one down and pass it around, {2} bottles of beer on the wall.\n""".format(i, i, i -1)


else:
    """This code runs when the for loop has finished"""
    print """2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around.  1 bottle of beer on the wall.\n"""

    print """1 bottle of beer on the wall.  1 bottle of beer.
Take one down and pass it around.  No bottles of beer on the wall.\n"""

    print """No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."""

```
This makes use of the for...else clause, very handy with something like this as there's no need to make a comparison for each value in the iterable.

---

### Post by Bachstelze on 2011-07-14
```
        print """2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around.  1 bottle of beer on the wall.\n"""
```

I would make it:

```

        print "2 bottles of beer on the wall, 2 bottles of beer."
        print "Take one down and pass it around.  1 bottle of beer on the wall.\n"
```

Bacause having an unindented line in the middle of a block disturbs me visually. Especially in Python, where intendation is paramount.

---

### Post by Randy Flagg on 2011-07-14
LOL, you guys have to give me a minute to update the code.  I really like this version.  I see if I wanted to do the last 3 verses the way I was doing them before the for else would be handy but I like how this code makes all the conditions in order and really makes it clear what the code is doing.

[PHP]
#Code outputs lyrics to 99 bottles of beer on the wall
#Version 2
#Included conditions for last three verses and reordered to create
#clearer flow of code

for i in range(99,-1,-1):
    if 99 >= i > 2:    
        print """{0} bottles of beer on the wall, {0} bottles of beer.
Take one down and pass it around, {1} bottles of beer on the wall.\n""".format(i, i -1)        

    if i == 2:
        print """2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around.  1 bottle of beer on the wall.\n"""

    if i == 1:
        print """1 bottle of beer on the wall.  1 bottle of beer.
Take one down and pass it around.  No bottles of beer on the wall.\n"""

    if i == 0:
        print """No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall."""
[/PHP]

---

### Post by Randy Flagg on 2011-07-14
> **Bachstelze said:**
> ```
        print """2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around.  1 bottle of beer on the wall.\n"""
```I would make it:

```

        print "2 bottles of beer on the wall, 2 bottles of beer."
        print "Take one down and pass it around.  1 bottle of beer on the wall.\n"
```Bacause having an unindented line in the middle of a block disturbs me visually. Especially in Python, where intendation is paramount.

I get that but then how should I do the:

```

        [COLOR=#000000][COLOR=#007700]print [/COLOR][COLOR=#DD0000]"""{0} bottles of beer on the wall, {0} bottles of beer.
Take one down and pass it around, {1} bottles of beer on the wall.\n"""[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]format[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]i[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]i [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700])[/COLOR][/COLOR]

```

---

### Post by Tony Flury on 2011-07-14
> **Randy Flagg said:**
> I get that but then how should I do the:

```

        [COLOR=#000000][COLOR=#007700]print [/COLOR][COLOR=#DD0000]"""{0} bottles of beer on the wall, {0} bottles of beer.
Take one down and pass it around, {1} bottles of beer on the wall.\n"""[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]format[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]i[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]i [/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700])[/COLOR][/COLOR]

```


Like this
```

print "{0} bottles of beer on the wall, {0} bottles of beer.".format(i)
print "Take one down and pass it around, {0} bottles of beer on the wall.\n".format(i-1)

```

---

### Post by Randy Flagg on 2011-07-14
Alright, here we go.  Again, thanks a million for the help.

[PHP]
#Ubuntu Forums Beginners Challenge 1
#Code outputs lyrics to 99 bottles of beer on the wall
#Version 2
#Included conditions for last three verses and reordered to create
#clearer flow of code

for i in range(99,-1,-1):
    if i > 2:
        print "{0} bottles of beer on the wall, {0} bottles of beer.".format(i)
        print "Take one down and pass it around, {0} bottles of beer on the wall.\n".format(i-1)        

    elif i == 2:
        print "2 bottles of beer on the wall, 2 bottles of beer."
        print "Take one down and pass it around.  1 bottle of beer on the wall.\n"

    elif i == 1:
        print "1 bottle of beer on the wall.  1 bottle of beer."
        print "Take one down and pass it around.  No bottles of beer on the wall.\n"

    elif i == 0:
        print "No more bottles of beer on the wall, no more bottles of beer."
        print "Go to the store and buy some more, 99 bottles of beer on the wall."
[/PHP]

---

### Post by Bachstelze on 2011-07-14
Another one:

```
    if 99 >= i > 2:    
```

There is no need for this convoluted construct. The for loop says i can never be greater than 99, testing i <= 99 again is reduntant. Also watch out for trailing spaces. ;)

You can also replace those if's with elif's, so as to avoid making unnecessary tests.

---

### Post by Randy Flagg on 2011-07-14
> **Bachstelze said:**
> Another one:

```
    if 99 >= i > 2:    
```There is no need for this convoluted construct. The for loop says i can never be greater than 99, testing i <= 99 again is reduntant. Also watch out for trailing spaces. ;)

You can also replace those if's with elif's, so as to avoid making unnecessary tests.

I made the edits in the last code post.

Got it except for the trailing spaces.  I kind of remember what they are but I don't see where I have any.

---

### Post by Bachstelze on 2011-07-14
> **Randy Flagg said:**
> 
Got it except for the trailing spaces.  I kind of remember what they are but I don't see where I have any.

After the line I pasted (yes, they are still there after your edits). They aren't in my paste for some reaon...

---

### Post by JupiterV2 on 2011-07-14
Is it idiomatic Python to use chained elif's or should it be a switch-like conditional?

---

### Post by Bachstelze on 2011-07-14
> **JupiterV2 said:**
> Is it idiomatic Python to use chained elif's or should it be a switch-like conditional?

There is no switch in Python, or anything close to it. There are convoluted ways to achieve something that looks roughly the same, but in general chains of a handful of elifs are acceptable (if you need more, your algorithm is probably wrong).

---

### Post by TwoEars on 2011-07-14
> **Bachstelze said:**
> There is no switch in Python, or anything close to it. There are convoluted ways to achieve something that looks roughly the same, but in general chains of a handful of elifs are acceptable (if you need more, your algorithm is probably wrong).

Or in fact use dicts, for example - 

```
import random

def action_a(x):
    print 'This is action a with the number %d reporting in!' % x
    print '4 fits in perfectly!'


def action_b(x):
    print 'This is action b with the number %d reporting in!'  % x
    print 'Oh no! There\'s a remainder of 1 when divided by 4!'

def action_c(x):
    print 'This is action c with the number %d reporting in!' % x
    print 'Oh no! There\'s a remainder of 2 when divided by 4!'

def action_d(x):
    print 'This is action d with the number %d reporting in!' % x
    print 'Oh no! There\'s a remainder of 3 when divided by 4!'

actions = {0:action_a, 1:action_b, 2:action_c,3:action_d}

numbers = range(1,20)
random.shuffle(numbers)
for x in numbers:
    actions[x%4](x)

```
Crude example I know, but there we go.

---

### Post by JupiterV2 on 2011-07-14
Nifty, good to know.

---

