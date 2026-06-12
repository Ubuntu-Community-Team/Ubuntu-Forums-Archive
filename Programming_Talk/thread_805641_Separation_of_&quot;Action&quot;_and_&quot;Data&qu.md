---
title: "Separation of &quot;Action&quot; and &quot;Data&quot; classes"
date: 2008-05-24
forum: Programming Talk
---

### Post by Xavieran on 2008-05-24
Hello All,

I have decided to do a complete rewrite (generally) of my pyBank program and am thinking that maybe I should separate my base BankAccount class into BankAccount and BankAccountOperations.

Is that confusing? ;)

Here is the code and I will try to explain what I mean.

```
#!/usr/bin/env python
'''Module for the manipulation and creation of bank accounts'''
__author__ = "Emmanuel Jacyna"
__copyright__ = "Copyright 2008 Emmanuel Jacyna"
__license__ = "GPL"
__version__ = "0.3"
__maintainer__ = "Emmanuel Jacyna"
__email__ = "xavieran_lives@yahoo.com.au"
__status__ = "Prototype"
__TODO__= '''Must figure out md5crypt.\nMust use the getpass module.\n'''
import time,os,sys,getpass
class BankAccount:
    '''A bank account class for manipulating bank accounts'''
#self.interest,self.logfile?
    def __init__(self,balance,name,password):
        self.balance=balance
        self.name=name
        self.password=password
    def logrecord(self,record):
        '''call logrecord to write self.record.For writing logs'''
        logfile=open("/home/%s/.pyBank/Logs/%s-log"%(os.getlogin(),self.name),'a')
        logfile.write(record)
        logfile.close()
        account=open("/home/%s/.pyBank/Accounts/%s"%(os.getlogin(),self.name),"w")
#This is the special format used by my account files
        account.write('''StartName %s StartBalance %f StartPass %s'''%(self.name,self.balance,self.password))
        account.close()

    def Withdraw(self,withdrawal):
        '''Withdraws money from current bank account'''
        self.balance -= withdrawal
        self.logrecord('''%s -- Withdrew $%f from %s -- 
$%f\n'''%(str(time.gmtime()[:6]),withdrawal,self.name,self.balance))

    def Deposit(self,deposit):
        '''Deposits money in the current bank account.'''
	self.balance += deposit
        self.logrecord('''%s -- Deposited $%f to %s -- $%f\n'''%(str(time.gmtime()[:6]),deposit,self.name,self.balance))

    def Transfer(self,amount,receiver):
        '''Transfers money between accounts'''
        self.balance -= amount
        receiver.balance += amount
	self.logrecord('''%s -- Transferred $%f to %s -- %f'''%(str(time.gmtime()[:6]),amount,receiver.name,self.balance))
	

```

I am wondering whether I should separate logrecord(),Withdraw(),Deposit() and Transfer() into a separate class or just as plain functions of the module.

Thankyou in advance! :)

---

### Post by Majorix on 2008-05-24
I have never seen Data and Action classes for the same class, but there is no reason why you shouldn't try it.

---

### Post by Xavieran on 2008-05-24
I have separated the "actions" as actions in the module and this seems clearer and easier to use for me.

New Code
```
#!/usr/bin/env python
'''Module for the manipulation and creation of bank accounts'''
__author__ = "Emmanuel Jacyna"
__copyright__ = "Copyright 2008 Emmanuel Jacyna"
__license__ = "GPL"
__version__ = "0.3"
__maintainer__ = "Emmanuel Jacyna"
__email__ = "xavieran_lives@yahoo.com.au"
__status__ = "Prototype"
__TODO__= '''Must figure out md5crypt.\nMust use the getpass module.\nMust add letters instead 
of numbers.\nMust make a config.\nMust add arg support.\nMust network it.\nMust separate BankAccount() and Menus()'''
import time,os,sys,getpass
class BankAccount:
    '''A bank account class for manipulating bank accounts'''
#self.interest,self.logfile?
    def __init__(self,balance,name,password):
        self.balance=balance
        self.name=name
        self.password=password

def logrecord(account,record):
    '''Call logrecord with the BankAccount class object and the record forr it'''
    logfile=open("/home/%s/.pyBank/Logs/%s-log"%(os.getlogin(),account.name),'a')
    logfile.write(record)
    logfile.close()
    accountfile=open("/home/%s/.pyBank/Accounts/%s"%(os.getlogin(),account.name),"w")
#This is the format used by my account files
    accountfile.write('''StartName %s StartBalance %f StartPass %s'''%(account.name,account.balance,account.password))
    accountfile.close()

def Withdraw(account,withdrawal):
    '''Withdraws money from current bank account'''
    account.balance -= withdrawal
    #logrecord('''%s -- Withdrew $%f from %s -- 
#$%f\n'''%(str(time.gmtime()[:6]),withdrawal,account.name,account.balance))

def Deposit(account,deposit):
    '''Deposits money in the current bank account.'''
    account.balance += deposit
    #logrecord('''%s -- Deposited $%f to %s -- $%f\n'''%(str(time.gmtime()[:6]),deposit,account.name,account.balance))

def Transfer(account,amount,receiver):
    '''Transfers money between accounts'''
    account.balance -= amount
    receiver.balance += amount
    #logrecord('''%s -- Transferred $%f to %s -- %f'''%(str(time.gmtime()[:6]),amount,receiver.name,account.balance))

if __name__=="__main__":
    Emmanuel=BankAccount(50.00,"Emmanuel","e")
    print Emmanuel.name,Emmanuel.password,Emmanuel.balance
    Deposit(Emmanuel,10.00)
    print Emmanuel.balance
```

