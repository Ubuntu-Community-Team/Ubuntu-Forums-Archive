---
title: "[Python] Help with a simple calculator"
date: 2008-10-09
forum: Programming Talk
---

### Post by dodle on 2008-10-09
I want to build a simple calculator with a gui (for practice), and I'm starting off by making a very simple cli calculator and working my way up.  I'm having trouble with it and I don't understand why.  Can someone please help me with my code?  Please keep in mind that I plan the change all the the input(), to raw_input(), as I have read it is better to do so.  But my problem as of now is just getting the code to work.

[PHP]

JCalc = 1
while JCalc == 1:
    numb1 = input("\nPlease input a number.\n: ")
    
    loop = 1
    while loop == 1:
    
        x = raw_input("\nWhat would you like to do?\n1) Add\n2) Subract\n3) Multipy\n4) Divide\n\
5) Get Answer\n6) Start Over\n7) Quit\n: ")
        if x == "1":
            add_num = input("\nWhat should I add to %s?\n:  " % (numb1))
            numb1 + add_num
        if x == "2":
            sub_num = input("\nWhat should I subtract from %s?\n: " % (numb1))
            numb1 - sub_num
        if x == "3":
            mult_num = input("\nWhat should I multiply %s with?\n: " % (numb1))
            numb1 * mult_num
        if x == "4":
            div_num = input("\nWhat should I divide %s with?\n: " % (numb1))
            numb1 / div_num
        if x == "5":
            print "\n:", numb1
        if x == "6":
            loop = 0
        if x == "7":
            loop = 0
            JCalc = 0

raw_input('Press "enter" to quit')[/PHP]

Edit:  Oh, I think I just found the problem.

Edit: Edit: Yep it worked.  A simple mistake on my part, sorry for wasting forum space.

[PHP]

JCalc = 1
while JCalc == 1:
    numb1 = input("\nPlease input a number.\n: ")
    
    loop = 1
    while loop == 1:
    
        x = raw_input("\nWhat would you like to do?\n1) Add\n2) Subract\n3) Multipy\n4) Divide\n\
5) Get Answer\n6) Start Over\n7) Quit\n: ")
        if x == "1":
            add_num = input("\nWhat should I add to %s?\n:  " % (numb1))
            numb1 = numb1 + add_num
        if x == "2":
            sub_num = input("\nWhat should I subtract from %s?\n: " % (numb1))
            numb1 = numb1 - sub_num
        if x == "3":
            mult_num = input("\nWhat should I multiply %s with?\n: " % (numb1))
            numb1 = numb1 * mult_num
        if x == "4":
            div_num = input("\nWhat should I divide %s with?\n: " % (numb1))
            numb1 = numb1 / div_num
        if x == "5":
            print "\n:", numb1
        if x == "6":
            loop = 0
        if x == "7":
            loop = 0
            JCalc = 0

raw_input('Press "enter" to quit')[/PHP]

---

### Post by dodle on 2008-10-09
Okay, I've tried adding functions to my code but now have a new problem.  Could someone help me fix my error(s)?

[PHP]# JICalc v0.3

# Version Changes: Changed name from JCalc to JICalc; Added functions to the code

def Addition():
    add_loop = 1
    while add_loop == 1:
        try:
            add_num = float(raw_input("\nWhat should be added to %s?\n: " % (numb1)))
            numb1 = numb1 + add_num
            add_loop = 0
        except:
            print "\nPlease use numbers."
    return numb1

def Subtraction():
    sub_loop = 1
    while sub_loop == 1:
        try:
            sub_num = float(raw_input("\nWhat should be subtracted from %s?\n: " % (numb1)))
            numb1 = numb1 - sub_num
            sub_loop = 0
        except:
            print "\nPlease use numbers."
    return numb1

def Multiplication():
    mult_loop = 1
    while mult_loop == 1:
        try:
            mult_num = float(raw_input("By what should %s be multiplied?\n: " % (numb1)))
            numb1 = numb1 * mult_num
            mult_loop = 0
        except:
            print "\nPlease use numbers."
    return numb1

