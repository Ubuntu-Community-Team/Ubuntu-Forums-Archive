---
title: "Random File"
date: 2007-07-15
forum: Programming Talk
---

### Post by nhandler on 2007-07-15
I'm trying to figure out how to pick a random file in bash. So for example, I use 'ls' to generate a list of all the files in the current directory. I then want to be able to pipe (|) it to a "random" command that will return the name of one of the files chosen randomly. I know you can generate a random number with bash. So I assume the way to go about this would be to put the output of ls in an array and then generate a random number based on the length of the array. And then use that random number to return a random filename.

That might be totally wrong (I'm basing that solely on prior knowledge of other languages). I'm just interested in an easy way to go about this.

---

### Post by Mr. C. on 2007-07-15
That sounds like a perfectly good way to solve the problem.

No need to pipe - just pick a random number.

Here's a nice trick - see if you can figure out what is going on.  Change directories into the directory you want to select random files, and then run:

```
set -- *
echo ${3}
```

MrC

---

### Post by nhandler on 2007-07-16
Thanks a lot! That worked perfect. But I'm having a hard time figuring out what it means. Here is what I found about the set -- part:

    If no arguments follow this option, then the positional parameters are unset. 
    Otherwise, the positional parameters are set to the arguments, 
    even if some of them begin with a `-'. 

But I still don't get how it chooses a random file. I know * is a wildcard and that set is normally used to set variables.

---

### Post by Mr. C. on 2007-07-16
The * in this context is a file pattern maching wildcard.  It matches every file (not including dot files like .bashrc).

The statements I gave do not choose a random file; they showed you how to setup the array, and how to access the nth cell.

Search **man bash** for **random**.  Then search for **Arithmetic Expansion** and **ARITHMETIC EVALUATION**.

MrC

---

### Post by jyba on 2007-07-16
Your original post was phrased in a way that suggested that you didn't want the code written for you but just wanted some hints on how to do it yourself.

Your analysis of the problem was spot-on...

[B]1. put the output of 'ls' in an array
2. then generate a random number based on the length of the array
3. and then use that random number to return a random filename.[/B]

Mr. C. helped you with the first of these problems by showing you a nifty one-liner that fills an array without the bother of looping through the output of 'ls' and assigning each filename to the array individually. To understand it remember that before the builtin command 'set' is evoked, the shell has to parse the line "set -- *". When the shell sees the asterisk it expands it into a string of all the files in the current directory. Then 'set' is evoked and given the option '--' and the string of arguments, so it sets the positional parameters (from $1 upwards) to those filenames. 

Anyway, now you have to solve items 2 and 3 in your list - generate a random number within a set range, and use that number to return a random filename from the array.

Here's a trick to help you with the 3rd problem...
Assuming that in stage two you've assigned your random number to the variable 'random_num', try...
```
echo ${!random_num}
```
The '!' has a special significance here.

---

### Post by Mr. C. on 2007-07-16
> **jyba said:**
> 
Assuming that in stage two you've assigned your random number to the variable 'random_num', try...
```
echo ${!random_num}
```
The '!' has a special significance here.

... assuming the random number has been properly scaled to fit.  Good technique.

MrC

---

### Post by jyba on 2007-07-16
Yes, but I think it's for Cheater to figure out how to turn some huge random number into a number within the range of '1' to 'the number of files'. His statement 'generate a random number based on the length of the array' suggests he's most of the way there.

---

### Post by Mr. C. on 2007-07-16
We're in complete agreement.  My clarification was aimed towards mollifying the frustration at running your variable expansion and having nothing returned.  Examples, in my opinion, should produce results, not blank lines, which leads to confusion.

MrC

---

### Post by jyba on 2007-07-16
Okay, agreed; at risk of confusing matters...
```
set -- "elephant" "tiger" "penguin" "kangaroo"
number=3
echo ${number}          #  Echo's "3"
echo ${!number}         #  Why does this echo "penguin"?
```
Anyway, you've sorted problem one, I've sorted problem three. Over to Cheater... :)

---

### Post by nhandler on 2007-07-16
Thanks a lot for all of your help. I've really learned a lot about bash.

For anyone wondering, here is the final script I came up with

```

set -- *
length=$#
random_num=$(( $RANDOM % ($length + 1) ))
echo ${!random_num}

```

---

### Post by Mr. C. on 2007-07-16
Very good!

---

### Post by pmasiar on 2007-07-16
> **Cheater said:**
> I'm trying to figure out how to pick a random file in bash. 

after so much hassle doing it in bash, here is very obvious and readable (no magic!) way how to print random file from current directory in Python:

```

import os
import random
where = '.' # source directory 

ls = os.listdir(where)
print random.choice(ls)

```

---

### Post by Mr. C. on 2007-07-16
The *hassle* in your eyes is simply *learning* to another's.  Your predilection towards python is fine, but to believe and espouse that "import os", "import random", and "where = '.'" are not yet just another form of spell-casting with a different spell-book is myopic.

*Every* language and system requires foundational knowledge, until which is learned, seems obtuse.

MrC

---

### Post by hod139 on 2007-07-16
> **Cheater said:**
> Thanks a lot for all of your help. I've really learned a lot about bash.

For anyone wondering, here is the final script I came up with

```

set -- *
length=$#
random_num=$(( $RANDOM % ($length + 1) ))
echo ${!random_num}

```


Very nice!  What happens if there are more than 32767 files in the directory?

---

### Post by jyba on 2007-07-16
Ay-yay, when were you last unwise enough to put 32767 files in a directory (and how did the GUI cope with it?). Back to reality, well done Cheater, you definitely have what it takes.

---

### Post by hod139 on 2007-07-16
> **jyba said:**
> Ay-yay, when were you last stupid enough to put 32767 files in a directory (and how did the GUI cope with it?)

Just a few hours ago actually!  I was generating a movie and had a directory containing many individual frames of screen shots to be combine by mencoder.  Not very stupid is it.  Do not misinterpret your normal daily activity as every else's, especially when programming.  Handling all possible input correctly and proving the correctness of your algorithm is where hackish programming ends and computer science begins.

---

### Post by Mr. C. on 2007-07-16
Settle down boys.  There are merits to both sides.

Quick solutions that fit the requirements are sufficient; the end cases should be noted and user made aware.

Proving program correctness and handling all possible cases becomes impossible as the problem space increases.  The best we can do is approximate and perform risk analysis.

MrC

---

### Post by pmasiar on 2007-07-17
> **Mr. C. said:**
> *Every* language and system requires foundational knowledge, until which is learned, seems obtuse.

I appreciate your deep knowledge of bash, but *for me* it is easier to remember "random.choice(listname)" than magical incantation "set -- *". I know some (very basic) bash, and cannot understand what is happening in bash example.

I was just tempted to solve OP's problem using different approach (without need to study docs or anything), and to show/compare. I did not know it is a crime. :-)

---

### Post by Mr. C. on 2007-07-17
No crime, no problems.

There are some universal truths about computer languages that you learn after studying and learning them for so many years.

a) No language is self-evident or obvious
b) All languages are insufficient and have deficiencies
c) All languages have strengths and weaknesses
d) All language require trade-offs and compromises
e) Most programmers are uncomfortable with (a) through (d), and many try to *fix* those unfix-able, intractable truths, or persuade other's that they aren't true.

MrC

---

### Post by hod139 on 2007-07-17
> **Mr. C. said:**
> 
There are some universal truths about computer languages that you learn after studying and learning them for so many years.

a) No language is self-evident or obvious
b) All languages are insufficient and have deficiencies
c) All languages have strengths and weaknesses
d) All language require trade-offs and compromises
e) Most programmers are uncomfortable with (a) through (d), and many try to *fix* those unfix-able, intractable truths, or persuade other's that they aren't true.

MrC

This should be stickied on the front page!

---

### Post by pmasiar on 2007-07-17
> **Mr. C. said:**
> No crime, no problems.

There are some universal truths about computer languages that you learn after studying and learning them for so many years.

a) No language is self-evident or obvious
b) All languages are insufficient and have deficiencies
c) All languages have strengths and weaknesses
d) All language require trade-offs and compromises
e) Most programmers are uncomfortable with (a) through (d), and many try to *fix* those unfix-able, intractable truths, or persuade other's that they aren't true.

MrC

I agree 99% - after 25 years and so many languages, I've seen many "silver bullets" become popular and fail. My first one was brief interest in Ada :-)

But even as all languages require compromises, they are not created equal: some are more forward-looking than others. Some do compromises at right places, some made wrong bets. Some are promoted by hype and money, some are promoted by word of mouth of experienced hackers. So it still makes sense to think before start coding, or before investing months to learn library, and years to become proficient (if not expert) in a selected platform.

I read it in MSFT brochure, but it is true regardless: :-) "Think before start coding: Code is like tattoo - it will stick on you for a long time".

And this is one thing my version of code has and your code lacks, IMHO: obviousness for un-initiated reader. Chances are, my Python code will be easier to understand 30 years from now, and your bash code will be like black magic for anyone without your level of deep knowledge of bash (and without comments).

I have nothing but deep appreciation for people like  you, MrC, who knows bash tricks: but my time is limited (as my memory capacity) so I'll skip on it and will keep Python instead. It fits my brains better :-)

---

### Post by the_unforgiven on 2007-07-18
> **jyba said:**
> Ay-yay, when were you last unwise enough to put 32767 files in a directory (and how did the GUI cope with it?). Back to reality, well done Cheater, you definitely have what it takes.
I doubt any serious file manager (let alone a gui tool - even vim's file manager script should be sufficient here - though I haven't confirmed it ;)) would use shell's wildcard to list directory contents :p

---

### Post by dirtysox on 2009-06-01
> **nhandler said:**
> Thanks a lot for all of your help. I've really learned a lot about bash.

For anyone wondering, here is the final script I came up with

```

set -- *
length=$#
random_num=$(( $RANDOM % ($length + 1) ))
echo ${!random_num}

```
how come putting everything in one line doesn't work
```
echo ${$((RANDOM%$#+1))}
```gives
```
bash: ${$((RANDOM%$#+1))}: bad substitution
```this doesn't work either
```
echo ${`echo $((RANDOM%$#+1))`}
```

---

### Post by _H3MLOCK on 2010-01-20
You know there is another simple way to do it.

$DIR=/dirname

$RANDOMFILE=$(ls $DIR | shuf -n1)

and then whatever action to $RANDOMFILE.

---

### Post by artm on 2010-02-17
the original solution is slightly incorrect: once in a while it'll echo ${0} which isn't necessarily a file in current directory. Should have been:

```

set -- *
length=$#
random_num=$(( $RANDOM % $length + 1 ))
echo ${!random_num}

```

or to "put it all in one line":

```

set -- *
echo  $(eval echo \${$(($RANDOM%$#+1))} )

```

if you do this sort of thing often you could create a shell function:

```

random.choice() { echo $(eval echo \${$(($RANDOM%$#+1))} ) ; }

```

now the solution really IS a one liner, and it looks like python function:

```

$ random.choice *
encrange
$ random.choice *
beijer-display
$ random.choice *
XTimer.hpp
$ random.choice *
cmake_install.cmake

```

And you're not limited to using it on files, it returns its random argument:

```

artm@snigel:~/src/beijer/src master$ random.choice foo bar baz
bar
$ random.choice foo bar baz
bar
$ random.choice foo bar baz
foo
$ random.choice foo bar baz
foo
$ random.choice foo bar baz
bar
$ random.choice foo bar baz
foo
$ random.choice foo bar baz
bar
$ random.choice foo bar baz
baz
$ random.choice foo bar baz
baz

```

This is slightly more efficient then piping ls throgh shuf because it doesn't have to spawn extra processes. But that only matters if you use it very often on a busy machine of course and in that case globbing the files into arguments will be the bottleneck.

---

