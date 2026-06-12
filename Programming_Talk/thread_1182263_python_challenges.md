---
title: "python challenges"
date: 2009-06-08
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-06-08
i need some python challenges, as i prefer to learn by use rather than memorization. i need some challenges that are kinda basic, that i can do with loops, etc, and nothing outside of python

i ran out of ideas. i only had 1

im only 13, and my friends all give me crazy ideas to do, like "make a program that will ignite all the nukes in the world!" *saaaaaad*

it would preferrably use as many as possible of the basic things covered in chapters 1-12 in A BYTE OF PYTHON, the tutorial i am using right now

---

### Post by myle on 2009-06-08
You could try:
[MIT OpenCourseWare](http://ocw.mit.edu/OcwWeb/Electrical-Engineering-and-Computer-Science/6-189January--IAP--2008/Assignments/index.htm) for a gentle introduction to python

and

[http://projecteuler.net/](http://projecteuler.net/)

---

### Post by Greyed on 2009-06-09
Create either a random dice roll generator which parses standard xdy+/-z notation or build a random password generator which accepts input for a pattern.  The latter has the benefit of having a practical use.  Both, however, would get you to step through basic input/output, random number generation, input sanitation/parsing and basic control/looping structures.  IE, they are simple projects which introduce you to the foundation of pretty much any language.

---

### Post by flyingsliverfin on 2009-06-09
i might need some more explanation about this: 
what is an algorithm (i probably should know this)? 
how do i create one??

thx


i think that the random number generations ill try... though i have no idea where to start

---

### Post by soltanis on 2009-06-09
An algorithm is how you solve a specific problem. If you wanted to find the hypotenuse of a triangle, the equation you would use would of course be

a^2 + b^2 = c^2

The algorithm would be the computational steps required to find c:

[php]
# python

from math import sqrt

def hypotenuse(a,b):
    c_squared = (a * a) + (b * b)
    return sqrt(c_squared)
[/php]

The algorithm here was, square a, square b, add them together, and store the result; then, take the square root of the result and return it from the function. You could've also done

[php]
from math import sqrt

def hypotenuse(a,b):
    return sqrt((a * a) + (b * b))
[/php]

Which does the same thing but in one line of code, or done

[php]
from math import sqrt

def hypotenuse(a,b):
    a_squared = a * a
    b_squared = b * b
    c_squared = a_squared + b_squared
    return sqrt(c_squared)
[/php]

All these examples implement the same formula, or function, but each uses different algorithms, or individual computational steps.

The ideal one would be the single-line function, which uses the least amount of intermediate variables which serve no purpose: but the python interpreter itself couldn't care less which one you use.

---

### Post by flyingsliverfin on 2009-06-10
im guessing that im not going to invent any of my own algorithms soon... ide have to find them, prove them (all things i hate).

thx

so where do i start with  the random password generation??

---

### Post by Greyed on 2009-06-11
> **flyingsliverfin said:**
> im guessing that im not going to invent any of my own algorithms soon... ide have to find them, prove them (all things i hate).

Practically speaking that is programming on a micro scale.  Creating algorithms to do things.

> so where do i start with  the random password generation??

Wouldn't be much of a challenge if we gave you the answer first, would it?  ;)

---

### Post by flyingsliverfin on 2009-06-11
true
i think i have an idea how to start it using import random ->  random.seed(the input taken in) etc

i can't work on it this week cuz im really busy with 2 camps/1  week.

ill see if i can work on it in the 2nd week of vacation.

---

### Post by RobOrr on 2009-06-11
pythonchallenge.com is entertaining, and helps you think about using programming skills to problem solve, as several of the challenges could be done without using programs, but they'd take a human with pen and paper ages. It definitely helped me think about programming ways to achieve an objective, rather than the raw programming knowledge.

---

### Post by flyingsliverfin on 2009-06-11
ill check it out

---

### Post by Greyed on 2009-06-12
> **flyingsliverfin said:**
> i think i have an idea how to start it using import random ->  random.seed(the input taken in) etc

Close.  You wouldn't seed based on the input.  If you did and they used the same pattern then the passwords generated would be identical.  Besides, random seeds itself once imported.

Actually, let me give you a little more to go on since you've shown interest on the random password generator.  The one I have written, which is one I've written in several languages as a way to learn the basics of those languages, does the following:

[LIST=1]
[*]Presents a default pattern but accepts a pattern from the user.
[*]The pattern classifies each character position.  Upper/lower case, vowel/consonant, number and symbol are recognized.  So bab11bab is different than Bab11bab since the first letter is capitalized.
[*]It outputs a 5x5 matrix of random passwords based on the pattern given.  This is so the end user can pick a random password they are likely to remember.
[/LIST]
Here's a sample run:

```

{grey@teleute:~/bin} ./newpass.py Jon1jon%
 Mac6new@ Qin1zat> Dem4mux/ Tah5hed< Pet6cas/
 Get8yuv= Kuf0kaq{ Jix0tud@ Lat2kew( Vih2zed,
 Suh8jek, Vut6diy= Xaj2cuf& Dod5zix> Jan1jix#
 Raw4sev> Zun0def. Viy2kod/ Cav6hep, Nap2pus}
 Hox2gal\ Tux5rak. Gud5tox} Nug0fic) Xor0jew|

```My Python code is 44 lines long and touches on imports, defining and using functions, loops, conditionals, basic data structures and basic command-line parsing.  Now, not saying any version you produce would have to have the same functionality nor fit in the same number of lines, but that should give you a good idea on where to get started and a good goal to shoot for.  :)

As an aside now looking at my version I realize this is a really old one.  It's written for Python 1.5.2 in mind.  I am actually using...
[php]
if set.find(x) > -1:
[/php]

...instead of...

[php]
if x in set:
[/php]

I might just go and clean this up.  Darn you making me look at old code.  ;)

