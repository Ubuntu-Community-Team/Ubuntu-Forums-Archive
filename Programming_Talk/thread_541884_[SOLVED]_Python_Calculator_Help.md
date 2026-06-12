---
title: "[SOLVED] Python Calculator Help"
date: 2007-09-03
forum: Programming Talk
---

### Post by boopyg on 2007-09-03
-

---

### Post by fredscripts on 2007-09-03
I'm not very good on programming, but why do you put one < 'm' instead of one == 'm'? (and so with the other operations)

```
one = raw_input("Multiplication, Subtraction, Division or Addition?|m,s,d,a|: ")
a = input("Enter a number: ")
b = input("Enter another number: ")
a = int(a)
b = int(b)
if one == 'm': 
 print '%s multiplied by %s equal %s' %(a, b, a*b)
if one == 's':
 print '%s subtracted by %s equal %s' %(a, b, a-b)
if one == 'd':
 print '%s divided by %s equal %s' %(a, b, a/b)
if one == 'a':
 print '%s added by %s equal %s' %(a, b, a+b)

```

On the other hand, I think it's better do this with the switch case stuff (python works with "elif",[http://www.java2s.com/Code/Python/Language-Basics/ifStatementsifelifandelse.htm](http://www.java2s.com/Code/Python/Language-Basics/ifStatementsifelifandelse.htm)), and also you don't need to cast to int the values. Furthermore, take a look at the "eval" python function, which could simplify this code. ([http://www.java2s.com/Code/Python/Application/Asimplecalculator.htm](http://www.java2s.com/Code/Python/Application/Asimplecalculator.htm))

---

### Post by boopyg on 2007-09-03
-

---

### Post by PenguinMafia on 2007-09-03
Keep in mind on the result of a division will be truncated how it's coded now (could cast a float() to one of the numbers)

if you wanted to run this from the shell you could create a symbolic link and put it into the /usr/bin dir

thinking about it more if all you wanted was a quick calculator in bash you could install calc or apcalc (which symbolically links to calc) through the universe repos.

```

sudo apt-get install apcalc

```

and you use it like this:

```

calc 21/4
        5.25

```

---

### Post by boopyg on 2007-09-03
-

---

### Post by nanotube on 2007-09-03
i understand that you're just doing it for practice...
but if you want a calculator, just use python itself. here's an interactive python shell that does some calculations:
```
>>> 2*2
4
>>> 4/8.0
0.5
>>> 2**3
8
>>> 5+9
14
>>> 

```

in other words... python /is/ a calculator. :)

---

### Post by boopyg on 2007-09-03
-

---

### Post by nanotube on 2007-09-03
> **boopyg said:**
> Nanotube, I would've used that ecxept I dont want to type python in the terminal everytime.

well... when you use your program, don't you have to type the name of your program in the terminal every time? unless the name of your program is something like "a", it can't be that much faster to start it up than python :)

also, you can
```
alias a='python'
```
in your .bashrc, and start python with "a" ;)

and of course, you can create an icon on your desktop or on the panel to start it, as well.

so... bad excuse :)

not that any of this has any relevance, since you're just doing it for practice... but there it is. :)

---

### Post by boopyg on 2007-09-03
-

---

### Post by boopyg on 2007-09-03
-

---

### Post by nanotube on 2007-09-03
you want the operations to also take place conditional on how many numbers. so indent those once further. 

(not that the whole thing is elegant, but for learning purposes...)

```
one = raw_input("Multiplication, Subtraction, Division or Addition?|m,s,d,a|: ")
one = one
n = input("How many numbers to you want?|2, 3|: ")
n = int(n)
if n == 2:
  a = input("Enter a number: ")
  b = input("Enter another number: ")
  a = int(a)
  b = int(b)
  if one == "m": 
    print '%s multiplied by %s equal %s' %(a, b, a*b)
  if one =='s':
    print '%s subtracted by %s equal %s' %(a, b, a-b)
  if one == 'd':
    print '%s divided by %s equal %s' %(a, b, a/b)
  if one == 'a':
    print '%s added by %s equal %s' %(a, b, a+b)
if n == 3:
  a = input("Enter a number: ")
  b = input("Enter another number: ")
  c = input("And your third: ")
  c = int(c)
  a = int(a)
  b = int(b)
  if one == "m": 
    print '%s multiplied by %s multiplied by %sequal %s' %(a, b, c, a*b*c)
  if one =='s':
    print '%s subtracted by %s subtracted by %s equal %s' %(a, b, c, a-b-c)
  if one == 'd':
    print '%s divided by %s divided by %sequal %s' %(a, b, c, a/b/c)
  if one == 'a':
    print '%s added by %s added by %s equal %s' %(a, b, c, a+b+c)

```

now, here's your next task: reduce code duplication; support variable number of numbers.
some hints:
did you know that you can input lists directly, separated by commas?
did you know that you can apply an operation to an entire list at once?
look up the function "reduce". 
also watch out for float vs int division.

