---
title: "Another silly Python excercise"
date: 2009-07-10
forum: Programming Talk
---

### Post by crownedzero on 2009-07-10
```
#Number guessing game

print '''Welcome to the guessing game!
The computer will select a random number between 1 and 100. You must then
correctly guess the random number in as few tries as possible.
Good luck! Type 'quit' at anytime to exit.'''


import random

random_num = random.randint(1,100)
x = 0
guessing = True

while guessing:
    x = x + 1
    guess = raw_input('Enter what you think the number might be: ')
    
    if guess in ['QUIT', 'Quit', 'quit']:
        print 'Thanks for playing!'
        break
    elif int(guess) == random_num:
        print 'Congratulations, you got it in only ', x,' guess(es)'
        guessing = False
    elif int(guess) > random_num:
        print 'Please try a lower number'
    elif int(guess) < random_num:
        print 'Please try a higher number'
```
Supposing the user puts in something completely wrong. For example typing 'qui' how would you put in a catch all here?

---

### Post by fredscripts on 2009-07-10
putting an else clause after all elif's so you can handle input that isn't any one of the other if's?

edit: first checking if the "guess" variable is a number, then if not if is a QUiT like and then the rest of possibilities just alert the user with wrong input.

---

### Post by Can+~ on 2009-07-10
> **crownedzero said:**
> Supposing the user puts in something completely wrong. For example typing 'qui' how would you put in a **catch** all here?

You answered your own question.

[PHP]>>> int("Hello")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'Hello'[/PHP]

[PHP]>>> try:
...     int("Hello")
... except ValueError:
...     print "Only numbers my friend."
... 
Only numbers my friend.[/PHP]

This is known as [Exception Handling]("http://docs.python.org/tutorial/errors.html"). In the moment that something on the try: statement fails, it will jump to the nearest except and check if it handles it's error. This can expand through the entire call stack.

Btw, you can also change this:

[PHP]if guess in ['QUIT', 'Quit', 'quit']:[/PHP]

to this:

[PHP]if guess.lower() == "quit":[/PHP]

---

### Post by crownedzero on 2009-07-10
That doesn't work. For the input I am not assigning "guess" as an int. "guess" is changed to an int during the <> statements.

---

### Post by crownedzero on 2009-07-10
> **Can+~ said:**
> You answered your own question.

[PHP]>>> int("Hello")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'Hello'[/PHP]

[PHP]>>> try:
...     int("Hello")
... except ValueError:
...     print "Only numbers my friend."
... 
Only numbers my friend.[/PHP]

This is known as [Exception Handling]("http://docs.python.org/tutorial/errors.html"). In the moment that something on the try: statement fails, it will jump to the nearest except and check if it handles it's error. This can expand through the entire call stack.

Btw, you can also change this:

[PHP]if guess in ['QUIT', 'Quit', 'quit']:[/PHP]

to this:

[PHP]if guess.lower() == "quit":[/PHP]
I'm following, and yet at the same time I'm not. I get what your saying but if you can't tell I'm learning and I'm not quite sure where this should take place.

---

### Post by Can+~ on 2009-07-10
[PHP]#!/usr/bin/python

import random

random_num = random.randint(1,100)
guessing = True
x = 0

while guessing:
	guess = raw_input('Enter what you think the number might be: ')
	x += 1
	
	try:
		#Let's assume it's an integer
		guess = int(guess)
		
		if guess == random_num:
			print 'Thats it! It took you',x,'tries'
			guessing = False
		elif guess > random_num:
			print 'Try lower'
		elif guess < random_num:
			print 'Try higher'
	
	except ValueError:
		#The assumption was wrong, maybe he wrote quit?		
		if guess.lower() == 'quit':
			print 'Goodbye'
			guessing = False
		#Nope, he didn't
		else:
			print 'Only numbers and the "quit" command are available.'

[/PHP]

---

### Post by crownedzero on 2009-07-10
> **Can+~ said:**
> [PHP]#!/usr/bin/python

import random

random_num = random.randint(1,100)
guessing = True
x = 0

while guessing:
	guess = raw_input('Enter what you think the number might be: ')
	x += 1
	
	try:
		#Let's assume it's an integer
		guess = int(guess)
		
		if guess == random_num:
			print 'Thats it! It took you',x,'tries'
			guessing = False
		elif guess > random_num:
			print 'Try lower'
		elif guess < random_num:
			print 'Try higher'
	
	except ValueError:
		#The assumption was wrong, maybe he wrote quit?		
		if guess.lower() == 'quit':
			print 'Goodbye'
			guessing = False
		#Nope, he didn't
		else:
			print 'Only numbers and the "quit" command are available.'