Now, to BankErrors;)

---

### Post by dwhitney67 on 2008-05-24
Xavieran, the title of your thread piqued my interest, and I am curious as to why you thought it was advantageous to stray away from an OO design, where data objects and operations (methods) were encapsulated together in a single class, and break these into a design where they are not?

I've looked at the before and after versions of the code, and other than for the lack of vertical white-space to separate sections of the code, I cannot understand why you found the first version hard to understand.

The difference appears to be tab-spaces, and the use of 'self' in lieu of 'account' in the methods.  That doesn't seem like a big deal to grasp.

I can think of one reason why the actions you did are not wise.  For instance, if you needed to create a sub-class of the original BankAccount to model a SavingsAccount, where deposits to an account would yield an interest bonus for each deposit.  Your Deposit() method does not offer this feature.

Perhaps also, there could be an account that charges fees after the third withdrawal within a month.  Let's call this the PoorManAccount.  Your Withdraw() method does not handle this particular feature for this type of account.

So how would you account for these example functionalities I have mentioned?  Would you create additional methods, using unique names?

Anyhow, I hope that with the simple examples I provided above, you will appreciate the advantages of OOD, and understand that the original design, is better than the design you have chosen.  With a sub-class, all one has to do is override (redefine functionality) of existing methods in the base-class to meet the specific needs of the sub-class.  Generic methods would remain the same.

Here's a web-page with some more [interesting reading]("http://www.freenetpages.co.uk/hp/alan.gauld/tutclass.htm") that further expands on what I have presented.

Cheers.

---

### Post by Xavieran on 2008-05-24
You have made some good points and I will try to answer them (and please remember that I am new to programming.

I felt that I needed to take a step back (not backwards ;)) and look at my code again.
I actually had printed out a copy of my original design and put notes on what I could improve, but it had strayed so far from my original design for a Bank Account system that I was getting confused as to what was part of BankAccounts and what needed to be gotten rid of (I had been designing a UI to use pyBank with instead of actually fleshing out the class).
I have moved things to get back to the original design idea and will probably move the actions into an inheriting sub-class of BankAccount.

Thanks for your advice, I really appreciate it. :)

---

### Post by CptPicard on 2008-05-24
Actually, separating data from action is not *that* strange. Model-View-Controller does that all the time, and sometimes it can be advantageous to have a data class to be just a representation of a data item.

It all depends on whether the actions are truly *intrinsic* to the object, or whether they are "external" to the object... sort of have an existence of their own, and could maybe be extended and overridden to take different kinds of data items. In the latter case it may be wise to do what you're doing.

Interestingly, I tend to more and more believe that OOD sucks, and that encapsulation just tends to create non-extensible systems where there are limits to what you can do that you must then work around through all sorts of OOD patterns.

Languages like Common Lisp do their "OOP" system completely differently. Data items are genuinely data items, and functions on the data items are then overridden to obtainspecializations for different parts of an inheritance hierarchy (and even completely different hierarchies, and combinations of different kinds of objects, etc)... IMO this is the Right Way to Do it, and just a few nights back I watched the creator of Clojure, Rich Hickey, describe how his Java had essentially migrated away from OOP where data and code are combined into where his classes no longer contained any data, and just had like 27 different static methods that did "functional programming in Java"...

---

### Post by Xavieran on 2008-05-24
Nice to see different opinions on my question :D

I have decided to include the functions in the main BankAccount class and have created the exceptions and an inherited class MultipleAccount that supports having more than one "account" to a name.The new code is here:

