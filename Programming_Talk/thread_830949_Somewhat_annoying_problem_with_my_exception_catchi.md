---
title: "Somewhat annoying problem with my exception catching - python"
date: 2008-06-16
forum: Programming Talk
---

### Post by Xavieran on 2008-06-16
Hello All,

I am writing my pyBank programs command line user interface, and have come across an annoying problem, either with my code (most likely) or with python.

Basically,
I have a try statement which encapsulates the logging in part of my program, and the except catches KeyErrors in the dictionary used to store the user data.

The problem is that ,for example, if the Transfer function get's a KeyError, it is caught by the topmost except statement, and the user is brought back to the main menu.

I hope that makes sense...

Code below:

[PHP]#!/usr/bin/python
from pickle import *
from getpass import getpass
import pyBank,time,os,sys,md5
#System variables or options can go here
DIR="/home/%s/"%os.getlogin()+"Code/"
#Some basic functions
def pickle(mode,data='',file="AcctData.pk"):
    '''Small wrapper for the pickle library to dump or load a pickled object'''
    if mode == "dump":
        picdump=open("%s"%DIR+file,"w")
        dump(data,picdump)
        picdump.close
    elif mode == "load":
        picload=open("%s"%DIR+file,"r")
        data=load(picload)
        picload.close()
	return data
    else: return "Invalid mode given"

def clear():
    os.system("clear")

def CreateUser():
    #These are simply the arguments for a BankUser object
    name=raw_input("UserID\n>")
    password=getpass("Password\n>")
    balance=float(raw_input("Balance for account\n>"))
    #Make sure no one tries to make trouble for us.
    if "-" in str(balance):
        raise pyBank.BankError,pyBank.BankError.message%"Cannot start an account with a negative amount."
    clear()
    DATA[name]=pyBank.BankUser({
                                "General":balance
                                },name,password)
    DATA[name+"-log"]="Account created %s with balance %f"%(time.asctime(),balance)
    #Write out the new account to the file.
    pickle("dump",DATA)
def Authenticator(password):
    userpass=getpass()
    if userpass != password:
        return 0
    if userpass == password:
        return 1
try:
    DATA=pickle("load")
except IOError:DATA={}
    
while 1:
    clear()
    prompt=raw_input("c) Create User\nl) Login\nq) Quit\n>")
    if prompt == "c":CreateUser()
    if prompt == "q":raise SystemExit
    if prompt == "l":
        UserId=raw_input("UserID:")
        try:
            if Authenticator(DATA[UserId].password) == 0:raw_input("Wrong password\nENTER to continue")
            else:
                
                while 1:
                    clear()
		    prompt=raw_input("Welcome to pyBank %s\nAccounts:\n%s\n\nw) Withdraw\nd) Deposit\nt) Transfer\nv) View History\nn) New Account\nq) Quit\n>"%(DATA[UserId].name,str(DATA[UserId].balance).strip("{}")))
                    
		    if prompt == "q":
                        pickle("dump",DATA)
                        break 
                    
                    elif prompt == "w":
                        try:
                            account=raw_input("Which account to deposit to?")
                            amount=float(raw_input("Amount to withdraw\n>"))
                            DATA[UserId].Withdraw(amount,account)
                            DATA[UserId+"-log"]+="\n%s -- Withdrew %f -- Balance:%f"%(time.asctime(),amount,DATA[UserId].balance["General"])
                        except pyBank.BankError:raw_input("Cannot withdraw more than you have")
                        except ValueError:raw_input("Amount must not be NULL")
                    elif prompt == "d":
                        try:
                            account=raw_input("Which account to deposit to?")
                            amount=float(raw_input("Amount to deposit\n>"))
                            DATA[UserId].Deposit(amount,account)
                            DATA[UserId+"-log"]+="\n%s -- Deposited %f -- Balance:%f"%(time.asctime(),amount,DATA[UserId].balance["General"])
                        except pyBank.BankError:raw_input("Cannot deposit a negative amount")
                        except ValueError:raw_input("Amount must not be NULL")
                        
                    elif prompt == "t":
                        try:
                            amount=float(raw_input("Amount to transfer\n>"))
                            receiver=raw_input("User to transfer to\n>")
                            
                            DATA[UserId].Transfer(amount,DATA[receiver])
                            DATA[UserId+"-log"]+="\nTransferred %f to %s:Balance:%f"%(amount,receiver,DATA[UserId].balance["General"])
                            DATA[receiver+"-log"]+="\n%s -- Received %f from %s -- Balance:%f"%(time.asctime(),amount,UserId,DATA[receiver].balance["General"])
                            
                        except pyBank.BankError:raw_input("Cannot transfer a negative amount")
                        except ValueError:raw_input("Amount must not be NULL")
                        
                    elif prompt == "n":
                        newaccount=raw_input("Name for new account\n>")
                        newbalance=float(raw_input("Balance for new account\n>"))
                        DATA[UserId].balance[newaccount]=newbalance
                        DATA[UserId+"-log"]+="\nNew account %s created %s with balance %f"%(newaccount,time.asctime(),newbalance)
                    elif prompt == "v":raw_input("%s"%DATA[UserId+"-log"])
                        
        except KeyError:raw_input("No UserID:%s\nENTER to continue"%UserId)