---

### Post by flyingsliverfin on 2009-06-12
lol... this doesn't sound too simple.

ill be gone for a couple days

cya

---

### Post by flyingsliverfin on 2009-06-15
ok, heres what i figured out so far (this is only for letter input):

inseq = input('enter a sequence of upper & lowercase letters only: ')
inseqlen = len(inseq)
for x in range (0,inseqlen):
	check = inseq[x]
	if check.upper == check:
		print check,'is uppercase'
	else:
		print check,'is lowercase'


several questions:
for each time it goes through a x, it get a new value for the check, right? so how do i store that info in new variables each time? i don't know how to cycle through variables...

also, since the letters in the input sequece are   not seperated by commas, i can't use the ___[x] notation; what would i use instead?                                then again, i could just ask the user to input with commas

---

### Post by Greyed on 2009-06-15
> **flyingsliverfin said:**
> ok, heres what i figured out so far (this is only for letter input):

Always good to put these into code blocks, it preserves indentation which is essential for Python code.

```

inseq = input('enter a sequence of upper & lowercase letters only: ')
inseqlen = len(inseq)
for x in range (0,inseqlen):
    check = inseq[x]
    if check.upper == check:
        print check,'is uppercase'
    else:
        print check,'is lowercase'

```First off, you don't need to know the length nor use range on the for loop.  Since strings are an iterable class of data you can just use the "for x in y" form.

```
>>> a = 'a string'
>>> for x in a:
...     print x
... 
a
 
s
t
r
i
n
g

```> for each time it goes through a x, it get a new value for the check, right?Correct.

> so how do i store that info in new variables each time?Why would you have to?

> i don't know how to cycle through variables.Cycle through variables?  Generally speaking when you want to store discrete pieces of related data you're either going to use a list or a dict.  The choice is really up to the form of access and method of identification you need.  Lists are best for sequential access where identification is based on position within the list.  Dicts are best for random access where identification is based more on some other piece of non-numeric identifier.

> since the letters in the input sequece are   not seperated by commas, i can't use the ___[x] notation; what would i use instead?Why not?  Strings are an iterable.  All iterables can be sliced in Python.