[/PHP]


Lol, did you just cheat?

---

### Post by Can+~ on 2009-07-10
> **crownedzero said:**
> Lol, did you just cheat?

What do you mean?

---

### Post by nvteighen on 2009-07-10
> **crownedzero said:**
> Lol, did you just cheat?

Yes, he did :)

Exceptions allow you to catch a certain type of error so you can handle it instead of letting the whole program crash... But, as a lot of stuff in the programming world, there are people who like them and there are people who hate them. I'm somewhat nearer to the Exception-haters, but I do use them when they are handy.

In this case, as **int()** will "throw" (aka "raise") a ValueError exception when it fails... you're sort of forced to use the **try...expect**.

The basic syntax is:
```

try:
    # Code to be tried :) Try to keep this as shortest as possible,
    # so the testing is done to the most precise extent.
except *ExceptionName*:
    # Code to be executed if something in the try block yields an 
    # exception *ExceptionName*.
finally:
    # This code will always be executed no matter whether the desired 
    # exception was caught or not. The finally block is optional.

```

In the **except** block you can test for more than one Exception, by enclosing all of them into parentheses **(Exception1, Exception2, ...)** but it's generally not a good idea as you'll be testing for too much things at once.

That's all (and maybe more) that you need now, I think.

---

### Post by JordyD on 2009-07-10
> **nvteighen said:**
>  But, as a lot of stuff in the programming world, there are people who like them and there are people who hate them.

Why would you hate them? Is there something bad about them?:confused:

---

### Post by Can+~ on 2009-07-10
> **nvteighen said:**
> Exceptions allow you to catch a certain type of error so you can handle it instead of letting the whole program crash... But, as a lot of stuff in the programming world, there are people who like them and there are people who hate them. I'm somewhat nearer to the Exception-haters, but I do use them when they are handy.

I remember seeing a piece of code for a game server in C++ that had almost 5000 lines a single file that checked certain spells.

Each spell had to do different "sanity checks" to ensure that certain conditions are met like "Make sure the caster isn't NULL", "Make sure that the SpellID isn't 0", etc.

They never used a single piece of try..catch for that situation, and it would've been perfect, for example (In python though, so the OP can understand too):

[PHP]def func1():
    if check_condition_1:
        return None

    if check_condition_2:
        return None

    ...

    do stuff

def func2():
    if check_condition_2:
        return None

    if check_condition_3:
        return None

    ...

    do stuff

def usefunc(funcid):
    funcdict[funcid]()[/PHP]

This had to be repeated for pretty much everything, expand this to 300 different functions.

This is how it would look like with Exceptions:

[PHP]def func1():
    do stuff

def func2():
    do stuff

def usefunc(funcid):
    try:
        funcdict[funcid]()
    except error1:
        print "you are out of Mana"
    except error2:
        print "you are dead."
    except error3:
        print "you are dead and out of mana, what else do you want?"[/PHP]

This is just a little story to show that even if exception Handling seems redundant an even stupid on trivial code, the big advantage, is that the code becomes more "scalable" in terms that, next time you want to create a function above, you could just write it and make sure all the exception Handling is being taken care of.

---

### Post by JordyD on 2009-07-10
> **Can+~ said:**
> 
[PHP]
    except error1:
        print "you are out of Mana"
    except error2:
        print "you are dead."
    except error3:
        print "you are dead and out of mana, what else do you want?"[/PHP]

I so wish you wrote the kernel messages.

Torvald's version of the above:
"SIGMOUT"
"SIGDEAD"
"SIGMOUTDEADWHATWANT"
"Game Panic"

---

### Post by nvteighen on 2009-07-11
> **JordyD said:**
> Why would you hate them? Is there something bad about them?:confused:

I admit my preference for return values over exceptions is because of my C background :p But again, I'm not a fundamentalist exception-hater! I just use them as my second option.

The critique is essentially the same against **goto**/**longjmp()**. An exception is an interrupt that let's you jump from some place to another one. Ok, exceptions are "typed" and therefore they are a kind of "computed goto" (gotos that work with restrictions), but they still ignore the program's structure.

Interrupts are not evil by themselves, but can lead to evil situations when they allow you to do very long jumps. **break**/**continue** in loops are also interrupts, but they won't allow you to jump from one call stack to the other... but just move yourself inside the same call stack. When you throw your exception, you're making your program being affected by a global condition (the exception instance), therefore your functions are not 100% predictable from their own locals' behaivor... but affected by another's locals', and also you suddenly change all factors that were leading the execution at that point.