have fun. :)

---

### Post by gnuman on 2007-09-03
[Post removed--as it was big and nanotube beat me to it anyway :-)]

---

### Post by gnuman on 2007-09-03
I played around with your program a little.  

Try this:

```
from __future__ import division

one = raw_input("Multiplication, Subtraction, Division or Addition?|m,s,d,a|: ")

n = int(input("How many numbers to you want?|2, 3|: "))

if n == 2:
    a = int(input("Enter a number: "))
    b = int(input("Enter another number: "))

    if one == "m": 
        print '%s multiplied by %s equals %s' %(a, b, a*b)
    elif one =='s':
        print '%s subtracted by %s equals %s' %(a, b, a-b)
    elif one == 'd':
        print '%s divided by %s equals %s' %(a, b, a/b)
    elif one == 'a':
        print '%s added by %s equals %s' %(a, b, a+b)
    else:
        print "ERROR, I expected m,s,d or a !"
if n == 3:
    a = int(input("Enter a number: "))
    b = int(input("Enter another number: "))
    c = int(input("And your third: "))

    if one == "m": 
        print '%s multiplied by %s multiplied by %sequals %s' %(a, b, c, a*b*c)
    elif one =='s':
        print '%s subtracted by %s subtracted by %s equals %s' %(a, b, c, a-b-c)
    elif one == 'd':
        print '%s divided by %s divided by %sequals %s' %(a, b, c, a/b/c)
    elif one == 'a':
        print '%s added by %s added by %s equals %s' %(a, b, c, a+b+c)
    else:
        print "ERROR, I expected m,s,d or a !"
raw_input("Press Enter to Exit this Program")
```

Some of the changes:

1.  Convert to and integer in the same step.
2.  Division gives the expected answer, using the __future__ module
3.  You had to indent those blocks that I indented, as you only want them to apply if the condition (ex. "If n==3") is met.
4.  I used a better way to end the program.  "end" is not a python word.

Hope this helps.

---

### Post by andyrobo60 on 2007-09-03
sorry someone replayed faster than me.

---

### Post by fredscripts on 2007-09-04
I repeat that you should take a look at the eval function...

```
while True:
    expression = raw_input("Enter an expression to be calculated(Enter to exit): ")
    if not expression: break
    try:
        aux = eval(expression)
        print "The result is: ",aux
    except:
        print "Bad expression..."

```

---

### Post by dwblas on 2007-09-04
Just use a list to store the numbers:```
one = raw_input("Multiplication, Subtraction, Division or Addition?|m,s,d,a|: ")
done=0
nums_list = []
while not done:
    n =raw_input("Integer number or just <Enter> to exit ")
    if (len(n) > 0) and (n.isdigit()):  ## or some terminating character wasn't entered
      nums_list.append( int(n) )
    else :
       done=1
print "nums_list =", nums_list     ## just FYI
if one == "m": 
   print "%d" %(nums_list[0]),   
   total=nums_list[0]
   for num in range( 1, len(nums_list) ):
      print "multiplied by %d" %(nums_list[num]),  ## print each number in the list
      total *= nums_list[num]                      ## multiply total by each number in the list
   print "equals %d" % (total)
```

etc for addition, subtraction, and division.  You could also come up with one generic function to do the calcs based upon what was passed to it, m or a or d or s, but this is enough for one day.  Also please clean up the code where you can. "Enter to exit"???

---

### Post by boopyg on 2007-09-04
-

---

### Post by nanotube on 2007-09-04
well, i wanted to wait before posting any "pythonic" code, so that you have a chance to play around for yourself... but since others were not so patient... well, here's my version of a calculator that does what yours does:

```
from operator import mul, sub, div
sum = lambda x, y: x+y
what = raw_input('enter what you want to do [m, s, d, a]: ')
oper = {'m': mul, 's': sub, 'd':div, 'a': sum}[what]
valuelist = input('enter your numbers, separated by comma: ')
valuelist = map(float, list(valuelist))
print 'The result of operation is ', reduce(oper, valuelist)
```

and here's a sample session using it:
```
$ python testcalc.py 
enter what you want to do [m, s, d, a]: a
enter your numbers, separated by comma: 4, 5, 56
The result of operation is  65.0
$ python testcalc.py 
enter what you want to do [m, s, d, a]: m
enter your numbers, separated by comma: 5, 7, 8
The result of operation is  280.0
$ python testcalc.py 
enter what you want to do [m, s, d, a]: m
enter your numbers, separated by comma: 3, 4, 5, 59, 34
The result of operation is  120360.0

```

notice that there are no for loops or any kind of loops anywhere - python understands lists pretty well so that you can avoid them - note the use of map and reduce. note also the use of input rather than raw_input, which allows us to get the list of numbers directly in one input line.

note also the little dictionary trick that acts as a "switch-case" type of deal - something that would otherwise be 4 different 'ifs'. 

have fun. :)

---