def Division():
    div_loop = 1
    while div_loop == 1:
        try:
            div_num = float(raw_input("By what should %s be divided?\n: " % (numb1)))
            numb1 = numb1 / div_num
            div_loop = 0
        except:
            print "\nPlease use numbers."
    return numb1

def Empezar():
    int_loop = 1
    while int_loop == 1:
        try:
            numb1 = float(raw_input("\nPlease input a number.\n: "))
            int_loop = 0
        except:
            print "\nPlease use numbers."
    return numb1

JICalc = 1
while JICalc == 1:

    Empezar()
    
    loop = 1
    while loop == 1:
    
        x = raw_input("\nWhat would you like to do?\n1) Add\n2) Subract\n3) Multipy\n4) Divide\n\
5) Get Result\n6) Start Over\n7) Quit\n: ")
        if x == "1":
            Addition()
        if x == "2":
            Subtraction()
        if x == "3":
            Multiplication()
        if x == "4":
            Division()
        if x == "5":
            raw_input("\n: result is %s (enter)" % (numb1))
        if x == "6":
            loop = 0
        if x == "7":
            loop = 0
            JICalc = 0

raw_input('Press "enter" to quit')[/PHP]

---

### Post by y-lee on 2008-10-09
Several things wrong with this  code. For one thing in your functions *Addition*, *Subtraction* and so on you are using a variable **numb1** which is not defined in that function. Your *try except* clause is catching the error and your code therefore ends up in an infinite loop. Second of all the same functions should be if they work right returning the value **numb1** but your code is not using this value, same is true of the function *Empezar*.

so to fix this take do something like:
[PHP]JICalc = 1
while JICalc == 1:

    numb1 = Empezar()
    
    loop = 1
    while loop == 1:
    
        x = raw_input("\nWhat would you like to do?\n1) Add\n2) Subract\n3) Multipy\n4) Divide\n\
5) Get Result\n6) Start Over\n7) Quit\n: ")
        if x == "1":
            numb1 = Addition(numb1)
        # and so on[/PHP]

and redo the arithmetic functions like:

[PHP]def Addition(numb1):
    add_loop = 1
    while add_loop == 1:
        try:
            add_num = float(raw_input("\nWhat should be added to %s?\n: " % (numb1)))
            numb1 = numb1 + add_num
            add_loop = 0
        except ValueError:
           print "\nPlease use numbers."
    return numb1[/PHP]

and note for the exception I am catching **only the error** where the user has entered a non number. **Never** just catch all errors like:

[PHP]except:
    # whatever[/PHP]

That is a really bad idea. There are some other issues to with this code, I find the logic  a bit strange and the use of 1 and 0 as booleans I don't care for, nor do i like and long list of if statements like you use, but these are style issues and not actual code errors. So fix the stuff I pointed out above and go on with whatever you are trying to do.

peace

---

### Post by dodle on 2008-10-10
Okay, here is what my code looks like as of now.  Thanks for the help.  I'm trying to get this ready to add a gui to it.  I'm new to programming in general, which is probably very noticeable.  I want to get this ready for a gui, but I'm told it needs a bit more work.  Some guys at [python-forum.org]("python-forum.org") have been helping me too.  Right now I need to get it to where the user can just type in 1 + 1 / 63 and get an answer.  I'm having trouble getting my brain wrapped around this.  Here is my code:[PHP]# JICalc v0.4

# Version Changes: Changed format of loops; "ValueError" added

numb1 = 0

def Addition(numb1):
    add_loop = True
    while add_loop:
        try:
            add_num = float(raw_input("\nWhat should be added to %s?\n: " % (numb1)))
            numb1 = numb1 + add_num
            add_loop = False
        except ValueError:
            print "\nPlease use numbers."
    return numb1

def Subtraction(numb1):
    sub_loop = True
    while sub_loop:
        try:
            sub_num = float(raw_input("\nWhat should be subtracted from %s?\n: " % (numb1)))
            numb1 = numb1 - sub_num
            sub_loop = False
        except ValueError:
            print "\nPlease use numbers."
    return numb1

