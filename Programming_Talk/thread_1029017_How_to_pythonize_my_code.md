---
title: "How to pythonize my code?"
date: 2009-01-03
forum: Programming Talk
---

### Post by jseiser on 2009-01-03
I learned to program using .net languages in school.  I am trying to learn python and I am just writing simple little things to try and learn.  I just want to know how I can better call my functions, or better yet, actually use classes.

here is my code for a simple script that asks for 2 numbers, and then displays them added, subtracted, multiplied and divided.  its nice and simple, but I would much rather have it call my functions properly, I feel like I have them nested and that it isnt the proper way to do this.

I call the numbers()  first, which then calls the quit function, which then calls the triggers function which calls all the other functions then prints out the answers.  It seems like you would actually want to just call

if __name__ == "__main__":
    numbers()
    quit()
    trigger()
    add()
    subtract()
    multiply()
    divide()
    printstr()


I guess I am just looking for input on how a python programmer would go about writing this.  Am I making to much work out of it with all the functions or should I try writing in a object oriented way and use classes?  Classes are something I struggled with in school :(

```

#!/usr/bin/env python

#
# Programming Challenge simple calculator
#

import sys
#!/usr/bin/env python

#
# Programming Challenge #5 (game)
#

import sys

def add(a,b):
    """ Adds 2 numbers that are passed to it"""
    added = (a + b)
    return added
    
def subtract(a,b):
    """ Subtracts 2 numbers that are passed to it """
    subtracted = (a - b)
    return subtracted
    
def multiply(a,b):
    """ multiplies 2 numbers that are passed to it"""
    multiplied = (a * b)
    return multiplied
    
def divide(a,b):
    """ divides 2 numbers that are passed to it"""
    divided = (a / b)
    return divided
    
def numbers():
    """gets to numbers from the user"""
    print ("Type quit to exit")
    num1 = raw_input(" Please give me a number: ")
    quit(num1)
    num2 = raw_input(" Please give me a number: ")
    quit(num2)
    num1 = int(num1)
    num2 = int(num2)
    trigger(num1,num2)
    
def trigger(num1,num2):
    tempadd = add(num1,num2)
    tempsubtract = subtract(num1,num2)
    tempmultiply = multiply(num1,num2)
    tempdivide = divide(num1,num2)
    print " *********************************** \n"
    print str(num1) + " + " + str(num2) + " = " + str(tempadd)
    print str(num1) + " - " + str(num2) + " = " + str(tempsubtract)
    print str(num1) + " * " + str(num2) + " = " + str(tempmultiply)
    print str(num1) + " / " + str(num2) + " = " + str(tempdivide)
    
def quit(test):
    if test == "quit":
        sys.exit()
    

if __name__ == "__main__":
    numbers()
def add(a,b):
    """ Adds 2 numbers that are passed to it"""
    added = (a + b)
    return added
    
def subtract(a,b):
    """ Subtracts 2 numbers that are passed to it """
    subtracted = (a - b)
    return subtracted
    
def multiply(a,b):
    """ multiplies 2 numbers that are passed to it"""
    multiplied = (a * b)
    return multiplied
    
def divide(a,b):
    """ divides 2 numbers that are passed to it"""
    divided = (a / b)
    return divided
    
def numbers():
    """gets to numbers from the user"""
    print ("Type quit to exit")
    num1 = raw_input(" Please give me a number: ")
    quit(num1)
    num2 = raw_input(" Please give me a number: ")
    quit(num2)
    num1 = int(num1)
    num2 = int(num2)
    trigger(num1,num2)
    
def trigger(num1,num2):
    tempadd = add(num1,num2)
    tempsubtract = subtract(num1,num2)
    tempmultiply = multiply(num1,num2)
    tempdivide = divide(num1,num2)
    print " *********************************** \n"
    print str(num1) + " + " + str(num2) + " = " + str(tempadd)
    print str(num1) + " - " + str(num2) + " = " + str(tempsubtract)
    print str(num1) + " * " + str(num2) + " = " + str(tempmultiply)
    print str(num1) + " / " + str(num2) + " = " + str(tempdivide)
    
def quit(test):
    if test == "quit":
        sys.exit()
    

if __name__ == "__main__":
    numbers()

```

---

### Post by pp. on 2009-01-03
First of all, your problem is a bit on the simple side. In fact, it is so simple that it's difficult to see any advantages Object Oriented Programming might have.

Still, just to answer your question:

Your sample problem consists four "things" which have similar features. Those "things" are the four basic calculator operations ***addition***, ***subtraction***, ***multiplication***, ***division***. 

Those are some of the features:
Each operation 
[LIST]
[*]has a name (addition, subtraction, multiplication, division).
[*]corresponds to a verb (add, subtract, multiply, divide).
[*]has a nick name (plus, minus, times, by)
[*]is denoted by a special character in a formula (+, -, *, /)
[/LIST]

Also, all of the operations can be applied to a pair of numbers. The results of applying the operation to two numbers varies from operation type to operation type. Also, for some of the operations the order of the numbers matters. There even are operations which do not accept numbers which are accepted by the other operations.

So, you might want to define a class called MathematicalOperation with the following instance variables:
- name
- verb
- nick
- characterInFormula
- function

The variables ***name***, ***verb***, ***nick*** and ***characterInFormula*** are just strings; they correspond to the features mentioned above. Please realise that I have introduced a few variables which you do not use in your original "problem".

The variable ***function*** would be used to hold a function which applies the operation implied by the object to two numbers. The use of lambda functions comes to mind.

Once you have defined your class MathematicalOperation, you start your program by defining all desired operations, placing those objects in a collection of some sort and running your tasks through the collection of MathematicalProblems: printing the op code, printing the op as formula, evaluating and printing the result.

---

### Post by catchmeifyoutry on 2009-01-03
You're making this WAAAY to complicated (you come from a .net background you say?). Oh, now I see that you copy pasted the code twice, I thought it looked like complete overkill with redefined functions :p.

Still, this is not a complicated task, I wouldn't define litter the code with functions which contain about two statements (depends on the situation though). You can use lambda functions if necessary.
Also, distrust the user input some more, it could be anything.

My hacksel:
[PHP]
#!/usr/bin/env python

if __name__ == "__main__":

    # loop forever
    while True:

        try:
            # try to get two integers
            num1 = int(raw_input(" Please give me a number: "))
            num2 = int(raw_input(" Please give me another number: "))

        except:
            # illegal input, quit (break while True loop)
            print 'quiting'
            break

        # define all four (binary) operators on the two numbers
        funcs = [
            ('+', lambda x,y: x + y),
            ('-', lambda x,y: x - y),
            ('*', lambda x,y: x * y),
            ('/', lambda x,y: float(x) / y),
        ]

        print " ***********************************"
        for func in funcs:
            op = func[0] # the operator sign to print to output
            result = func[1](num1, num2) # calculate the result
            print '%d %s %d = %s' % (num1, op, num2, result)
        print " ***********************************"
        print
[/PHP]

---

### Post by ghostdog74 on 2009-01-03
actually, there is even no need to create your own operator functions. Use the operator module. It has add, subtract, etc already defined.
```

>>> import operator
>>> operator.add(10,1)
11

```

---