```
#!/usr/bin/env python
'''Module for the manipulation and creation of bank accounts.\n'''
__author__ = "Emmanuel Jacyna"
__copyright__ = "Copyright 2008 Emmanuel Jacyna"
__license__ = "GPL Version 2"
__version__ = "0.3"
__maintainer__ = "Emmanuel Jacyna"
__email__ = "xavieran_lives@yahoo.com.au"
__status__ = "Prototype"
__TODO__= '''Think!'''
class BankError(Exception):
    message="Problem with input:%s"
class BankAccount:
    '''A base bank self class for keeping base information on bank accounts'''
#self.interest,self.logfile?

    def __init__(self,balance,name,password):
        self.balance=balance
        self.name=name
        self.password=password


    def Withdraw(self,amount):
        '''Withdraws money from current bank account'''
        if amount > self.balance or "-" in str(amount):
            raise BankError,BankError.message%"Cannot withdraw more than you have."
        else:
            self.balance -= amount

    def Deposit(self,deposit):
        '''Deposits money in the current bank account.'''
        if "-" in str(amount):
            raise BankError,BankError.message%"Cannot deposit a negative amount"
        self.balance += deposit
        
    def Transfer(self,receiver,amount):
        '''Transfers money between accounts'''
        if amount > self.balance or "-" in str(amount):
            raise BankError,BankError.message%"Cannot transfer negative amounts."
        else:
            try:
                self.balance-=amount
                receiver.balance+=amount
            except TypeError:
                acctno=int(raw_input("%s's account no. to transfer to\n>"%receiver.name))
                receiver.balance[acctno]+=amount
        
        
class MultipleAccount(BankAccount):
    '''A sub-class of BankAccount that can be used to hold multiple balances, or, accounts to the same name'''
    
    def Withdraw(self,amount,acctno):
        if amount > self.balance or "-" in str(amount):
            raise BankError,BankError.message%"Cannot withdraw more than you have or a negative amount."
        else:self.balance[acctno]-=amount
        
    def Deposit(self,amount,acctno):
        if "-" in str(amount):
            raise BankError,BankError.message%"Cannot deposit a negative amount"
        self.balance[acctno]+=amount
        
    def Transfer(self,receiver,amount,acctno):
        '''Accepts an extra argument, the account no of the account to withdraw from.'''
        if amount > self.balance or "-" in str(amount):
            raise BankError,BankError.message%"Cannot transfer more than you have or negative amounts."
        else:
            try:
                self.balance[acctno]-=amount
                receiver.balance+=amount
            except TypeError:
                acctno=int(raw_input("%s's account no. to transfer to\n>"%receiver.name))
                receiver.balance[acctno]+=amount

if __name__=="__main__":
    Emmanuel=BankAccount(100.00,"Emmanuel","e")
    Other=BankAccount(1000.00,"Other","e")
    print "Starting balance for Emmanuel:",Emmanuel.balance
    Emmanuel.Withdraw(50.00)
    print "Withdrew $50.00 from Emmanuel",Emmanuel.balance
    print "Others balance:",Other.balance
    try:Other.Withdraw(-500.00)
    except BankError:print "action cannot be completed"
    print "Emmanuel's balance:",Emmanuel.balance
    Emmanuel.Withdraw(20.0)
    print "Withdrew $20.00 from Emmanuel",Emmanuel.balance,"\nBegin MultipleAccount Demo"
    JJ=MultipleAccount({1:90.00,2:80.00},"JJ","jj")
    print "JJ's balances in his two accounts:",JJ.balance,
    Jj=MultipleAccount({1:35.00,2:35.00,3:673.00},"Jj","JJ")
    print "Jj's balances in his accounts:",Jj.balance
    JJ.Withdraw(23.00,1)
    print "Withdrew 23.00 from JJ's acount no.1.\nCurrent Balance:",JJ.balance[1]
    print "Transferring money between MultipleAccount()'s"
    JJ.Transfer(Jj,23.00,1)
    print Jj.balance[2]
    print JJ.balance
```

---

### Post by dwhitney67 on 2008-05-24
Looks good... however feel free to embellish the code with some vertical white-space (i.e. carriage returns) to make it more readable.  The code all runs together from start-to-finish... makes it hard to read.  My $0.02 of advice.

---

### Post by Xavieran on 2008-05-24
By the way, is there a way to clear the screen in python?
Short of os.system("clear")?

---

### Post by lisati on 2008-05-24
Reading through the discussion I spotted something called "Transfer". Not having had any relevant experience with OOP-based design I was wondering which object the transfer class would belong to, the source account or the destination account? Or possibly both in some fashion? Perhaps my ignorance of this design technique was playing tricks with my imagination....

---

### Post by Xavieran on 2008-05-24
> Reading through the discussion I spotted something called "Transfer". Not having had any relevant experience with OOP-based design I was wondering which object the transfer class would belong to, the source account or the destination account? Or possibly both in some fashion? Perhaps my ignorance of this design technique was playing tricks with my imagination....