def Multiplication(numb1):
    mult_loop = True
    while mult_loop:
        try:
            mult_num = float(raw_input("\nBy what should %s be multiplied?\n: " % (numb1)))
            numb1 = numb1 * mult_num
            mult_loop = False
        except ValueError:
            print "\nPlease use numbers."
    return numb1

def Division(numb1):
    div_loop = True
    while div_loop:
        try:
            div_num = float(raw_input("\nBy what should %s be divided?\n: " % (numb1)))
            numb1 = numb1 / div_num
            div_loop = False
        except ValueError:
            print "\nPlease use numbers."
    return numb1

def Empezar(numb1):
    int_loop = True
    while int_loop:
        try:
            numb1 = float(raw_input("\nPlease input a number.\n: "))
            int_loop = False
        except ValueError:
            print "\nPlease use numbers."
    return numb1

JICalc = True
while JICalc:

    numb1 = Empezar(numb1)
    
    loop = True
    while loop:
    
        x = raw_input("\nWhat would you like to do?\n1) Add\n2) Subract\n3) Multipy\n4) Divide\n\
5) Get Result\n6) Start Over\n7) Quit\n: ")
        if x == "1":
            numb1 = Addition(numb1)
        if x == "2":
            numb1 = Subtraction(numb1)
        if x == "3":
            numb1 = Multiplication(numb1)
        if x == "4":
            numb1 = Division(numb1)
        if x == "5":
            raw_input("\n: result is %s (enter)" % (numb1))
        if x == "6":
            loop = False
        if x == "7":
            loop = False
            JICalc = False

raw_input('Press "enter" to quit')[/PHP]

Edit: I see people talking about my "logic" quit a bit, but never completely understand what they are talking about.  Could someone give me an example of my "logic" compared to some that would seem to be more "logical"?

---

### Post by newbuntuxx on 2008-10-10
Not an expert in python scripting (still learning), however, I think you should let the user enter the mathematical expression they want to process (for starters, only allow addition, subtraction, multiplication, and division) as a string. Then you can parse the string, extract the integers with int() and extract the signs. You probably want to use a list to store each character as the pop() and push() methods will be real handy. 

So...this is a rough flow chart....

1. obtain user input
2. read user input until a non-numerical character is found
3. concatenate the characters read so far, use int() to get the integer and push() them into the list
4. push() the sign into the list
5. repeat until the entire expression is exhausted
6. while pushing the signs, you should have a counter to count the number of division/multiplication signs, because they must be done first (remember bedmas? brackets, exponents, division/multiplication, addition/subtraction)
7. now you process the expression. You first check your counter to see if there are any division/multiplication signs, if yes, then you will need to pop the values of the list until you get to the / or X sign, and evaluate it first. Repeat as many times as the number of counts
8. once the value is evaluated, you push it back into the list (or stack)
9. repeat until all values are evaluated. your list should get shorter and shorter. remember not to mess the order of the numbers

to demonstrate it visually, here is an expression

1 + 40 / 4 * 5

put it to the list start with 1, our list will look like:

5
*
4
/
40
+
1
now, our counter should be equal two, as there are two signs that we must evaulate first, so, we pop until the first sign

list.pop() = 5
list.pop() = *5
pop one more 
list.pop() = 4 * 5

our list looks like:
/
40
+
1

evaluate: 4*5 then push it to the list

list.push(20)

our list now is:
20
/
40
+
1

now, one more count that we must look at it, so pop until / or X

list.pop() = 20
list.pop() = /
pop one more
list.pop() = 40

our list looks:
+
1

evaluate 40/20 = 2
push it back

list.push(2)

our list:
2
+
1

now, you can simply push three characters, and evaluate them, since we know we dont have any more divisions/multlipcation signs. 

list.pop() = 2
list.pop() = +
list.pop() = 1
evaluate = 1 + 2 = 3

print result 3

