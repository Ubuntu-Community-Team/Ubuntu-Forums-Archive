---
title: "Python not working correctly in Windows..please help"
date: 2007-03-03
forum: Programming Talk
---

### Post by billdotson on 2007-03-03
I am on a computer running Windows XP and it has those user accounts setup. As it is not my computer I do not have administrative access I cannot edit system files. The odd thing though is I clicked on the Python installer and it installed, although I cannot get it to run any program I create. Here is one of my sample programs.


```
 
p = input( "What is your initial investment (input a number)?" , ) 
r = input( "What is your rate of interest?" , ) 
t = input( "How many years will your money be invested?" , ) 
n = input( "How many interest payments do you receive a year (how many compounding periods)?" , ) 
money = p + (1+((r/100)/n)**(n*t)) 
print money

```

when I open the DOS shell I do the following:

dir C:\py*

c:\Python25\python

then type exit() in the Python interpreter because Ctrl + Z + Enter does not work.

Then if I type python interest.py (my interest application) it just drops down a line and doesn't aska question and just has a blank line to enter the input. It does this until the inputs are done and then it just goes back to the C:\> and doesn't return the answer.
If I just double click on the .py file it oepns it ina terminal and shows the input questions but then after the final one is answered the terminal just closes.

I was thinking I needed to add Python to my autoexec.bat to make it work correctly but I am not sure.
 
Can anyone help as I want to be able to continue Python until I get my computer back.

---

### Post by marianom on 2007-03-03
Do you have Python in your PATH? If it's not there, add it and restart the machine.

---

### Post by billdotson on 2007-03-03
how do I add it to my PATH, it is something to do with autoexec.bat isn't it?

---

### Post by pythonbite77 on 2007-03-03
Right-click My Computer -->Properties -->Advanced --> Environment variables, go to 'system variables' and then 'path', click on edit and add the location of the python exe to the end of your current path in the variable value box. Click OK.

---

### Post by billdotson on 2007-03-03
do I add C:\Python25\python.exe to the path or add just C:\Python25\ ?? as I have added C:\Python25\python.exe and it is still doing the same thing.  my python program is on the desktop.  thanks

---

### Post by ghostdog74 on 2007-03-04
you just add c:\python2.5 to your path. no need to include python.exe

---

### Post by billdotson on 2007-03-04
so here is my "finished" program.  

```

p = input( "What is your initial investment (input a number) ?" , )
r = input( "What is your rate of interest (Example: for 5.75% interest rate enter 5.75)?" , )
t = input( "How many years will your money be invested?" , )
n = input( "How many interest payments will you receive a year (compounding interest payments) ?" , )
i = r/100.0
#print p
#print r
#print t
#print n
#print i
money = float (p * (1+(i/n))**(n*t))
print
print "So after a period of" , t ,"year/years" , " with your original investment of $" , p , "gaining at an interest rate of" , r , "% will have $" , money
print "So in" , t , "years you have gained $" , money - p

```

Does that look pretty good?  The only thing I need to do is somehow tell the string up decimals to round up to 2 decimal places since it is money.  Also are there any other things I could do to make the code shorter? (the commented print statementsm when uncommented are to check values of the variables if something in the program isn't calculating something correctly)

---

### Post by Tuna-Fish on 2007-03-05
First things first: Money is NEVER calculated as floating point. This has led to serious issues in real life. While it is not really a big issue for this kind of programs, better get the basics straight. The correct way is to use an integer type, count pennies and turn it into a float and divide by 100 just before printing output. Every time you divide integers, remember to add the modulo (the % operator) if appropriate. You don't ever round money, just just count it at the right precision.

Second, using input() is not smart, as one can just type python code in it. Rather, use:
name_of_variable = int(raw_input(message))

This is again not much of a concern if the recipient of the program can be expected not to abuse it, but it is more professional.

---

### Post by Tuna-Fish on 2007-03-05
oh, and remember that python has a cool and reasonably fast arbitrary-precision integer type:
a = long(raw_input())
can store as long numbers as your ram can take, so you don't have to worry about overflowing.

---

### Post by billdotson on 2007-03-05
tuna-fish you just absolutely confused me to death.. I have only been learning Python for 3 days now and that just fried my brain..  :confused:

---

### Post by Tuna-Fish on 2007-03-05
oops. sorry :(

---

### Post by billdotson on 2007-03-05
could you please explain what you mean and how to go about using the raw_input in the program? I would like to understand your reasons for using raw_input() as opposed to just using input() and how to set it up like that.

---

### Post by pmasiar on 2007-03-05
> **billdotson said:**
> could you please explain what you mean and how to go about using the raw_input in the program? I would like to understand your reasons for using raw_input() as opposed to just using input() and how to set it up like that.

did you tried to read documentation? Build-in functions are documented here:
[http://docs.python.org/lib/built-in-funcs.html](http://docs.python.org/lib/built-in-funcs.html)

input(  	[prompt]):     Equivalent to eval(raw_input(prompt)). 
raw_input(  	[prompt]):     If the prompt argument is present, it is written to standard output without a trailing newline. The function then reads a line from input, converts it to a string (stripping a trailing newline), and returns that. 

raw_input() returns string. 
input() returns number, if you entered number; variable, if you entered name of variable. It evaluates entered expression.

If you dont know what "evaluate" means, either read it up, or don't use it - use raw_input instead, which most likely does what you want anyway.

Wikibooks has excellent online book about Python and all this is explained in great detail:

[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Who_Goes_There%3F](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Who_Goes_There%3F)

---

### Post by Tuna-Fish on 2007-03-06
To simplify it, try this at the python parser:
>>> import sys
>>> a = input('this is dangerous! > ',)
this is dangerous! > sys.exit()

You can give python commands into input() and it'll execute them. Imagine having a python script that evaluates some input from someone on the web and the guy gives commands to delete everything in your home dir.

---

### Post by billdotson on 2007-03-06
yeah that would suck.  So if I wanted to get it the way you suggested where raw_input() was used so only numbers and such could be entered there and to get the money thing set up so it is not a floating point how would I go about it?  And I understand that this is my first simple program and that these things don't really matter as of right now but later on they would.

Btw when would it be useful to use input() over raw_input()?

so if I did that above
import sys
and then entered sys.exit() it would shut down my system or something?

---