[/PHP]

---

### Post by slavik on 2008-06-16
umm, you have your main menu in a try/except block, that's why you come back to it.

---

### Post by Xavieran on 2008-06-16
I know,
is there any way to have it out of the try,except block, but still catch KeyErrors before it logs in?

If not, I'll just move the try,except block a level down,

Thanks,
Emmanuel

---

### Post by slavik on 2008-06-16
> **Xavieran said:**
> I know,
is there any way to have it out of the try,except block, but still catch KeyErrors before it logs in?

If not, I'll just move the try,except block a level down,

Thanks,
Emmanuel
you need to move it lower in the hierarchy. The key point about exceptions (which I don't think many if any people understand) is that they are really interrupts. When you interrupt a function in the middle, when it returns, it will simply return and not finish all the way through. think of the try block as a function, when there is an interrupt (an error), the handler handles it (the except block) and then goes on to the rest of the program.

ie: in C, if you want to keep your program asleep, what you usually do is **while (1) sleep(10);** if the program is interrupted while in the sleep function, sleep() will return and since it is in the while loop, it will get called again.

---

### Post by Xavieran on 2008-06-16
I have solved my problem, though I'm not sure whether you would call it "pythonic" or not ;).

My new code:(snipped)
[PHP]    if prompt == "l":
        UserId=raw_input("UserID:")
        try:
            if Authenticator(DATA[UserId].password) == 0:
                raw_input("Wrong password\nENTER to continue")
                VALID=0
            else:VALID=1
        except KeyError:raw_input("No UserID:%s"%UserId)
        if VALID==1:
            while 1:do stuff[/PHP]

---

### Post by Martin Witte on 2008-06-16
Another option is to catch the KeyError which can be raised in Autheticate like below, and catch other KeyErrors in a seperate try/except block
```
#!/usr/bin/env python
from pickle import dump, load
from getpass import getpass
from os import system

DIR = '/tmp'

def pickle(mode,data='',file="AcctData.pk"):
    '''Small wrapper for the pickle library to dump or load a pickled object'''
    if mode == "dump":
        picdump=open("%s"%DIR+file,"w")
        dump(data,picdump)
        picdump.close
    elif mode == "load":
        picload=open("%s"%DIR+file,"r")
        data=load(picload)
        picload.close()
        return data
    else:
        return "Invalid mode given"
    
def Authenticator(password):
    userpass=getpass()
    if userpass != password:
        return False
    else:
        return True
    
try:
    DATA = pickle('load')
except IOError:
    DATA={}

def CreateUser():
    # made it empty - put your code back here
    pass

def clear():
    system("clear")

while True:
    clear()
    prompt=raw_input("c) Create User\nl) Login\nq) Quit\n>")
    if prompt == "c":
        CreateUser()
    elif prompt == "q":
        raise SystemExit
    elif prompt == "l":
        UserId=raw_input("UserID:")
        try:
            if not Authenticator(DATA[UserId].password):
                raw_input("Wrong password\nENTER to continue")
                UserId = None
        except KeyError:
                raw_input("No UserID:%s\nENTER to continue"% UserId)
                UserId = None
        if UserId:
            try:
                # put here the remainder of the code
                pass
            except KeyError, e:
                print 'Caught KeyError'
```

---