```

'a string'
>>> a[1]
' '
>>> a[0]
'a'
>>> a[2]
's'

```> then again, i could just ask the user to input with commasWouldn't help.  There's a difference between "a,w,o,r,d" and ['a','w','o','r','d'].  The first is a single string with letters interspersed by commas.  The latter is a list with 5 elements, each being a single letter.  If you had the first you could not treat it as the second without first doing some work.  Besides, generally not a good idea to rely on user input in that manner.  :D

With that said you have a good start.  You're asking for input, iterating over that input to see if each piece is upper or lower case.  That's good progress on thinking through the problem.  Here's a suggestion though, instead of checking for case perform a different check.  By checking for case you're also setting yourself up for having to check for letter vs number vs symbol as well as consonant vs vowel when it is a letter.  There is a way to check for each of those with a single generic test.

```

if x in y:

```

Try thinking of a way to order your data to test for all of the above using if x in y:

---

### Post by flyingsliverfin on 2009-06-16
hey ive modified mine slighty. sorry, i did this before i read ur post. if y don't mind, ill stick with the in range thing, it just seeems easier to me... and it works. i found that if i just keep the input without commas and put into, say, x, then it converts it into a list automatically :) very useful.heres what i updated 

cases = [] 
inseq = input('enter a sequence of upper & lowercase letters only: ')
inseqlen = len(inseq)
for x in range (0,inseqlen):
	check = inseq[x]
	if check.upper == check:
		cases.append('u')		
		print check,'is uppercase'
	else:
		print check,'is lowercase'
		cases.append('l')#

i DO know that i need to indent stuff, but this box keeps getting rid of the tabs/spaces

after this im completely lost. i think i should first make a random sequence using random.random(), Hpwever, then do i make for instance 2 = a, b=3, etc? or is there a way to create random lists of the alphabet...

---

### Post by flyingsliverfin on 2009-06-27
any1 here>?

---

### Post by smartbei on 2009-06-27
Ok - post code in code blocks like this:
[code ]
##code goes here
[/code ](without the spaces)

Now about the random - say you have a list or a string and want to choose a random object, you can use random.choice.
```

import random
MY_STRING = "abcdefg"
random_letter = random.choice(MY_STRING)

```
And there you go.

Also, note that STRING.upper is a method - it needs to be called. Also note that you have an isupper method as well, so you could have:
```

MY_STRING = "abcdefg"
cases = []
for char in MY_STRING:
    if char.isupper():
        cases.append('u')
    else:
        cases.append('l')

```
Better yet, why not:
```

for char in MY_STRING:
    cases.append(char.isupper())

```
Which will give you a list of boolean values, where True means that it was uppercase.
And just for fun, lets do it in one line:
```

cases = [char.isupper() for char in MY_STRING]

```
Notice that that is actually just as readable - for each object in the iteration sequence, do something and stick it in a list.

Good luck with the rest of the project!

---

### Post by flyingsliverfin on 2009-06-27
the attatchment shows what ive worked out. its not done yet. im just wondering how to append three strings into 1 (see last lines of code)

add these as the second to last lines of code

final = sliced_numbers.append
final = sliced_symbols.append

those lines are my problem

---

### Post by ideaplan9 on 2009-06-27
> **flyingsliverfin said:**
> the attatchment shows what ive worked out. its not done yet. im just wondering how to append three strings into 1 (see last lines of code)

add these as the second to last lines of code

final = sliced_numbers.append
final = sliced_symbols.append

those lines are my problem

It's hard to tell what you are looking for but here is what I have for the last lines:

```
final = sliced_alphabet[:]
final = sliced_alphabet+sliced_numbers+sliced_symbols
random.shuffle(final)

final = ''.join(["%s" % item for item in final])

print final
```:cry:

---

### Post by flyingsliverfin on 2009-06-28
what does this do again?

final = ''.join(["%s" % item for item in final])

