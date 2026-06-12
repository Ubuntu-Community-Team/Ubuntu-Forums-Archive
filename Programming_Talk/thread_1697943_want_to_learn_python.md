---
title: "want to learn python"
date: 2011-03-01
forum: Programming Talk
---

### Post by sogeking99 on 2011-03-01
hey guys i am learning python, i started reading 'learn python the hard way' as people suggested. it seems good but also...brief like i am learning but am also left with questions.

this for example
```
x = "there are %d types of people." % 10
binary = "binary"
do_not = "don't"
y = "those who understand %s and those who %s" % (binary, do_not)

print x
print y

print "i said: '%r' " % x
print "i also said: '%r' " % y

hilarious = False
joke_evaluation = "isn that joke so funny?! %r"

print joke_evaluation % hilarious

w = "this is the left side of a string..."
e = "that has a right side."

print w + e
```

he doesn't really tell you what % is and why he uses it instead of + most the time. except at the bottom where he does w + e

also, is python good for first time programmers in your opinion? and can it be used to make roguelikes?

thanks.

---

### Post by Vaphell on 2011-03-01
yes it is good for first time programmers, because it's easy to pick up and has a lot of tools that take care of many tasks handled manually in languages like C or C++. You can write programs that do useful stuff fast and good morale is conductive to learning :-)

%
it is used in few contexts
- in print it separates parametrized string from parameters
```
print <string> **%** <parameters>
```
- it is used to indicate placeholders for params in the printed string - %d - number, %s - string, etc
```
print "param1=**%d** param2=**%d** param3=**%s**" % ( 1, 2, "oh noes" )
param1=1 param2=2 param3=oh noes
```
- it is a math operator 'remainder of' eg
```
11 **%** 3
2
```

---

### Post by cgroza on 2011-03-01
Python is a great learning language. The %s, %d, and others are used to insert a string(%s) or an int(%d). I find it more convenient than the + version. I can not realize what is the difference between them.

Maybe in this case:

Say, you take an int and you want it in the middle of a string.
With a + version you would have to do:
"string here"+ str(5) + "string here too"
The other version would be just:
"string here %d string here too"%5

Hope it helped.

---

### Post by sogeking99 on 2011-03-01
thanks guys that helped a lot.

the book im reading is python 2, seems python 3 isn't widely used, is it bad? or is it likely to be standardized anytime soon?

---

### Post by Vaphell on 2011-03-01
it's not bad but it's not good either. While py3 has some nifty features, it's adoption is held back by all the modules people depend on which haven't been ported yet. Py2 is here to stay for some time. When all important modules get translated, people will follow.

---

### Post by robots.jpg on 2011-03-01
> **sogeking99 said:**
> can it be used to make roguelikes?

I had to do a quick search before making a joke about there being a library specifically for making roguelikes, and it turns out there actually *is* one out there with Python bindings that does exactly that, called libtcod.  

I don't know anything about it, but it sounds interesting.

---

### Post by Milliways on 2011-03-01
> **sogeking99 said:**
> 
```
x = "there are %d types of people." % 10
binary = "binary"
do_not = "don't"
y = "those who understand %s and those who %s" % (binary, do_not)

```

The first few lines should be as follows 

```

    x = "there are %d types of people." % 10
    ternary = "ternary"
    binary = "binary"
    do_not = "don't"
    y = "those who understand %s, those who %s and those who confuse it with %s" % (ternary, do_not, binary)

```

---

### Post by sogeking99 on 2011-03-02
what reading material would you guys recommend?

---

