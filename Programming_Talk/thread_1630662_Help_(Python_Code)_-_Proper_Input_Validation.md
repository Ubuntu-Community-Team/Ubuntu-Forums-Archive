---
title: "Help (Python Code) - Proper Input Validation"
date: 2010-11-25
forum: Programming Talk
---

### Post by banditkeef on 2010-11-25
I'm trying to figure out a way to prevent my program from crashing when using string input where a numeric input belongs, i know i can change it to a raw_input instead of a input and put ' before and after the number but that doesn't store the numeric value for continues loops... like if i had a raw_input instead of an input and i put down 1000 then added 100 it would come up 1000100. Here is a brief something of what I'm doing.

#module to add a expense
def addExpense(totalBudget):
    -expense = 0
    -frequency = 0
    -totalExpense = 0
    
    -expense = input('Enter the amount of the expense that you want to add: $')
    -while expense < 0:
       --print 'Error: Your expense cannot be less than 0.'
        --expense = input('Enter the correct amount: $')

    -frequency = input('Enter how many times a month the expense is paid: ')
    -while frequency < 0:
        --print 'Error: Your frequency of payment cannot be less than 0.'
        --frequency = input('Enter the correct amount: ')

    -totalExpense = expense * frequency

    -if totalBudget >= totalExpense:
        --totalBudget = totalBudget - totalExpense
        --budgetAmount = totalBudget
        --print 'Your expense amount was excepted, your current amount is $', totalBudget
    -else:
        --print 'Your expense was rejected do to insufficient funds, please try again.'
    -return totalBudget

im using the - to hold my indent, its not actually in my code.

---

### Post by fly-by-night on 2010-11-25
Tough one.:D  Ask a mod to move it here:

Programming talk
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Edit:  Click on the exclamation mark (Report Post) [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] next to your post, to ask a mod to move it.

---

### Post by The Cog on 2010-11-25
Moved to programming talk.

You can highlight code and click the # code button in the advanced editor when entering code into the forum.

You could try something like:
```

    txt = input('Enter how many times a month the expense is paid: ')
    try:
        frequency = int(txt)
    except:
        frequency = 0
    while frequency <= 0:
        print 'Error: Frequency of payment must be a number greater than 0.'
```
EDIT:
No, that's not going to work - it'll loop forever if they get it wrong. Maybe:
```

    frequency = 0
    while frequency <= 0:
        txt = input('Enter how many times a month the expense is paid: ')
        try:
            frequency = int(txt)
        except:
            print 'Error: Frequency of payment must be a number greater than 0.'
```

---

### Post by banditkeef on 2010-11-25
no, your on the right track.

ill play with a little bit more but this is what i got when i entered your bottom input





Enter your total budget amount for the month: $1000
Menu Selection
1 - Add an Expense
2 - Remove an Expense
3 - Add Revenue
4 - Remove Revenue
5 - Exit
Enter your selection: 1
Enter the amount of the expense that you want to add: $100
Enter how many times a month the expense is paid: n

Traceback (most recent call last):
  File "/Volumes/KMS FLASH/Personal Budget Program.py", line 150, in <module>
    main()
  File "/Volumes/KMS FLASH/Personal Budget Program.py", line 38, in main
    totalBudget = addExpense(totalBudget)
  File "/Volumes/KMS FLASH/Personal Budget Program.py", line 66, in addExpense
    frequency = input('Enter how many times a month the expense is paid: ')
  File "<string>", line 1, in <module>
NameError: name 'n' is not defined

---

### Post by banditkeef on 2010-11-25
wait i have an idea...

would it be possible to make the frequency variable a raw_input
then after you input the amount....,
set the frequency variable to turn into a numeric assignment instead of a string?

---

### Post by TheWeakSleep on 2010-11-26
I think if you just used

```
spam = int(raw_input("prompt: "))
```it should work, shouldn't it? As far as I know, input() treats anything as a valid python statement, which is why it is telling you that name 'n' is not defined.

EDIT: Though I'm still new to python, so don't take my word for it, try it out for yourself :)

---

### Post by StephenF on 2010-11-26
> **TheWeakSleep said:**
> I think if you just used

```
spam = int(raw_input("prompt: "))
```it should work, shouldn't it? As far as I know, input() treats anything as a valid python statement, which is why it is telling you that name 'n' is not defined.

EDIT: Though I'm still new to python, so don't take my word for it, try it out for yourself :)
```

>>> int("r")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'r'

```
How about no.

---

### Post by Vox754 on 2010-11-26
> **StephenF said:**
> ```

>>> int("r")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'r'

```
How about no.

Actually, yes. That is the correct solution.

Of course, you still need to catch the exception.
```

try:
    spam = int(raw_input("prompt: "))
    print("Integer")
except(TypeError, ValueError):
    print("Not an integer")

```

All people reading this, get this straight: "input()" was a mistake in Python 2, and it should never be used. In Python 3, "input()" behaves like Python 2 "raw_input()", and conversion to an integer, float or other data type must be done explicitly.

Read the manual: [2. Built-in Functions](http://docs.python.org/library/functions.html#input)

Some info on validation: [Dealing with User Input in Python](http://linuxgazette.net/issue83/evans.html)

The proposal to let (the new) "input()" exist as a built-in: [PEP 3111 -- Simple input built-in in Python 3000](http://www.python.org/dev/peps/pep-3111/)

Python's creator, Guido van Rossum, originally didn't want to deprecate (the old) "input()": [[Python-Dev] deprecate input()?](http://lfw.org/python/pydev-sample/msg00206.html)

Of course, whenever you read threads or posts, look at the date first, some things change.

---

### Post by banditkeef on 2010-11-26
yeah that worked, but i need it to hold a real number not a integer.

like 103.**

Enter your total budget amount for the month: $1000
Menu Selection
1 - Add an Expense
2 - Remove an Expense
3 - Add Revenue
4 - Remove Revenue
5 - Exit
Enter your selection: 1
Enter the amount of the expense that you want to add: $100
Enter how many times a month the expense is paid: 1
Your expense amount was excepted, your current amount is $ 900
Menu Selection
1 - Add an Expense
2 - Remove an Expense
3 - Add Revenue
4 - Remove Revenue
5 - Exit
Enter your selection: 1
Enter the amount of the expense that you want to add: $1.95

Traceback (most recent call last):
  File "/Volumes/KMS FLASH/Personal Budget Program.py", line 147, in <module>
    main()
  File "/Volumes/KMS FLASH/Personal Budget Program.py", line 38, in main
    totalBudget = addExpense(totalBudget)
  File "/Volumes/KMS FLASH/Personal Budget Program.py", line 61, in addExpense
    expense = int(raw_input('Enter the amount of the expense that you want to add: $'))
ValueError: invalid literal for int() with base 10: '1.95'
>>> 

I'm sure i can figure it out from here, thanks for pointing me in the right directions.

---

### Post by TheWeakSleep on 2010-11-26
> **StephenF said:**
> ```

>>> int("r")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'r'

```How about no.

I'm sorry, I should have been more descriptive in what I was trying to tell you to try. I assumed you knew to use a try...except as it was in the post before mine. I will try to be more helpful next time. As for your 'real number' issue, could you not use float() instead of int()?

---