Transfer is a method (function) of the class BankAccount, it would have to belong to the source account and not the destination account or the destination could withdraw money from the source account by "requesting" money.This is also why I have put a BankError when someone uses a negative number as the argument for amount.

Was that confusing? ;)

---

### Post by dwhitney67 on 2008-05-24
A money transfer occurs from one account (i.e. self) to another account (BankAccount).

The method should (unless you subscribe to Pickard's viewpoint) reside inside the BankAccount class.

The "self" (a BankAccount object) is no different from the other account receiving the funds.  Xavieran has defined the Transfer() method correctly in his post.  I have not looked at the implementation, but I'm sure it is correct too.

---

### Post by CptPicard on 2008-05-24
> **Xavieran said:**
> 
I have decided to include the functions in the main BankAccount class and have created the exceptions and an inherited class MultipleAccount that supports having more than one "account" to a name.

This breaks a pretty significant rule of OOD and inheritance... since when does it hold that a set-of-accounts "is-an" account? A child in a hierarchy should be substitutable for a parent, and I have a bad feeling you're breaking something in the conceptual model here.

Also, regarding "transfer", it should perhaps still be a bit more clear what the direction of transfer is... something like Account.transferFrom(Account to).

An interesting way to think of transfer as a separate process is if you think that usually there is more involved in doing transfers... you want transactional support and maybe some kind of logging and reporting. Stuffing that inside your "Account" encapsulates quite a lot inside a class that is supposed to just represent an Account. 

The Common Lisp Object System (CLOS) would approach this differently. It would have a "transfer function" that takes two accounts, and then there would be multiple-dispatch specializations for all sorts of accounts. In addition, the nice :before and :after methods allow you to tag all sorts of preconfiguration and cleanup actions onto your main method.

Python allows similar decoupling of methods from objects... that's what the explicit self parameter is there for. I actually didn't like the "self" before understanding its use -- the ability to just take any function and use it for a method (or not, if you don't want to) can be very nice.

---

### Post by Xavieran on 2008-05-24
Set of accounts is hard to explain,and I should find a better word, but think of it like this...

John has an account with his local bank under the name John.
He also has a savings account under the same name.
He may get a loan from his bank,and then,he will get a loan account...

They are just ways to organise your money, under the same password...

About the logging...I have decided that that can be taken care of by a program using pyBank as a module.You don't usually build exception handling in the sense of "except BankError:next loop" into a module either and it would be more flexible as to what could be logged if that was built in to the program using pyBank.
Which is what I have designed it to be like in the first place.

I really cannot see what is so confusing about Transfer(self,receiver,amount) especially if it was being used in a client program in the form of:

Welcome to your account.
T) Transfer Money between accounts
W) Withdraw Money from your account
L) Log Out

I will try and make the documentation a bit better also...

---

### Post by dwhitney67 on 2008-05-24
Essentially there is no right or wrong way to do things.  Whatever works to accomplish the goal at hand is probably an acceptable solution.  Many s/w weenies try to overcompensate with wild solutions to an otherwise simple problem.

Frankly, it really doesn't matter whether one solves a problem with an OO design or not.  It's the non-techies that are footing the bill.  Does anyone think they really care how the task is accomplished?  Only those that are idiot-savants think that OO is the only approach... "gotta have that reusable code!"... which, for those who have years of experience, know that it will never be used again because the next project will employ a different language/technology, or will cut into their employment lifespan.

-- "Deep Thoughts" from a pessimistic s/w weenie.

---

### Post by CptPicard on 2008-05-24
You are very correct in considering this whole reusability potential suspect. It is my own personal experience that in particular inheriting functionality is really dangerous unless you really know for sure in advance that requirements will not change even a single bit.

The problem is that first you create this wonderful architecture where you remove duplication of functionality as tightly as you possibly can, and then imagine your code is reusable... then comes this some new requirement you didn't  foresee, and all of a sudden, your architecture doesn't *quite* fir the picture. Now, you can't *really* reuse code, but you need to go back to your architecture and redesign parts of it to be applicable... and guess what?

*Now you have to rewrite your original, other project too unless you want to fork the whole codebase*.

---

### Post by Xavieran on 2008-05-24
Well, my pyBank program is just to teach myself basic concepts of OOP and programming (note.*very* basic :)).
It is useful in the sense that I could make a GTK interface to it or make it networkable, but it is definitely a learning work...

Thanks for your help and encouragement CptPicard and dwhitney67.
It really was quite useful!

:)

---

### Post by Xavieran on 2010-04-23
Wow.

I posted this three years ago, and boy was I ignorant. Since then I've learned LISP, figured out what I actually want to do with my life in computer science, and actually understand what the two repliers were talking about. I just want to say a big thanks to all the people on this forum for helping me get to the stage where I can read SICP, and actually understand it (should have started it those three years ago ;)

---