sorry for the detailed post, but as you can see, this is much more user friendly and efficient. If you are successful in implementing this, you can easily add other features like brackets and exponents.

try to implement it...and post what you get....

---

### Post by era86 on 2008-10-10
+1 for above post... this is a good way to understand how infix notation is computed as well.  Try implementing it this way because when you program the GUI later, it will be easier to modify your CLI Calc code for it.

---

### Post by unutbu on 2008-10-10
dodle, as you know, one of the nice things about Python is that it has many high-level tools available. One of these tools is pyparsing. (sudo apt-get install python-pyparsing)

pyparsing simplifies the very difficult problem of parsing user input into tokens.

A simple calculator using pyparsing can be found here: [http://pyparsing.wikispaces.com/Examples](http://pyparsing.wikispaces.com/Examples) . Search for SimpleCalc.py and fourFn.py

Tutorials on how to use pyparsing can be found here:
[http://www.onlamp.com/pub/a/python/2006/01/26/pyparsing.html?page=1](http://www.onlamp.com/pub/a/python/2006/01/26/pyparsing.html?page=1)
[http://rephrase.net/days/07/04/pyparsing](http://rephrase.net/days/07/04/pyparsing) 
/usr/share/doc/python-pyparsing/htmldoc/parserFwk.pyparsing-module.html (after you install python-pyparsing)

Learning pyparsing is not super easy, but mastering this tool can be a great help for your future projects. Learning how to parse input by hand may be a good learning experience too, but in the end for something as complicated as parsing algebraic expressions you'll probably be better off with a parsing tool like pyparsing.

---

### Post by y-lee on 2008-10-10
> **dodle said:**
> Edit: I see people talking about my "logic" quit a bit, but never completely understand what they are talking about.  Could someone give me an example of my "logic" compared to some that would seem to be more "logical"?

Ok i was one of *those people* talking about your logic :) so here goes:

One, your functions Addition Subtraction, Multiplication Division and Empezar all look about the same. Whenever that happens in my code I take it as evidence that really all the similar looking functions are just special cases of the same thing. And then I try to write a more general function that handles all cases.

Two, you have 7 if statements all in a row : 

[PHP]
        if x == "1":
            numb1 = Addition(numb1)
        if x == "2":
            numb1 = Subtraction(numb1)
        if x == "3":
            numb1 = Multiplication(numb1)
        if x == "4":
            numb1 = Division(numb1)
        if x == "5":
            raw_input("\n: result is %s (enter)" % (numb1))
        if x == "6":
            loop = False
        if x == "7":
            loop = False
            JICalc = False[/PHP]

Now I understand the logic of that but I never did care for that kind of programming and try to avoid it.

Three your programming style is straight up procedural. Now I have no issues with [procedural programming]("http://en.wikipedia.org/wiki/Procedural_programming") especially with small  and simple programs. However some might object and if you are going to make a full fledged GUI out of this basic idea you have you will find there are advantages to learning a more [Object Oriented]("http://en.wikipedia.org/wiki/Object-oriented_programming") style of programming. Sometimes however OO programming can add a certain amount of unnecessary complexity to a program, so it depends on the program and it is sort of a judgment call.

However as python supports an object oriented style of coding I would suggest you learn how to use it and I would also suggest you learn programming better before you start trying to write GUI applications.

As to an example of "better logic" at least in my view:

[PHP]#!/usr/bin/env python

# ***************************************************************************
# *   JICalc.py     This is an example of a simple CLI calculator           *
# *                                                                         *
# *   This program is free software with no restrictions whatsoever placed  *
# *     upon it use, misuse, or distribution.                               *
# *                                                                         *
# *   This program is distributed in the hope that it will be useful,       *
# *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
# *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.                  *
# *                                                                         *
# ***************************************************************************

import sys
import operator as op

EMPEZAR = 5
op_instr= [ '\nWhat should be added to %f?\n: ',
            '\nWhat should be subtracted from %f?\n: ',
            '\nBy what should %f be multiplied?\n: ',
            '\nBy what should %f be divided?\n: ',
            '\n: result is %f\n\n  (Press enter) ',
            '\nPlease input a number.\n: ']

def catch_err(func,*arg):
    def wrapper(*arg):
        res = arg[0]
        valid = False
        while not valid:
            try:
                res = func(*arg)
                valid = True
            except ValueError:
                print '\nPlease use numbers.'
                valid = (arg[1] != EMPEZAR + 1)
            except ZeroDivisionError:
                print '\nError: Infinite Result--Division By 0'
                valid = True # Ignore result and continue
        return res
    return wrapper
    
def Empezar(num):
    num = float(raw_input(op_instr[EMPEZAR]))
    return num

def Show(num):
    SHOW = 4
    raw_input(op_instr[SHOW] % (num))
    return(num)

def Quit(num):
    ch = raw_input("Press 'enter' to quit ")
    if len(ch) == 0:
        sys.exit()
    return num
    
def Invalid(num):
    print "\nInvalid choice, please try again\n"
    return num    
    
@catch_err
def Operate(num, x):
    op_lst =[op.add, op.sub,op.mul,op.div, Show, Empezar, Quit, Invalid]
    index = int(x)-1
    arguments = [num]
    if index >= len(op_lst) or index < 0:
        index = len(op_lst) - 1
    elif 0 <= index < 4:
        arguments.append( float(raw_input(op_instr[index] % (num))))
    return op_lst[index](*arguments)
    
def JICalc():
    numb1 = Operate(0, EMPEZAR + 1)
    while True:
        x = raw_input('\nWhat would you like to do?\n1) Add\n2) Subtract\n3)'\
                      ' Multiply\n4) Divide\n5) Get Result\n6) Start Over\n7)'\
                      ' Quit\n: ' )
        numb1 = Operate(numb1,x)

if __name__ == '__main__':
    try:
        JICalc()
    except KeyboardInterrupt:
        sys.stderr.write('\n\nUser Interrupt: exiting ...\n')

# ----- Always look on the bright side of life.  [/PHP]

You should note that I have kept the same basic idea as your original code and also I went with a procedural style of coding. Also note I didn't really comment this code but i certainly would advise it. I simply wanted to keep it short for posting here, also note that python supports [doc strings]("http://diveintopython.org/getting_to_know_python/documenting_functions.html") and they play a role much similar to comments only more useful. So as professors and books are found of saying I leave commenting and adding doc strings to the reader.:lolflag:

Now one thing probably needs clarification and that is the function catch_err and its use 
[PHP]@catch_err
def Operate(num, x):
    # Bunch of code goes here... [/PHP]

This called a [decorator string]("http://wiki.python.org/moin/PythonDecorators") and is a pretty handy trick :) here I use it to simply catch errors and deal with them appropriately. It should however be noted some would say it is preferred to catch input errors by validating input such as with if statements, so keep that in mind. Also note decorator functions like this do have a performance cost and in this case will confuse tools like [pydoc]("http://www.python.org/doc/2.5.2/lib/module-pydoc.html").

However as to the use of tools like pydoc and whatnot we can use pythons decorator module to avoid this problem. So here is version 2 using said module, basically the same code with minor changes:

[PHP]#!/usr/bin/env python

# ***************************************************************************
# *   JICalc.py     This is an example of a simple CLI calculator           *
# *                                                                         *
# *   This program is free software with no restrictions whatsoever placed  *
# *     upon it use, misuse, or distribution.                               *
# *                                                                         *
# *   This program is distributed in the hope that it will be useful,       *
# *   but WITHOUT ANY WARRANTY; without even the implied warranty of        *
# *   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.                  *
# *                                                                         *
# *      Version Changes: added decorator module to preserve signature      *
# *                       of orginal function and play nicely with pydoc    *  
# ***************************************************************************

import sys
import operator as op
try:
    from decorator import decorator
except ImportError:
    print "Import Error: requires decorator module."
    print "\t http://pypi.python.org/pypi/decorator/2.2.0"
    sys.exit(0)
    
EMPEZAR = 5
op_instr= [ '\nWhat should be added to %f?\n: ',
            '\nWhat should be subtracted from %f?\n: ',
            '\nBy what should %f be multiplied?\n: ',
            '\nBy what should %f be divided?\n: ',
            '\n: result is %f\n\n  (Press enter) ',
            '\nPlease input a number.\n: ']

def catch_err(func, *arg, **kw):
    res = arg[0]
    valid = False
    while not valid:
        try:
            res = func(*arg)
            valid = True
        except ValueError:
            print '\nPlease use numbers.'
            valid = (arg[1] != EMPEZAR + 1)
        except ZeroDivisionError:
            print '\nError: Infinite Result--Division By 0'
            valid = True  # Ignore result and continue
    return res

def Empezar(num):
    num = float(raw_input(op_instr[EMPEZAR]))
    return num

def Show(num):
    SHOW = 4
    raw_input(op_instr[SHOW] % (num))
    return(num)

def Quit(num):
    ch = raw_input("Press 'enter' to quit ")
    if len(ch) == 0:
        sys.exit()
    return num
    
def Invalid(num):
    print "\nInvalid choice, please try again\n"
    return num    
    
@decorator(catch_err)
def Operate(num, x):
    op_lst =[op.add, op.sub,op.mul,op.div, Show, Empezar, Quit, Invalid]
    index = int(x)-1
    if index >= len(op_lst) or index < 0:
        index = len(op_lst) - 1
    arguments = [num]
    if 0 <= index < 4:
        arguments.append( float(raw_input(op_instr[index] % (num))))
    return op_lst[index](*arguments)

def JICalc():
    numb1 = Operate(0, EMPEZAR + 1)
    while True:
        x = raw_input('\nWhat would you like to do?\n1) Add\n2) Subtract\n3)'\
                      ' Multiply\n4) Divide\n5) Get Result\n6) Start Over\n7)'\
                      ' Quit\n: ' )
        numb1 = Operate(numb1,x)

if __name__ == '__main__':
    try:
        JICalc()
    except KeyboardInterrupt:
        sys.stderr.write('\n\nUser Interrupt: exiting ...\n')

# ----- Always look on the bright side of life.[/PHP] 

Both these examples should work ok but *I make no promises* :) I wrote them quickly and only briefly tested them and then tested only on python 2.4. Also note in both examples I am making use of 2 global variables, something some would say to avoid. But i feel it is appropriate here to keep the logic simple and besides I can always fall back on the as professors and books are found of saying *I leave eliminating these global variables to the reader.* :lolflag:

