---
title: "Confused by error in python"
date: 2008-08-06
forum: Programming Talk
---

### Post by Retaliation on 2008-08-06
Hi,

I am new to python and programming in general, and just recently installed Ubuntu. I'm just messing around with python using DrPython and while I was testing some of my code, I got an error message. Here is my code so far:

[PHP]loop = 1

while loop == 1:

    print "info"
    print "info"
    print " "
    print "info"
    print "info"
    print "info"
    print "info"
    print "info"
    
    choice = raw_input("Enter the name you would like to obtain detailed info on: "
    if choice == choice1:
        print "blah blah"
        print "blah blah"
        print "blah blah,"
        print "blah blah"
        print " "
        print "End info"
        loop = 0
        [/PHP]

When I try to save or run the script, it gives me a syntax error:

[PHP]compile:
invalid syntax (Test.py, line 15)


Traceback (most recent call last):
  File "/usr/bin/drpython", line 641, in CheckSyntax
    compile(ctext, fn, 'exec')
<type 'exceptions.SyntaxError'>: invalid syntax (Test.py, line 15)[/PHP]



Line 15 is the 'if choice == choice1' bit.

Could anyone give any insight to this problem? I have looked at other code to try and distinguish what the problem is, but I haven't noticed anything. I'm assuming it's some sort of typing or indenting error because the error says invalid syntax, but I'm just not sure. Thanks in advance

---

### Post by Def13b on 2008-08-06
Never take syntax error locations on face value, always look at the preceding line or lines as well to make sure they're also correct.

In this case the error is with the assignment to the choice variable.

If you open a door, make sure you close it behind you.

---

### Post by Torajima on 2008-08-06
You didn't define the variable named choice1.

Unless it's text, then it should be "choice1"

---

### Post by nvteighen on 2008-08-06
> **Retaliation said:**
> 
[PHP]
    choice = raw_input("Enter the name you would like to obtain detailed info on: "
[/PHP]

You have a typo there: you have to close the parenthesis.

---

### Post by Malac on 2008-08-06
Yeh Looks like you are missing a bracket on the end of the line.

---

### Post by Retaliation on 2008-08-06
Ah, thank you, I'm not sure how I missed the closing parentheses. It is still giving me the error message though, even after correcting it. Any other ideas?

P.S. And Torajima, it is text.

---

### Post by catchmeifyoutry on 2008-08-06
> **Retaliation said:**
> Ah, thank you, I'm not sure how I missed the closing parentheses. It is still giving me the error message though, even after correcting it. Any other ideas?

P.S. And Torajima, it is text.

So did you also fix the "choice1" answer, which should be text as Torajima suggested?
Your code contained two bugs which both resulted, by coincidence, in an error in the same line:
1) the closing parentheses
2) choice1 is interpreted as an (unknown, thus illegal) variable, change it to a string.

With those two lines corrected, the complete code becomes:
[PHP]
loop = 1

while loop == 1:

    print "info"
    print "info"
    print " "
    print "info"
    print "info"
    print "info"
    print "info"
    print "info"
    
    choice = raw_input("Enter the name you would like to obtain detailed info on: ")
    if choice == "choice1":
        print "blah blah"
        print "blah blah"
        print "blah blah,"
        print "blah blah"
        print " "
        print "End info"
        loop = 0  
[/PHP]

which works on my computer.

Best.

---

### Post by days_of_ruin on 2008-08-06
> **Retaliation said:**
> Hi,

I am new to python and programming in general, and just recently installed Ubuntu. I'm just messing around with python using DrPython and while I was testing some of my code, I got an error message. Here is my code so far:

[PHP]loop = 1

while loop == 1:

    print "info"
    print "info"
    print " "
    print "info"
    print "info"
    print "info"
    print "info"
    print "info"
    
    choice = raw_input("Enter the name you would like to obtain detailed info on: "
    if choice == choice1:
        print "blah blah"
        print "blah blah"
        print "blah blah,"
        print "blah blah"
        print " "
        print "End info"
        loop = 0
        [/PHP]

When I try to save or run the script, it gives me a syntax error:

[PHP]compile:
invalid syntax (Test.py, line 15)


Traceback (most recent call last):
  File "/usr/bin/drpython", line 641, in CheckSyntax
    compile(ctext, fn, 'exec')
<type 'exceptions.SyntaxError'>: invalid syntax (Test.py, line 15)[/PHP]



Line 15 is the 'if choice == choice1' bit.

Could anyone give any insight to this problem? I have looked at other code to try and distinguish what the problem is, but I haven't noticed anything. I'm assuming it's some sort of typing or indenting error because the error says invalid syntax, but I'm just not sure. Thanks in advance

This isn't where the error is but there is a simpler way to print the
same thing multiple times:```
print "hello\n" * 10
```

That will print "hello" ten times, each time on a different line.

---

### Post by Retaliation on 2008-08-06
> **catchmeifyoutry said:**
> So did you also fix the "choice1" answer, which should be text as Torajima suggested?
Your code contained two bugs which both resulted, by coincidence, in an error in the same line:
1) the closing parentheses
2) choice1 is interpreted as an (unknown, thus illegal) variable, change it to a string.

With those two lines corrected, the complete code becomes:
[PHP]
loop = 1

while loop == 1:

    print "info"
    print "info"
    print " "
    print "info"
    print "info"
    print "info"
    print "info"
    print "info"
    
    choice = raw_input("Enter the name you would like to obtain detailed info on: ")
    if choice == "choice1":
        print "blah blah"
        print "blah blah"
        print "blah blah,"
        print "blah blah"
        print " "
        print "End info"
        loop = 0  
[/PHP]

which works on my computer.

Best.


Ah, thank you. This is what all the trouble was. Thanks again!

---