### Post by cgroza on 2011-03-02
I learned mostly by online tutorials. Take a look here:
[http://wiki.python.org/moin/PythonBooks/](http://wiki.python.org/moin/PythonBooks/)

---

### Post by sogeking99 on 2011-03-03
thanks.

> #learning python the hard way exercise 13 Parameters, Unpacking, Variables
from sys import argv

script, first, second, third = argv

print "this script is called", script
print "your first variable is:", first
print "your second variable is:", second
print "your third variable is:", third

i dont understand what this is really at all.

---

### Post by cgroza on 2011-03-03
Argv is an array of the command line arguments.
The line:```

script, first, second, third = argv
```
just takes the array and assigns argv[0] to script, arg[1] to first etc.

You should buy a book, explanation are more clear and it really teaches you the terminology.

---

### Post by sogeking99 on 2011-03-03
i like think python but i dont like all the math. this for example

Exercise 2.4 Practice using the Python interpreter as a calculator:
  1. The volume of a sphere with radius r is 4 &#960;r3 . What is the volume of a sphere with radius 5?
                                              3
     Hint: 392.6 is wrong!i am useless at math.

---

### Post by cgroza on 2011-03-03
Just follow the formula,a simple google search threw this:
V = 4/3 &#960;R3
So your volume will be :
4/3*pi*5**3
EDIT: The  raise to the power  got screwed by the editor.

---

### Post by Vaphell on 2011-03-03
392.6 is wrong and 523.3 is correct because you stepped on a mine (we ignore the issue of pi precision, it's unimportant for the problem at hand).
4 / 3 = 1 because integer arithmetic is applied when both arguments are integers, so no matter what is later, the whole expression gives the wrong result.
start with floating point number (pi or 4.0 or whatever) to force the expression to use real numbers

```
>>> pi = 3.14
>>> pi
3.1400000000000001
>>> 4 / 3 * pi * 5**3
392.5
>>> 4.0 / 3 * pi * 5**3
523.33333333333337
>>> 4 / 3
1
>>> 4.0 / 3
1.3333333333333333

```

---

### Post by sogeking99 on 2011-03-03
oh i see now thanks

---

### Post by Crazedpsyc on 2011-03-04
My favorite python book is "Dive into Python" (diveintopython.org). A really great part about it other than the fact that it just explains everything so well is that the onlive version is there in case you need help after you are forced to return the book to your library ;)!
I believe it has at least an entire section (if not a chapter) on string formatting!

---

### Post by ki4jgt on 2011-03-04
I learned Python from TheNewBoston.com it is a complete video series. :-) Kind of beats having to stick with a book all the time. I'll admit, he doesn't cover advanced topics and so you will eventually have to either read a LLLLLOOOOONNNNNGGGGG! website or two or a nice BBBIIIGGG book, but his series is entertaining and FREE! It's a very good way for beginners to learn programming in Python, if I do say so myself.

---

### Post by Shpongle on 2011-03-04
The best thing I can say is JUST DO IT , the more you do the more you'll learn. Its good to have a small project or task in mind and as you go along you'll learn what you need to in order to accomplish the task. Get the basics down first , such as variables , assignment, operators , loops and conditional statements etc.  Good luck

---

### Post by sogeking99 on 2011-03-04
thanks guys, many suggestions here. tough to choose :)

---

### Post by sogeking99 on 2011-03-10
hey guys, just started learning about control flow and stuff. i started this game, well not much of a game but i just wanted to test what i've learned, figured its better than just doing endless book exercises. have i got the right idea? i dont think i do but i've had fun doing it either way. feel free to tell me its rubbish, im not really attached to it :D also, is there a basic tutorial for making one?

thanks.

EDIT: note functions have not been implemented yet :)

   ```
 hp = 30
    
    print 'You enter a dark room with two doors. Do you want to enter door #1 or door #2?'
    door = raw_input('> ')
    
    if door == "1":
        print 'Theres a giant bear eating what appears to be a human arm, though its so damaged it\'s hard to be sure'
        print 'what do you want to do?'
        print '#1 try to take the arm'
        print '#2 scream at the bear'
    
        bear = raw_input('> ')
    
        if bear == "1":
            print 'You approach the bear slowly, never breaking eye contact. After what feel like a thousand years you are finally face to face with the bear. \nYou grab the arm and pull. of course the bear responds by eating you face. well done!'
    
        elif bear == "2":
            print 'You scream at the bear, a decent sound as well. The bear however was not impressed it would seem \nas he insantly eats your face. Well done!'
    
        else:
            print 'Well, doing %s is probably better. Bear runs away.' % bear
    
    elif door == "2":
        print 'You stare into the endless abyss of Bollofumps retina.'
        print 'Oh dear, seems the insanity of Bollofumps existence had driven you quite insane.'
        print '#1. drool'
        print '#2. scream and drool'
        print '#3. Understand the fabrics of molecula toy crafting'
        insanity = raw_input('> ')
    
        if insanity == "1" or "2":
            print 'Your body survives, powered by pure insanity!'
    
        else:
            print 'your mind melts into green flavoured jello! mmm!'
    
    else:
        print 'you think for a while but suddenly a troll weilding a terrible looking knife comes through a trap door and shanks you!'
```

---