And so I hope you have found this to be somewhat educational **dodle** and not terribly confusing. It might not be apparent but I have made *an effort* to keep the code as simple as possible and resisted the temptation "*to be clever*".

peace.

---

### Post by dodle on 2008-10-11
@ newbuntuxx:  Thanks, I'll give your suggestions a go.  I haven't used push() or pop() yet (takes a while for my brain to absorb things).  

Thank you everyone for being so helpful.  I wanted to show you a new script to compare it with my old one and see if anybody thought it was better, not any better, or waaay worse.[PHP]# JICalc v0.6

# Version Changes: Complete revamp of system; After operator is found,
#  arithmetic sequence is looked for
# Bugs: Will not work for more than one operator; Spaces cause an unaccepted
#  sequence

loop_master = True
while loop_master == True:
    acuire_loop = True
    while acuire_loop == True:
        value = raw_input("\nType an arithmetic sequence\n: ")
        if value == "quit":
            loop_master = False
            acuire_loop = False
        elif value.split('+'):
            try:
                print "\n%s" % (float(value[0]) + float(value[2]))
                acuire_loop = False
            except:
                print "\nsequence not accepted"
        elif value.split('-'):
            try:
                print "\n%s" % (float(value[0]) - float(value[2]))
                acuire_loop = False
            except:
                print "\nsequence not accepted"
        elif value.split('*') or value.split('x'):
            try:
                print "\n%s" % (float(value[0]) * float(value[2]))
                acuire_loop = False
            except:
                print "\nsequence not accepted"
        elif value.split('/'):
            try:
                print "\n%s" % (float(value[0]) / float(value[2]))
                acuire_loop = False
            except:
                print "\nsequence not accepted"