That leads to following API issues: functions that can return something but also raise an exception. Where lies the 1 function = 1 task principle? Ok, your function does something but it also can affect the program's behaivor in its whole...

But, why exceptions are much more acceptable than a goto? Because they are meant to handle errors. And errors will mess the whole execution, so it doesn't matter if you suddenly change from one call stack to another. The problem occurs when you start using exceptions to handle situations derived from the program's normal functioning... That's why that game server's example by Can~+ IMO should have been dealt with conditions or, maybe, using some signal (event-driven programming) system.

I restrict myself the use of exceptions to two situations:
1. When a standard built-in function is able to raise exceptions. In that case, I catch them... You know, when you accept to use an API, you accept to follow the rules :) If you don't like them, you better reimplement everything :p
2. When some situation is able to cripple the normal execution of some program that is not resolvable by making the function **return** something (and therefore exit that call stack) the caller can interpret.

The problem in Python is that it lacks a **switch** statement like C and C++'s and you have to use all that annoying if...elif's...

---

### Post by JordyD on 2009-07-11
> **nvteighen said:**
> The problem in Python is that it lacks a **switch** statement like C and C++'s and you have to use all that annoying if...elif's...

I believe that's from the Pythonistas' view of "one way to do everything".

Plus, why are they so annoying? The combination of if and elifs are basically a switch statement. You just have to retype what you are checking a lot.

---

### Post by smartbei on 2009-07-11
Occasionaly when you have a bunch of if...elifs... in a switch-like pattern, they can be replaced with a dictionary - for example:
```

def process_add(arg1, arg2):
    ## code here

def process_sub(arg1):
    ## code here

ACTIONS = {'add': process_add, 'sub': process_sub,
          ## ...
          }
def process(command, *args):
    if command in ACTIONS:
        ACTIONS[command](*args)
    else:
        raise ValueError("Incorrect comamnd passed")

```

Of course, you could also have the functions be declared in the main 'process' function, and the dictionary also.

---

### Post by crownedzero on 2009-07-14
> **nvteighen said:**
> Yes, he did :)

Exceptions allow you to catch a certain type of error so you can handle it instead of letting the whole program crash... But, as a lot of stuff in the programming world, there are people who like them and there are people who hate them. I'm somewhat nearer to the Exception-haters, but I do use them when they are handy.

In this case, as **int()** will "throw" (aka "raise") a ValueError exception when it fails... you're sort of forced to use the **try...expect**.

The basic syntax is:
```

try:
    # Code to be tried :) Try to keep this as shortest as possible,
    # so the testing is done to the most precise extent.
except *ExceptionName*:
    # Code to be executed if something in the try block yields an 
    # exception *ExceptionName*.
finally:
    # This code will always be executed no matter whether the desired 
    # exception was caught or not. The finally block is optional.

```

In the **except** block you can test for more than one Exception, by enclosing all of them into parentheses **(Exception1, Exception2, ...)** but it's generally not a good idea as you'll be testing for too much things at once.

That's all (and maybe more) that you need now, I think.

Just FYI these kind of explanations rock!

That and I'm amazed at how a simple script can spark such an interesting debate. Should I break out the popcorn?

---

### Post by hetx on 2009-07-14
Yeah honestly this is 100 times better than most tutorials!

---

### Post by lavinog on 2009-07-14
> **smartbei said:**
> Occasionaly when you have a bunch of if...elifs... in a switch-like pattern, they can be replaced with a dictionary - for example:
```

def process_add(arg1, arg2):
    ## code here

def process_sub(arg1):
    ## code here

ACTIONS = {'add': process_add, 'sub': process_sub,
          ## ...
          }
def process(command, *args):
    if command in ACTIONS:
        ACTIONS[command](*args)
    else:
        raise ValueError("Incorrect comamnd passed")

```

Of course, you could also have the functions be declared in the main 'process' function, and the dictionary also.

Cool, I really have to work with dictionaries more.
One thing that bugs me though is the test for key existance. Is there less of a performance hit if you use:
```

def process(command, *args):
    try:
        ACTIONS[command](*args)
    except:
        raise ValueError("Incorrect command passed")

```

---