thx otherwise, it solved my problem...ill be back iin a couple days with the updates codde i hope  :)

---

### Post by flyingsliverfin on 2009-06-28
well, heres what i happened to get right now. (attatched) the new error is down where i defined 'arrange' (im only definning a function becuz i wan the practice :D)   heres the error:

python randomgenerator.py 
enter a sequence: 9H0/%c
9 is a number
H is uppercase
0 is a number
/ is a symbol
% is a symbol
c is lowercase
Traceback (most recent call last):
  File "randomgenerator.py", line 64, in <module>
    arrange()
  File "randomgenerator.py", line 52, in arrange
    final[final_counter] = numbers[final_counter]
UnboundLocalError: local variable 'final_counter' referenced before assignment

i know that there are some bugs and things like what happens if u enter an input that is longer than 10 characters (then u run out of numbers. so lets say that there were 11 total, and the 11th one was  a number, then final_counter would be 11. if it went to find the 11th index, then it would find it does not exist :) can some1 help me resolve this eror for now only? this was supposed to be a kinda self test, and here i am asking for help. so, as little as possible plz

---

### Post by Greyed on 2009-06-28
Interesting work. I can see where you're going and definitely see the steps you're taking to solve the problem.  You're getting the initial pattern, stepping through that pattern to determine what each place holds and then using that as a template attempting to generate a random sequence based on the characteristics of the pattern you identify.  Strictly speaking that is the foundation of programming.  Taking a problem, breaking it down into the steps needed to solve the problem and solving those steps individually.

However, I think you're overthinking portions of this.  For example, why have the alphabet, numbers and symbols as lists?  Remember, both lists and strings are sequences so any code which applies to reading/inspecting sequences will work on both interchangeable.

eg:

[php]
>>> list = ['a', 'b', 'c']
>>> string = 'abc'
>>> list[1:1]
[]
>>> list
['a', 'b', 'c']
>>> string
'abc'
>>> list[0:1]
['a']
>>> string[0:1]
'a'
>>> if 'a' in list:
...     print "aaaaaaayyyeeee"
... 
aaaaaaayyyeeee
>>> if 'a' in string:
...     print "aaaaaaayyyeeee"
... 
aaaaaaayyyeeee
>>> for letter in list:
...     print letter
... 
a
b
c
>>> for letter in string:
...     print letter
... 
a
b
c
[/php]The difference in strings and lists is that strings are immutable sequences of single characters while a list is a mutable array of non-homogeneous objects.  However in this case since we're looking at a sequence of single characters only for inspection and not changing it at all, why not make it easier and just use strings?  Here's the initialization of the data in my script:

[php]
alpha = 'abcdefghijklmnopqrstuvwxyz'
consonant = 'bcdfghjklmnpqrsdtvwxyz'
vowel = 'aeiou'
numeric = '1234567890'
symbol = '!@#$%^&*()-_=+[{]}\|,<.>/?'
[/php]As an aside, if you really need to construct a list of single character elements which need to be mutable, it's ok to cheat...

[php]
>>> the_hard_way = ['a', 'b', 'c', '1', '2', '3']
>>> the_easy_way = 'a b c 1 2 3'.split()
>>> the_easy_way
['a', 'b', 'c', '1', '2', '3']
[/php]Also something else to keep in mind...

[php]
        if check.isalnum()==True:
                if check.isdigit() == True:
[/php]If you're checking Boolean there's no reason to compare it against anything.  If it is true the check passes, if it is false, it does not.

[php]
>>> istrue = True
>>> if istrue == True:
...     print "This works, but..." 
... 
This works, but...
>>> if istrue:
...     print "just checking istrue directly works and reads better."
... 
just checking istrue directly works and reads better.
[/php]Finally, there's a better method in the random library for getting the random characters.  random.choice().  It takes a sequence and picks an element (or elements) from that sequence and returns that element.

[php]
>>> import random
>>> letters = 'abcde'
>>> for x in range(5):
...     random.choice(letters)
... 
'b'
'e'
'b'
'c'
'a'
[/php]