[/PHP]

P.S. Thanks for being patient with me too.

Edit:  Is my code messy?

Edit:  Edit:  I just noticed there is something really wrong with this.  The only equation that works is addition.

Edit:  Edit: Edit: Okay, this isn't working at all.

---

### Post by artir on 2008-10-11
I tried to do sth like this and I created THE PYCULATOR!
RIght now, it just identifies the input, you can type 432431+43242 and it will say "432431" "+" "43242"
I'm to lazy to implement the functions; but here is the code_

[PHP]#!/usr/bin/python
#Licensed under GPL v3
#Created by Artir
# THE PYCULATOR! v 0.1
# Let's make an uber calculator
#What should it be able to do: 1 and 2 grade equations. Equation systems, standard operations,anything!
#Why? To learn python, of course!
#Changelog: 
#V0.1 : Acepts numbers+operation(*,+,/,-)+ numbers syntax i.E     333+4 or  5*6     . Prints numbers at right of the operation, then the operation and then the numbers at left.
global operacion
print "THE PYCULATOR! v 0.1"
print "Author: Artir (put your name here if ya helped)"
numbers=["1","2","3","4","5","6","7","8","9","0"]
operations=["/","*","+","-"]
def minimenu():
      global entrada
      entrada=raw_input(">> ")
     
      splitter()
    



