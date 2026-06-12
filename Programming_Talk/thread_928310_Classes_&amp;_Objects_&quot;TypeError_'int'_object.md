---
title: "Classes &amp; Objects: &quot;TypeError: 'int' object is not callable&quot;"
date: 2008-09-23
forum: Programming Talk
---

### Post by azurepancake on 2008-09-23
I've been spending some time with programming objects and classes in Python. Wanting to dabble a little bit more, I decided to make a simple ATM simulation program. With this program, you can view, make a withdrawal or deposit to your bank account. 

Heres the code. 

```

# create class
class Bank(object):

    def __init__(self, total):
        self.total = total
        print "\nYour new bank account has been created, with a total of", self.total, "dollars.\n"

    def money(self):
        print "\nYou have", self.total, "dollars in the bank.\n"
        
    def withdrawl(self):
        self.withdrawl = int(raw_input("\nHow much money would you like to withdrawl?: "))
        if self.withdrawl < self.total:
            self.total -= self.withdrawl
        else:
            print "\nYou only have", self.total, "in the bank. You can't withdrawl", self.withdrawl, "dollars.\n"
        
            
bank1 = Bank(1000)

print \
    """
    Welcome to 'My Bank'
    
    1 - To view bank account.
    2 - To make withdrawl.
    3 - To make deposit.
    4 - To quit.
    """
choice = None
while choice != 4:
    choice = int(raw_input("\nChoice: "))
    if choice == 1:
        bank1.money()
    elif choice == 2:
        bank1.withdrawl()
    elif choice == 3:
        print "This feature yet to be implemented."

print "Good-bye."

```

To me, this program looks like it should work. But, being new to classes, I have a feeling I'm quite wrong.. 

Here is how the program crashes:

```

tristan@panzerkunst:~/projects/python/practice$ python object1.py

Your new bank account has been created, with a total of 1000 dollars.


    Welcome to 'My Bank'
    
    1 - To view bank account.
    2 - To make withdrawl.
    3 - To make deposit.
    4 - To quit.
    

Choice: 1

You have 1000 dollars in the bank.


Choice: 2

How much money would you like to withdrawl?: 100


Choice: 1

You have 900 dollars in the bank.


Choice: 2
Traceback (most recent call last):
  File "object1.py", line 36, in <module>
    bank1.withdrawl()
TypeError: 'int' object is not callable


```

I tried looking up this particular TypeError, but couldn't find how it relates to my program. Does anyone know what my mistake in the code is?

Thanks in advanced!

---

### Post by azurepancake on 2008-09-23
Hmm, well it seems I fixed the issue. This is the second time I've done this and my apologies if it appears I keep making wasteful posts. Sometimes if I don't finish a problem before I hit the sack, I can't sleep.. ;)

Here is the modified code, that works:

```

# create class
class Bank(object):

    def __init__(self, total):
        self.total = total
        print "\nYour new bank account has been created, with a total of", self.total, "dollars.\n"

    def money(self):
        print "\nYou have", self.total, "dollars in the bank.\n"
        
    def withdrawl(self, total_withdrawl):
        self.total_withdrawl = total_withdrawl
        if self.total_withdrawl < self.total:
            self.total -= self.total_withdrawl
        else:
            print "\nYou only have", self.total, "in the bank. You can't withdrawl", self.total_withdrawl, "dollars.\n"
        
            
bank1 = Bank(1000)

print \
    """
    Welcome to 'My Bank'
    
    1 - To view bank account.
    2 - To make withdrawl.
    3 - To make deposit.
    4 - To quit.
    """
choice = None
while choice != 4:
    choice = int(raw_input("\nChoice: "))
    if choice == 1:
        bank1.money()
    elif choice == 2:
        total_withdrawl = int(raw_input("\nHow much money would you like to withdrawl?: "))
        bank1.withdrawl(total_withdrawl)
    elif choice == 3:
        print "This feature yet to be implemented."

print "Good-bye."

```

The big difference here obviously, is that the client code defines the with-drawled amount and sends it through the parameter. Then, in the method it assigns self.total_withdrawl the value of total_withdrawl.

I still don't understand how this fixed the issue though. I just found that this works by pure experimentation.

Any thoughts. It will be much appreciated!

---

### Post by dwhitney67 on 2008-09-24
The reason why the code in your OP failed was because you were trampling over the class' withdrawl [sic] method when you performed the assignment of the raw input.

Change the variable name to something other than withdrawl, and it should work.  And btw, you do not need to make a local variable a class variable.

In other words, if you had done this:
[PHP]    def withdrawal(self):
        amount = int(raw_input("\nHow much money would you like to withdraw?: "))
        if amount < self.total:
            self.total -= amount
        else:
            print "\nYou only have", self.total, "in the bank. You can't withdrawl", amount, "dollars.\n"[/PHP]

Btw, I corrected the spelling of withdrawl to be withdrawal.


P.S.  Your second solution is more elegant; it separates the application controller from the application model (Bank object).  I recommend you stick with it.  The comments above were merely given so that you understand the bug in your original code.

P.S.S.  Your opening comment in the file (create class) is incorrect.  You are defining the class, not creating it.  When you instantiate 'bank1' at a later time, then you are creating a class object.

---

### Post by gomputor on 2008-09-24
And you don't have to use raw_input() and convert it to int if you want to get arithmetic values.

Just use input() instead:
[COLOR="Blue"]input("\nHow much money would you like to withdrawl?: ")[/COLOR]

---

### Post by azurepancake on 2008-09-24
Ahh.. So THAT is how you spell 'withdrawal'! ;)

Thanks a lot for clearing up my confusion and misconceptions!

---