Overall though it is a good amount of progress.  Notice that my criticisms above are more about language idioms and knowledge more so than actual programing methodology.  Both of those are addressable through time and experience.  :)

---

### Post by Greyed on 2009-06-28
> **flyingsliverfin said:**
> 
  File "randomgenerator.py", line 64, in <module>
    arrange()
  File "randomgenerator.py", line 52, in arrange
    final[final_counter] = numbers[final_counter]
UnboundLocalError: local variable 'final_counter' referenced before assignment

You're using a global variable in a function and trying to assign a value to it.  You cannot doing that without declaring your intent to assign values to the global function.  Reading global variables from inside a function is ok, assigning to is not.

[php]
x = 'a'

def readglobal():
    print(x)

def correctly_modify():
    global x
    x = b

def incorrectly_modify():
    x = b

readglobal()
correctly_modify()
incorrectly_modify()[/php]

---

### Post by flyingsliverfin on 2009-06-28
right.... i think ill ignore ur previous post cuz its confusing my poor 13-year old brain :-(

do u mind if i keep my program the way it currently is so i can understand it beter? maybe when its done ill change it 

right so all i have to do is:

```
global final_counter = 0
```        in the beginning?
or should i define ```
global final_counter = 0
``` in the function itself?

---

### Post by flyingsliverfin on 2009-06-28
oh i see. ive updated the program now. theres a new error. can u exceute it on ur own? i don't feel like pasting the error right now :)

---

### Post by flyingsliverfin on 2009-06-29
forget it :) i got it AND AM DONE WITH THE PROGRAM :p. Thx for the help every1.

if any1 wants to see the end result u can check the attatchment. The comments are there cuz my i learned from my brother (he had a bad experience with this) that things u delete might be needed later :).

---

### Post by Greyed on 2009-06-30
It indeed works.  For comparison here's the random password generator I wrote ages ago.

[php]
#!/usr/bin/python

# random password generator

import random
import string
import sys

# character sets
alpha = 'abcdefghijklmnopqrstuvwxyz'
consonant = 'bcdfghjklmnpqrsdtvwxyz'
vowel = 'aeiou'
numeric = '1234567890'
symbol = '!@#$%^&*()-_=+[{]}\|,<.>/?'
sets = [consonant,
        consonant.upper(),
        vowel,
        vowel.upper(),
        numeric,
        symbol]
passes = 15
maxcol = 5
maxrow = 5
def_pattern = 'babbab99'

# set a pattern
if len(sys.argv) == 2:
    pattern = sys.argv[1]
else:
    pattern = def_pattern

def genpass(pattern):
    newpass = ''
    for x in pattern:
        for set in sets:
            if x in set:
                newpass = string.join([newpass, random.choice(set)], '')
    return newpass

for y in range(maxrow):
    line = ''
    for x in range(maxcol):
        line = string.join([line, genpass(pattern)], ' ')
    print line

[/php]

And what you say about things being deleted is true.  That is what revision control is for.  On a small project like this it is overkill but if you start working on something larger or spans a large chunk of time revision control is a very good habit to get into.  :)

---

### Post by sidious1741 on 2009-06-30
I wanted to let you know that an algorithm doesn't just have to be mathematical.  You apply an algorithm to solving a rubix cube or a sudoku puzzle or even searching for keys (look in kitchen, bedroom, office, repeat).
I see your caught up in the generator, but If your still interested, You could make a program that does a cryptography thing.  If you know that the letters (h,e,l,l,o) are used but you don't know what order, you can find all the different possible combinations and compare them to a dictionary file to see which combinations are actually words.  (Ubuntu has a dictionary file at /usr/share/dict/words)
Have fun with python.  It's a great language.

---

### Post by flyingsliverfin on 2009-07-01
yay!

i think im taking a break from python for a bit, then im going to get a real python book/tutorial... A Byte of Python is a bit incomplete.

then im going to go to OOP... then i might take on another challenge :)

---