def splitter():
    
    
    
    global procesar
    
    procesar=[]
    for i in range(0,len(entrada)):
        procesar.append(entrada[i])
    
    del i
    parser()



def parser():
    arguments=0
    global cuenta
    cuenta=""
    for i in procesar:
        if arguments==1:
            cuenta=""
        if i in numbers:
         cuenta=cuenta+i
         
        elif i in operations:
            print cuenta
            if i =="+":
                 #global operacion
                 operacion="+"
                 arguments=+1
                 print "+"
            elif i=="-":
                #global operacion
                operacion="+"
                arguments=+1 
                print "-"
            elif i=="/":
               # global operacion
                operacion="/"
                arguments=+1
                print "/"
            elif i=="*":
             #global operacion
             operacion="*"
             arguments=+1
         
             print "*"
              
    print cuenta        
minimenu()


        
    [/PHP]

The trick is to take the input as a string

---

### Post by dodle on 2008-10-11
I'm going to do some studying up on the "for" and "in" statements, 'cuz I'm seeing a lot of that in others' code.  I'm also going to do some studying up on OO programming, since my miniature brain can't comprehend it.  If anybody would like to give some input on those subjects, I would appreciate it.

---

### Post by LaRoza on 2008-10-11
> **dodle said:**
> I'm going to do some studying up on the "for" and "in" statements, 'cuz I'm seeing a lot of that in others' code. 

A for loop is a handy way of iterating.

Try the following:
```

names = ["LaRoza","CptPicard","pmasiar", "mssever", "tinny"]
for name in names:
    print name

```

---

### Post by dodle on 2008-10-11
> **LaRoza said:**
> A for loop is a handy way of iterating.

Try the following:
```

names = ["LaRoza","CptPicard","pmasiar", "mssever", "tinny"]
for name in names:
    print name

```

I've seen a lot of people put:[PHP]for i in list:
  print i[/PHP]But you don't have to put "i" do you?  Whatever value you put is assigned to list/tuple?

---

### Post by OutOfReach on 2008-10-11
you can put any letter even words. It's just like assigning variables

like:
```
for x in whatever:
```
or
```
for hello in something_here:
```

---

### Post by LaRoza on 2008-10-11
> **dodle said:**
> I've seen a lot of people put:[PHP]for i in list:
  print i[/PHP]But you don't have to put "i" do you?  Whatever value you put is assigned to list/tuple?

for [variable] in [iterable object]

You can name variables anything you want. For readability sake, the names should make sense. Like "for line in open("file")".

i is often used as a counter number for looping in C, but since the Python for loop does that automatically, there is no need.

JavaScript:
```

for (var i = 0; i < names.length; i++)
{
    print(names[i]);
}

```

Python:
```

for name in names:
    print name

```

for loops are usually used to iterate over arrays, and the Python for loop is built for that.

---

### Post by ghostdog74 on 2008-10-12
> **dodle said:**
> I've seen a lot of people put:[PHP]for i in list:
  print i[/PHP]But you don't have to put "i" do you?  Whatever value you put is assigned to list/tuple?

if your primary purpose is to display list items only, then no need for loop
```

print list

```
otherwise, use the for loop for further one by one custom processing.

---

### Post by dodle on 2008-10-12
Ma brain's gonna 'splode

---

### Post by newbuntuxx on 2008-10-17
ok....they should have explained to you how it actually works..and what it does....unlike other languages, in python when you write a loop like this:

for i in list:
   print i

this actually means:
take the first item in (list) and put it in i, loop
take the second item in (list) and put it in i, loop
take the third item in (list) and put it in i, loop
.
.
.
take the last item in (list) and put it in i, loop
end

thats what "for i in list" means.

if you used other langauges, then what is really familiar to you is the following:

for i in range(1,10):
   print i

it will print the numbers 1 to 9 (note it will not print 10). so, essentially, it goes from 1 to 9 and at each number, it assigns it to i and loops etc...

this is similar to java, c, c++ (the classical languages basically) where you write (and correct my syntax)

i = 1;
for (i; i <10; i++)
   {
     print i;
   }

python is just too hight level (a very good thing). it makes use of in, is, and other human readible operators. Coming from a java, C background, i definitly feel python's breeze

---

### Post by newbuntuxx on 2008-10-17
hey....

i was working on Artir code, but didn't finish (i am at work, alas).

Here is what I got though. I fixed the splitter function and wrote the main algorithem for poping and pushing. It works only for multiplication, you can just duplicate the same code for the other operators. Of course the main algorithem needs to be placed into its own function. 



```
#!/usr/bin/python 
#Licensed under GPL v3 
#Created by Artir 
# THE PYCULATOR! v 0.1 
# Let's make an uber calculator 
#What should it be able to do: 1 and 2 grade equations. Equation systems, standard operations,anything! 
#Purpose: To learn Python
#Changelog:  
#V0.1 : Accepts any input, provided that the operators [+,-,*,/] are not placed at the start or the end of the line
## And provided that every operator is separated by a number

print "THE PYCULATOR! v 0.5" 
print "Author: Artir, newbuntuxx (Insert your name here if you helped)"

numbers=["1","2","3","4","5","6","7","8","9","0"] 
operators=["/","*","+","-"] 
def minimenu(): 
      global input_s 
      input_s =raw_input(">> ") 
      splitter()


def splitter(): 
    global equation
    c_str = ""
    equation=[]
    for i in input_s: 
        if i in numbers:
            c_str = c_str + i
        if i in operators:
            equation.append(c_str)
            equation.append(i)
            c_str = ''
    equation.append(c_str)
    parser() 


def parser():
    temp = []
    temp1 = 0
    temp2 = 0
    i = 0
    counter = equation.count('*') + equation.count('/')
    print counter
    while counter != 0:
       temp.append(equation.pop())
       if temp[-1] is "*":
            temp.append(equation.pop())
            temp1 = int(temp.pop())
            gar = temp.pop() #this is garbage
            temp2 = int(temp.pop())
            equation.append(temp1*temp2)
            counter = counter - 1
    print equation
                            
##def calc(temp[],counter):

##    temp.append(equation.pop())
##    if temp[-1] is "*":
##    temp.append(equation.pop())
##    temp1 = int(temp.pop())
##    gar = temp.pop() #this is garbage
##    temp2 = int(temp.pop())
##    equation.append(temp1*temp2)
##    counter = counter - 1
##        
    

minimenu()
```

---

