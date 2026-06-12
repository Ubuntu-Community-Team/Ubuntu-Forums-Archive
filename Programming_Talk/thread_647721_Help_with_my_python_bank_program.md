---
title: "Help with my python bank program"
date: 2007-12-22
forum: Programming Talk
---

### Post by Xavieran on 2007-12-22
I am writing a small banking program that keeps track of accounts.
The accounts are in the disc and I use this to add them to the program instead of something like Tim=BankAccount(1000,"Tim","Password"):
```
    def GetAccounts(self):
        import os
#change the dir to where the accounts are kept
        os.chdir('/home/xavieran/python/Bank/Accounts')
        global cwd
        cwd=os.listdir(os.getcwd())
        global account
        accounts=[]
#remove files with a ~ in their name because they will cause duplicates
        for account in cwd:
    	    if '~' in account:
    		    os.remove(account)
#Some fancy string formatting to open the file		
        for account in cwd:
            filedir='%s/%s'%(os.getcwd(),account)
            readline=open(filedir,'r')
            check=str(readline.read())
            StartBalance=check.find('Balance')+8
            StartPass=check.find('Password')+9  
            NAME=check[1:StartBalance]
            BALANCE=check[StartBalance:StartPass]
            PASSWORD=check[StartPass:]
            account=BankAccount('%s'%file,BALANCE,PASSWORD)
            print account.name
            accounts.append(account)
```

But when I try to access them using a menu function I made it says that they have not been defined but I made accounts(the list)  global and when I print accounts I get :```
[<Bank.BankAccount instance at 0xb7dbf78c>, <Bank.BankAccount instance at 0xb7dbf7cc>, <Bank.BankAccount instance at 0xb7dbf8ac>]

``` so they are definetely there...

P.S.Any tips on making good names for variables?
mine always seem to end up being very similar...xDD

Heres the full code:
```
'''Module for the manipulation and creation of bank accounts'''
class BankAccount:
    '''A bank account class for manipulating bank accounts'''
    def __init__(self,balance,name,password):
        self.balance=balance
        self.name=name
        self.password=password    
            
    def logwrite(self):        
        log=open("/home/xavieran/python/Bank/Accounts/%s-log"%self.name,'a')       
        log.write(record)
        log.close()
        
    def identify(self):
        '''Identifies the user'''
        global access        
        access = 0
        while access != 1:
            prompt=raw_input("Password:")           
            if prompt != self.password:                
                print "Incorrect." 
            if prompt==self.password:
                print "Correct.\nYou may proceed."
                access+=1      
                
                                                                                    
    def CurrentBalance(self):
        '''Displays the current balance'''
        print "Display Current Balance"
        if access != 1:
            print "You do not have permission to view this"           
        else:
            return "Current Balance:$%d"%self.balance        
    def Withdraw(self):
        '''Withdraws money from current bank account'''
        print access
        print "Withdraw Money"                
        withdrawal=int(raw_input("Type the balance to withdraw:"))
        self.balance=self.balance-withdrawal
        global record
        record="Withdrew %d from %s\nCurrent Balance:%d\n"%(withdrawal,self.name,self.balance)
        self.logwrite()                
        return "Current Balance:$%d"%self.balance
    def Deposit(self):
        '''Deposits money in the current bank account'''
        print "Deposit Money"
        deposit=int(raw_input("Type the amount to deposit:"))
        self.balance=self.balance + deposit
        global record
        record="Deposited %d to %s\nCurrent Balance:%d\n"%(deposit,self.name,self.balance)
        self.logwrite()
        return "Current Balance:$%d"%self.balance
    def Transfer(self):
        '''Transfers money between accounts'''
        print "Transfer Money Between Accounts"        
        ammount=int(raw_input("Type the ammount to transfer:"))
        receiver=eval(raw_input("Type the name of the account to transfer to:"))
        self.balance=self.balance-ammount
        receiver.balance=receiver.balance+ammount
        global record
        record="$%d transferred to %s\nCurrent Balance:%d\n"%(ammount,receiver.name,self.balance)
        self.logwrite()
        return "Current Balance:$%d"%self.balance
        

class Menus:
    '''Class to navigate bank menus'''
    def __init__(self,list1,list2):
        self.list1=list1
        self.list2=list2
    def Login(self):
        '''Logs a user in'''
        print "Login"
        global accountname
        accountname=eval(raw_input("Account:"))
        accountname.identify()
        self.UserCP()                   
    def CreateAccount(self):
        '''Creates Account'''
        NewAcctName=raw_input("Name of new account:")
        NewAcctBalance=int(raw_input("How much do you wish to deposit?"))
        NewAcctPass=raw_input("Type a password for your new account:")
        create=open("/home/xavieran/python/Bank/Accounts/%s"%NewAcctName,"w")       
        create.write("Name %s\nBalance %d\nPassword %s"%(NewAcctName,NewAcctBalance,NewAcctPass))
        create.close()
        print "please restart this program to login to your new account"
        self.MainMenu()   
    def MainMenu(self):
        '''The Main Menu'''
        print "Welcome to pybank\n"
        for entry in self.list1:
            print self.list1.index(entry)+1,')',entry        
        prompt=int(raw_input("What do you what to do?"))-1
        rand="self.%s()"%self.list1[prompt]
        eval(rand)       
    def UserCP(self):
        '''User Control Panel'''
        print "Welcome to %s"%accountname.name
        print "Current Balance:%d"%accountname.balance
        for entry in self.list2:
            print self.list2.index(entry)+1,')',entry    
        prompt=int(raw_input("What do you want to do?"))-1
        rand="%s.%s()"%(accountname.name,self.list2[prompt])
        eval(rand)
    def GetAccounts(self):
        import os       
        os.chdir('/home/xavieran/python/Bank/Accounts')
        global cwd
        cwd=os.listdir(os.getcwd())
        global account
        accounts=[]
        for account in cwd:
    	    if '~' in account:
    		    os.remove(account)		
        for account in cwd:
            filedir='%s/%s'%(os.getcwd(),account)
            readline=open(filedir,'r')
            check=str(readline.read())
            StartBalance=check.find('Balance')+8
            StartPass=check.find('Password')+9  
            NAME=check[1:StartBalance]
            BALANCE=check[StartBalance:StartPass]
            PASSWORD=check[StartPass:]
            account=BankAccount('%s'%file,BALANCE,PASSWORD)
            print account.name
            accounts.append(account)
```

---

### Post by Majorix on 2007-12-22
You aren't defining the accounts -list- as global. You have only defined a global account -variable-.

Importing in functions is generally not a good idea, as it kills the possibility to call the function in a loop. If you do call it in a loop, you will end up with thousands of imported modules.

And are you English or American or do you live in another English-spoken country? If not, you could use your native tongue to make up variable names, where you will be much more comfortable.

---

### Post by Xavieran on 2007-12-23
Thanks for that...that was a pretty stupid mistake xD.

I live in an English speaking country and English is my mother tongue,so yeah...
I didn't think about that import thing thanks for that too...

But:Now that the accounts list is global it still does not recognize the objects...
Heres my current code:
Bank Module:
```
'''Module for the manipulation and creation of bank accounts'''
import os
class BankAccount:
    '''A bank account class for manipulating bank accounts'''
    def __init__(self,balance,name,password):
        self.balance=balance
        self.name=name
        self.password=password    
            
    def logwrite(self):        
        log=open("/home/xavieran/python/Bank/Logs/%s-log"%self.name,'a')       
        log.write(record)
        log.close()
        
    def writebalance(self):
        account=open("/home/xavieran/python/Bank/Accounts/%s","w")
        account.write("StartName %s StartBalance %d StartPass %s"%(self.name,self.balance,self.password))
        account.close()
        
    def identify(self):
        '''Identifies the user'''
        global access       
        access = 0
        while access != 1:
            prompt=raw_input("Password:")           
            if prompt != self.password:                
                print "Incorrect." 
            if prompt==self.password:
                print "Correct.\nYou may proceed."
                access+=1      
                
                                                                                    
    def CurrentBalance(self):
        '''Displays the current balance'''
        print "Display Current Balance"
        if access != 1:
            print "You do not have permission to view this"           
        else:
            return "Current Balance:$%d"%self.balance        
    def Withdraw(self):
        '''Withdraws money from current bank account'''
        print access
        print "Withdraw Money"                
        withdrawal=int(raw_input("Type the balance to withdraw:"))
        self.balance=self.balance-withdrawal
        global record
        record="Withdrew %d from %s\nCurrent Balance:%d\n"%(withdrawal,self.name,self.balance)
        self.logwrite()
        self.writebalance()                
        return "Current Balance:$%d"%self.balance
    def Deposit(self):
        '''Deposits money in the current bank account'''
        print "Deposit Money"
        deposit=int(raw_input("Type the amount to deposit:"))
        self.balance=self.balance + deposit
        global record
        record="Deposited %d to %s\nCurrent Balance:%d\n"%(deposit,self.name,self.balance)
        self.logwrite()
        self.writebalance()
        return "Current Balance:$%d"%self.balance
    def Transfer(self):
        '''Transfers money between accounts'''
        print "Transfer Money Between Accounts"        
        ammount=int(raw_input("Type the ammount to transfer:"))
        receiver=eval(raw_input("Type the name of the account to transfer to:"))
        self.balance=self.balance-ammount
        receiver.balance=receiver.balance+ammount
        global record
        record="$%d transferred to %s\nCurrent Balance:%d\n"%(ammount,receiver.name,self.balance)
        self.logwrite()
        self.writebalance()
        return "Current Balance:$%d"%self.balance
        

class Menus:
    '''Class to navigate bank menus'''
    def __init__(self,list1,list2,list3,list4,password):
        self.list1=list1
        self.list2=list2
        self.list3=list3
        self.list4=list4
        self.password=password
#    def GetAccounts(self):
#        '''Loads accounts into accountslist'''
#        import os      
#        os.chdir('/home/xavieran/python/Bank/Accounts')
#        cwd=os.listdir(os.getcwd())
#        global accountslist
#        accountslist=[]
#        for account in cwd:
#    	    if '~' in account:
#    		    os.remove(account)        		
#        for account in cwd:
#            filedir='%s/%s'%(os.getcwd(),account)
#            readline=open(filedir,'r')
#            check=str(readline.read())
#            StartName=check.find('StartName')+10
#            EndName=check.find('StartBalance')
#            StartBalance=check.find('StartBalance')+13
#            EndBalance=check.find('StartPass')
#            StartPass=check.find('StartPass')+10
#            NAME=check[StartName:EndName]
#            BALANCE=check[StartBalance:EndBalance]
#            PASSWORD=check[StartPass:]
#            account=BankAccount(BALANCE,NAME,PASSWORD)
#            accountslist.append(account)
             
    def MainMenu(self):
        '''The Main Menu'''
        print "Welcome to pybank\n"
        for entry in self.list1:
            print self.list1.index(entry)+1,')',entry        
        prompt=int(raw_input("What do you what to do?"))-1
        rand="self.%s()"%self.list1[prompt]
        eval(rand)
    def Login(self):
        '''Logs a user in'''
        print "Login"
        for entry in self.list4:
            print self.list4.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account?"))-1
        rand="%s.identify()"%self.list4[prompt].name
        eval(rand)
        self.UserCP()                   
    def ListAccounts(self):
        '''Lists the current accounts in accountslist'''
        for entry in self.list4:
            print entry.name 
            
        self.MainMenu()           
    def CreateAccount(self):
        '''Creates Account'''
        NewAcctName=raw_input("Name of new account:")
        NewAcctBalance=int(raw_input("How much do you wish to deposit?"))
        NewAcctPass=raw_input("Type a password for your new account:")
        create=open("/home/xavieran/python/Bank/Accounts/%s"%NewAcctName,"w")       
        create.write("StartName %s StartBalance %d StartPass %s"%(NewAcctName,NewAcctBalance,NewAcctPass))
        create.close()
        self.GetAccounts()
        self.MainMenu() 
                 
    def UserCP(self):
        '''User Control Panel'''
        print "Welcome to %s"%Test.name
        print "Current Balance:%d"%Test.balance
        for entry in self.list2:
            print self.list2.index(entry)+1,')',entry    
        prompt=int(raw_input("What do you want to do?"))-1
        rand="%s.%s()"%(Test.name,self.list2[prompt])
        eval(rand)
        
    def Admin(self):
        '''The admin menu'''
        verify=raw_input("Password:")
        if verify != self.password:
            self.MainMenu()
        for entry in self.list3:
            print self.list3.index(entry)+1,')',entry    
        prompt=int(raw_input("What do you want to do?"))-1
        rand="self.%s()"%(self.list3[prompt])
        eval(rand)    
    def ReadLogs(self):
        '''Reads logs'''
        prompt=raw_input("Which user's logs do you wish to view?")
        log=open("/home/xavieran/python/Bank/Logs/%s-log"%prompt,"r")
        print log.read()
        log.close
        self.Admin()
    def DeleteAccount(self):
        for entry in self.list4:
            print self.list4.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account?"))-1
        cont=raw_input("Are you sure you want to delete %s?"%self.list4[prompt].name)        
        if cont == 'y':
            rand=os.remove("/home/xavieran/python/Bank/Accounts/%s"%self.list4[prompt].name)
        self.Admin()    
    def DeleteLogs(self):
        for entry in self.list4:
            print self.list4.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account's logs?"))-1
        cont=raw_input("Are you sure you want to delete %s?"%self.list4[prompt].name)        
        if cont == 'y':
            rand=os.remove("/home/xavieran/python/Bank/Logs/%s-log"%self.list4[prompt].name)
        self.Admin()
```

BankMenu(run this one):
```
'''Module for the manipulation and creation of bank accounts'''
import os
class BankAccount:
    '''A bank account class for manipulating bank accounts'''
    def __init__(self,balance,name,password):
        self.balance=balance
        self.name=name
        self.password=password    
            
    def logwrite(self):        
        log=open("/home/xavieran/python/Bank/Logs/%s-log"%self.name,'a')       
        log.write(record)
        log.close()
        
    def writebalance(self):
        account=open("/home/xavieran/python/Bank/Accounts/%s","w")
        account.write("StartName %s StartBalance %d StartPass %s"%(self.name,self.balance,self.password))
        account.close()
        
    def identify(self):
        '''Identifies the user'''
        global access       
        access = 0
        while access != 1:
            prompt=raw_input("Password:")           
            if prompt != self.password:                
                print "Incorrect." 
            if prompt==self.password:
                print "Correct.\nYou may proceed."
                access+=1      
                
                                                                                    
    def CurrentBalance(self):
        '''Displays the current balance'''
        print "Display Current Balance"
        if access != 1:
            print "You do not have permission to view this"           
        else:
            return "Current Balance:$%d"%self.balance        
    def Withdraw(self):
        '''Withdraws money from current bank account'''
        print access
        print "Withdraw Money"                
        withdrawal=int(raw_input("Type the balance to withdraw:"))
        self.balance=self.balance-withdrawal
        global record
        record="Withdrew %d from %s\nCurrent Balance:%d\n"%(withdrawal,self.name,self.balance)
        self.logwrite()
        self.writebalance()                
        return "Current Balance:$%d"%self.balance
    def Deposit(self):
        '''Deposits money in the current bank account'''
        print "Deposit Money"
        deposit=int(raw_input("Type the amount to deposit:"))
        self.balance=self.balance + deposit
        global record
        record="Deposited %d to %s\nCurrent Balance:%d\n"%(deposit,self.name,self.balance)
        self.logwrite()
        self.writebalance()
        return "Current Balance:$%d"%self.balance
    def Transfer(self):
        '''Transfers money between accounts'''
        print "Transfer Money Between Accounts"        
        ammount=int(raw_input("Type the ammount to transfer:"))
        receiver=eval(raw_input("Type the name of the account to transfer to:"))
        self.balance=self.balance-ammount
        receiver.balance=receiver.balance+ammount
        global record
        record="$%d transferred to %s\nCurrent Balance:%d\n"%(ammount,receiver.name,self.balance)
        self.logwrite()
        self.writebalance()
        return "Current Balance:$%d"%self.balance
        

class Menus:
    '''Class to navigate bank menus'''
    def __init__(self,list1,list2,list3,list4,password):
        self.list1=list1
        self.list2=list2
        self.list3=list3
        self.list4=list4
        self.password=password
#    def GetAccounts(self):
#        '''Loads accounts into accountslist'''
#        import os      
#        os.chdir('/home/xavieran/python/Bank/Accounts')
#        cwd=os.listdir(os.getcwd())
#        global accountslist
#        accountslist=[]
#        for account in cwd:
#    	    if '~' in account:
#    		    os.remove(account)        		
#        for account in cwd:
#            filedir='%s/%s'%(os.getcwd(),account)
#            readline=open(filedir,'r')
#            check=str(readline.read())
#            StartName=check.find('StartName')+10
#            EndName=check.find('StartBalance')
#            StartBalance=check.find('StartBalance')+13
#            EndBalance=check.find('StartPass')
#            StartPass=check.find('StartPass')+10
#            NAME=check[StartName:EndName]
#            BALANCE=check[StartBalance:EndBalance]
#            PASSWORD=check[StartPass:]
#            account=BankAccount(BALANCE,NAME,PASSWORD)
#            accountslist.append(account)
             
    def MainMenu(self):
        '''The Main Menu'''
        print "Welcome to pybank\n"
        for entry in self.list1:
            print self.list1.index(entry)+1,')',entry        
        prompt=int(raw_input("What do you what to do?"))-1
        rand="self.%s()"%self.list1[prompt]
        eval(rand)
    def Login(self):
        '''Logs a user in'''
        print "Login"
        for entry in self.list4:
            print self.list4.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account?"))-1
        rand="%s.identify()"%self.list4[prompt].name
        eval(rand)
        self.UserCP()                   
    def ListAccounts(self):
        '''Lists the current accounts in accountslist'''
        for entry in self.list4:
            print entry.name 
            
        self.MainMenu()           
    def CreateAccount(self):
        '''Creates Account'''
        NewAcctName=raw_input("Name of new account:")
        NewAcctBalance=int(raw_input("How much do you wish to deposit?"))
        NewAcctPass=raw_input("Type a password for your new account:")
        create=open("/home/xavieran/python/Bank/Accounts/%s"%NewAcctName,"w")       
        create.write("StartName %s StartBalance %d StartPass %s"%(NewAcctName,NewAcctBalance,NewAcctPass))
        create.close()
        self.GetAccounts()
        self.MainMenu() 
                 
    def UserCP(self):
        '''User Control Panel'''
        print "Welcome to %s"%Test.name
        print "Current Balance:%d"%Test.balance
        for entry in self.list2:
            print self.list2.index(entry)+1,')',entry    
        prompt=int(raw_input("What do you want to do?"))-1
        rand="%s.%s()"%(Test.name,self.list2[prompt])
        eval(rand)
        
    def Admin(self):
        '''The admin menu'''
        verify=raw_input("Password:")
        if verify != self.password:
            self.MainMenu()
        for entry in self.list3:
            print self.list3.index(entry)+1,')',entry    
        prompt=int(raw_input("What do you want to do?"))-1
        rand="self.%s()"%(self.list3[prompt])
        eval(rand)    
    def ReadLogs(self):
        '''Reads logs'''
        prompt=raw_input("Which user's logs do you wish to view?")
        log=open("/home/xavieran/python/Bank/Logs/%s-log"%prompt,"r")
        print log.read()
        log.close
        self.Admin()
    def DeleteAccount(self):
        for entry in self.list4:
            print self.list4.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account?"))-1
        cont=raw_input("Are you sure you want to delete %s?"%self.list4[prompt].name)        
        if cont == 'y':
            rand=os.remove("/home/xavieran/python/Bank/Accounts/%s"%self.list4[prompt].name)
        self.Admin()    
    def DeleteLogs(self):
        for entry in self.list4:
            print self.list4.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account's logs?"))-1
        cont=raw_input("Are you sure you want to delete %s?"%self.list4[prompt].name)        
        if cont == 'y':
            rand=os.remove("/home/xavieran/python/Bank/Logs/%s-log"%self.list4[prompt].name)
        self.Admin()
```

---

### Post by Quikee on 2007-12-23
You forgot to substitute %s in filename here:
[PHP]     def writebalance(self):
        account=open(**"/home/xavieran/python/Bank/Accounts/%s"**,"w")
        account.write("StartName %s StartBalance %d StartPass %s"%(self.name,self.balance,self.password))
        account.close()
[/PHP]

You still use globals - get rid of them. ;)

You could use pickle to dump the objects to files instead to write and parse the files yourself.

Example:[PHP]
#!/usr/bin/env python
import pickle

#data to serialize
data = {'a': [1, 2.0, 3, 4+6j],
         'b': ('string', u'Unicode string'),
         'c': None}

#write
output = open('data.pkl', 'wb')
pickle.dump(data, output)
output.close()

#read 
pickleFile = open('data.pkl', 'rb')
dataFromFile = pickle.load(pickleFile)
pickleFile.close()

print dataFromFile['a']
print dataFromFile['b']
print dataFromFile['c'][/PHP]


Alternatively you could use yaml (get python-yaml from repository) instead of pickle. 

Example:

[PHP]#!/usr/bin/env python

import yaml

data = {'a': [1, 2.0, 3, 4+6j],
        'b': ('string', u'Unicode string'),
        'c': None}
        
stream = file('data.yaml', 'w')
yaml.dump(data, stream)
stream.close()
         
stream = file('data.yaml', 'r')
readData = yaml.load(stream)
stream.close()

print readData['a']
print readData['b']
print readData['c'][/PHP]

---

### Post by Xavieran on 2007-12-23
Pickle looks very interesting...it took me about 15 mins to get the prog to parse my files,so I could probably use something like that...

My real problem is,and I seriously have no idea what is causing it is that when I run the program and do a "login" it says that the object I just tried to call has not been defined,even though it is happily residing in the accountslist[] list and I can call it's name from the ListAccounts() function.

What's wrong with global variables?

Thanks for your help guys,it really is appreciated:)

---

### Post by Quikee on 2007-12-23
> **Xavieran said:**
> 
What's wrong with global variables?


Globals are acceptable if you write procedural but even there I would not use them. If you write object oriented they are not acceptable at all as they break the "locality" and encapsulation of the object/class. 

Example:

[PHP]class BankAccount:
    '''A bank account class for manipulating bank accounts'''
    def __init__(self,balance,name,password):
        self.balance=balance
        self.name=name
        self.password=password    
            
    def logwrite(self):        
        log=open("/home/xavieran/python/Bank/Logs/%s-log"%self.name,'a')       
        log.write(record)
        log.close()
        
    def writebalance(self):
        account=open("/home/xavieran/python/Bank/Accounts/%s","w")
        account.write("StartName %s StartBalance %d StartPass %s"%(self.name,self.balance,self.password))
        account.close()
        
    def identify(self):
        '''Identifies the user'''
        global access       
        access = 0
        while access != 1:
            prompt=raw_input("Password:")           
            if prompt != self.password:                
                print "Incorrect." 
            if prompt==self.password:
                print "Correct.\nYou may proceed."
                access+=1      
[/PHP]

When you used access as a global you made your BankAccount secretly dependent on this variable. If I try to write my own program and don't know (also don't care about) the implementation of your BankAccount then I would trip on a surprise when i would try to use identify() method. 

Imagine that you would need to do something like this to open a file: 
[PHP]
filename = "somefile.file"
mode = "w"
file = open()
file.close()
[/PHP]

instead of:
[PHP]
file = open("somefile.file", "w")
file.close()
[/PHP]

Pretty stupid.. but that would be the consequence of using globals. 

The next question then is - is to identify the user really the responsibility of a BankAccount? Of course not - a more correct approach here would be to create a class called let say "Authenticator" which would get the password and check if the user may proceed.. depending on the information in BankAccount. Taking care of value inputing (like passwords) is also the responsibility of someone else - not the Authenticator or BankAccount. 

Good luck.

---

### Post by Martin Witte on 2007-12-23
I agree with the others that in this case the global is not what you want. For some more thoughts on what you try to do see the comments in the code
[PHP]#!/usr/bin/env python
class BankAccount:
    '''A bank account class for manipulating bank accounts'''
    def __init__(self, balance ,password):
        self.balance = balance
        self.password = password
        # access is a property of the account, it doesn't have a global meaning
        # Python knows booleans, in this case it makes your code easier to read
        self.access = False
            
    def identify(self):
        '''Identifies the user'''
        # introduce a counter, else if you don't know the password there is no escape
        # from this loop
        count = 0
        while not self.access and count < 3:
            prompt=raw_input("Password:")           
            if prompt != self.password:                
                print "Incorrect."
                count += 1
            if prompt==self.password:
                print "Correct.\nYou may proceed."
                self.access = True      
                
                                                                                    
    def CurrentBalance(self):
        '''Displays the current balance'''
        print "Display Current Balance"
        if not self.access:
            print "You do not have permission to view this"           
        else:
            #balance is a float, not an integer in most currencies
            print "Current Balance:$ %.2f" % self.balance        


if __name__ == '__main__':
    account = BankAccount(5.0, 'qwerty')
    account.identify()
    account.CurrentBalance()
[/PHP]

---

### Post by Xavieran on 2007-12-24
> Martin Witte:
    def identify(self):
        '''Identifies the user'''
        # introduce a counter, else if you don't know the password there is no escape
        # from this loop
        count = 0
        while not self.access and count < 3:
            prompt=raw_input("Password:")           
            if prompt != self.password:                
                print "Incorrect."
                count += 1
            if prompt==self.password:
                print "Correct.\nYou may proceed."
                self.access = True

I did have something like this originally but did not know how to have a while loop depend on two things. O.K.,So global variables are evil.:D

I'll try and improve my code along the lines that you guys have been posting.

Again,thanks for your help.:)

And Merry Christmas!

---

### Post by Xavieran on 2007-12-26
Hey guys,thanks for the help :)

Here it is,in all of it's working glory!

Of course you need to create the directory structure to be able to use it ,but my next project shall be an *installer*
It could still do with a little work, but it works!

```
'''Module for the manipulation and creation of bank accounts'''
import os,sys
class BankAccount:
    '''A bank account class for manipulating bank accounts'''
#record is a variable used to hold records to be written in logwrite()
    def __init__(self,balance,name,password,record):
        self.balance=balance
        self.name=name
        self.password=password    
            
    def logwrite(self):
        '''call logwrite to write self.record...useful for ,uh,stuff'''        
        log=open("/home/xavieran/python/Bank/Logs/%s-log"%self.name,'a')       
        log.write(self.record)
        log.close()
        
    def writebalance(self):
        account=open("/home/xavieran/python/Bank/Accounts/%s"%self.name,"w")
#This is the special format used by my account files
        account.write("StartName %s StartBalance %d StartPass %s"%(self.name,self.balance,self.password))
        account.close()
                                                             
    def CurrentBalance(self):
        '''Displays the current balance'''
        print "Display Current Balance"
        return "Current Balance:$%d"%self.balance        
    def Withdraw(self,amount=0):
        '''Withdraws money from current bank account'''
        print "Withdraw Money"                
        withdrawal=int(raw_input("Type the balance to withdraw:"))
#We wouldn't want people creating money out of nowhere now would we...
        if withdrawal > self.balance:
            print "You do not have that much money."
        else:
            self.balance -= withdrawal
        self.record="Withdrew %d from %s\nCurrent Balance:%d\n"%(withdrawal,self.name,self.balance)
        self.logwrite()
        self.writebalance()                
        return "Current Balance:$%d"%self.balance
    def Deposit(self,amount=0):
        '''Deposits money in the current bank account.amount is an optional argument used for execution without user input'''
        print "Deposit Money"
        deposit=int(raw_input("Type the amount to deposit:"))
        self.balance += deposit
        self.record="Deposited %d to %s\nCurrent Balance:%d\n"%(deposit,self.name,self.balance)
        self.logwrite()
        self.writebalance()
        return "Current Balance:$%d"%self.balance
        if amount !=0:
            self.balance += deposit
            self.record="Deposited %d to %s\nCurrent Balance:%d\n"%(deposit,self.name,self.balance)
            self.logwrite()
            self.writebalance()            
#Transfer function left in for compatability
    def Transfer(self):
        '''Transfers money between accounts'''
        print "Transfer Money Between Accounts"        
        amount=int(raw_input("Type the amount to transfer:"))
        receiver=eval(raw_input("Type the name of the account to transfer to:"))
        self.balance +- amount
        receiver.balance=receiver.balance+amount
        self.record="$%d transferred to %s\nCurrent Balance:%d\n"%(amount,receiver.name,self.balance)
        self.logwrite()
        self.writebalance()
        return "Current Balance:$%d"%self.balance


        
def Authenticator(password):
    '''Can be called to authenticate a password'''
    tries = 0
    userpass=''
    status=0
    password = str(password) 
    while userpass != password:
        userpass = raw_input("Password:")
        if userpass == password:
            print "Authenticated"
            status=1
        else:
            print "Incorrect.\nTry Again."
            tries += 1   
                                
        
class Menus:
    '''A very featured class.\n\nIt has 3 menus with each menu going up a level of command.\npassword is the admin password.\nuser is not meant to be instantiated by a user of the Menu because user is used as an index for Users.\nWhen you instantiate this class, the Ops variables *must* have functions that are in the module itself.ie:Login,CreateAccount etc.\nThe list Users must have BankAccount class objects in it and nothing else.'''
    def __init__(self,MainMenuOps,UserCPOps,AdminOps,Users,password,user=""):
        self.MainMenuOps=MainMenuOps
        self.UserCPOps=UserCPOps
        self.AdminOps=AdminOps
        self.Users=Users
        self.password=password
        self.user=user
        
    def GetAccounts(self):
            os.chdir('/home/xavieran/python/Bank/Accounts')
            cwd=os.listdir(os.getcwd())
            for account in cwd:
                if '~' in account:
                    os.remove(account)        		
                filedir='%s/%s'%(os.getcwd(),account)
                readline=open(filedir,'r')
                check=str(readline.read())
                StartName=check.find('StartName')+10
                EndName=check.find('StartBalance')-1
                StartBalance=check.find('StartBalance')+13
                EndBalance=check.find('StartPass')
                StartPass=check.find('StartPass')+10
                NAME=check[StartName:EndName]
                BALANCE=int(check[StartBalance:EndBalance])
                PASSWORD=check[StartPass:]
                account=BankAccount(BALANCE,NAME,PASSWORD,'')
                self.Users.append(account)

    def MainMenu(self):
        '''The Main Menu'''
        print "Welcome to pybank\n"
#I add 1 to make it more readable for the end-user.Knowing this, we must subtract one from the answer
        for entry in self.MainMenuOps:
            print self.MainMenuOps.index(entry)+1,')',entry
        try:        
            prompt=int(raw_input("What do you want to do?"))-1
        except ValueError:
            print "Spelling mistake, try again"
            self.MainMenu()
#We have to index MainMenuOps with prompt to grab the users wanted function
        try: 
            rand="self.%s()"%self.MainMenuOps[prompt]
            eval(rand)
        except IndexError:
            print "Spelling mistake, try again"
            self.MainMenu()
    def Login(self):
        '''Logs a user in'''
        print "Login"
        for entry in self.Users:
            print self.Users.index(entry)+1,')',entry.name-
        self.user=int(raw_input("Which account?"))-1
#Authenticator is our general purpose password checking function...still needs some work.
        Authenticator(self.Users[self.user].password)
        self.UserCP()                   
    def ListAccounts(self):
        '''Lists the current accounts in accountslist'''
        for entry in self.Users:
            print entry.name             
        self.MainMenu()           
    def CreateAccount(self):
        '''Creates Account'''
        NewAcctName=raw_input("Name of new account:")
        NewAcctBalance=int(raw_input("How much do you wish to deposit?"))
        NewAcctPass=raw_input("Type a password for your new account:")
#Create the users file...
        create=open("/home/xavieran/python/Bank/Accounts/%s"%NewAcctName,"w")       
        create.write("StartName %s StartBalance %d StartPass %s"%(NewAcctName,NewAcctBalance,NewAcctPass))
        create.close()
        self.GetAccounts()
        self.MainMenu() 
                 
    def UserCP(self):
        '''User Control Panel'''
        print "Welcome to %s"%self.Users[self.user].name
        while 1 is 1:
            print "Current Balance:%d"%self.Users[self.user].balance
            for entry in self.UserCPOps:
                print self.UserCPOps.index(entry)+1,')',entry    
            prompt=int(raw_input("What do you want to do?"))-1  
#It calls the Transfer function in self,not the Transfer function in BankAccounts          
            if prompt == 2:
                self.Transfer()
#This is also our own function in the Menus class
            if prompt == 3:
                self.Logout()
#Otherwise do things as if they were a function of the object
            else:    
                run="self.Users[%s].%s()"%(self.user,self.UserCPOps[prompt])
                eval(run)
    def Logout(self):
            '''Log's the user out,kinda...xDD'''
            self.MainMenu()
    def Transfer(self):
        print "Transfer Money Between Accounts"        
        amount=int(raw_input("Type the amount to transfer:"))
#We don't want cheaters do we?
        if amount > self.Users[self.user].balance:
            print "You do not have that much money"
        else:        
            for entry in self.Users:
                print self.Users.index(entry)+1,')',entry.name
#It looks daunting but mainly just
            receiver=int(raw_input("Which account?"))-1
            self.Users[self.user].balance -= amount
            self.Users[self.user].record="$%d transferred to %s\nCurrent Balance:%d\n"%(amount,self.Users[receiver].name,self.Users[self.user].balance)
            self.Users[self.user].logwrite()
            self.Users[self.user].writebalance()
            self.Users[receiver].balance += amount
            self.Users[receiver].record="$%d received from %s\nCurrent Balance:%d\n"%(amount,self.Users[self.user].name,self.Users[receiver].balance)
            print "Current Balance:$%d"%self.Users[self.user].balance
            self.UserCP()
                
    def Admin(self):
        '''The admin menu'''
        verify=raw_input("Password:")
        if verify != self.password:
            self.MainMenu()
        while 1 is 1:
            for entry in self.AdminOps:
                print self.AdminOps.index(entry)+1,')',entry    
            prompt=int(raw_input("What do you want to do?"))-1
#This is another "Logout" function...sortof...xDD
            if prompt == 3:
                self.MainMenu()
            try:    
                run="self.%s()"%(self.AdminOps[prompt])
                eval(run)
            except IndexError:
                print "Spelling mistake, try again"
                self.Admin()    
    def ReadLogs(self):
        '''Reads logs'''
        prompt=raw_input("Which user's logs do you wish to view?")
        log=open("/home/xavieran/python/Bank/Logs/%s-log"%prompt,"r")
        print log.read()
        log.close
        self.Admin()
    def DeleteAccount(self):
        '''Deletes Accounts'''
        for entry in self.Users:
            print self.Users.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account?"))-1
        cont=raw_input("Are you sure you want to delete %s?"%self.Users[prompt].name)        
        if cont == 'y':
            rand=os.remove("/home/xavieran/python/Bank/Accounts/%s"%self.Users[prompt].name)
        self.GetAccounts()
        self.Admin()    
    def DeleteLogs(self):
        '''Deletes Logs'''
        for entry in self.Users:
            print self.Users.index(entry)+1,')',entry.name
        prompt=int(raw_input("Which account's logs?"))-1
        cont=raw_input("Are you sure you want to delete %s?"%self.Users[prompt].name)        
        if cont == 'y':
            os.remove("/home/xavieran/python/Bank/Logs/%s-log"%self.Users[prompt].name)
        self.Admin()
        
        
        
        
if __name__ == "__main__":
    MainMenuOps=["Login","CreateAccount","ListAccounts","Admin"]
    UserCPOps=["Withdraw","Deposit","Transfer","Logout"]
    AdminOps=["ReadLogs","DeleteAccount","DeleteLogs","Logout"]
    Users=[]      
    menu=Menus(MainMenuOps,UserCPOps,AdminOps,Users,"admin")
    menu.GetAccounts()
    menu.MainMenu()
```

---

### Post by Quikee on 2007-12-27
I have created a somewhat similar program yesterday for someone's homework (I know I should not be doing someone else's homework but - it was Christmas ;) ). It is not very pretty because it was done in a haste and following the instructions precisely but you still might find something useful to use in your program. Good luck. 

[PHP]
#!/usr/bin/env python

import pickle

class Product(object):
	def __init__(self, name, code, price, stock):
		self.name = name
		self.code = code
		self.price = price
		self.stock = stock
	
	def value(self):
		return self.price*self.stock

class ProductDatabase(object):
	def __init__(self, filename):
		self.filename = filename
		self.database = {}
		
		try:
			self.open()
		except IOError:
			self.save()	
	
	def open(self):
		file = open(self.filename, "rb")
		self.database = pickle.load(file)
		file.close()
	
	def save(self):
		file = open(self.filename, "wb")
		pickle.dump(self.database, file)
		file.close()

	def printDB(self):
		for productName, product in self.database.iteritems():
			print "Product: %s(%s) - Price %.2f Stock %d Value %.2f" % \
				(product.name, product.code, product.price, product.stock, product.value())

	def addProduct(self):
		print "Input product name"
		productName = raw_input()
		
		print "Input product code"
		productCode = raw_input()
	
		productPrice = self.inputProductPrice()
		productStock = self.inputProductStock()
		
		self.database[productName] = Product(productName, productCode, productPrice, productStock)
		self.save()
	
	def inputProductPrice(self):
		productPrice = None
		while not productPrice:
			try:
				print "Input product price"
				productPrice = float(raw_input())
			except ValueError: 
				productPrice = None
		return productPrice
		
	def inputProductStock(self):
		productStock = None
		while not productStock:
			try:
				print "Product Stock:"
				productStock = int(raw_input())
			except ValueError: 
				productStock = None
		return productStock
	
	def selectProductByName(self):
		print "Input product name"
		return raw_input()
	
	def getProductByName(self, name):
		if name not in self.database:
			return None
		return self.database[name]
		
	def deleteProduct(self):
		productName = self.selectProductByName()
		
		try:
			del self.database[productName]
		except KeyError:
			print "Product does not exists"
			return
		print "Product %s deleted" % productName
		self.save()
	
	def changePriceAndSave(self):
		self.changePrice()
		self.save()
		
	def changePrice(self):
		productName = self.selectProductByName()
		
		product = self.getProductByName(productName)
		if not product:
			print "Product %s not in databse yet!" % productName
		
		productPrice = self.inputProductPrice()
		product.price = productPrice
		
	def changeStockAndSave(self):
		productName = self.selectProductByName()
		
		product = self.getProductByName(productName)
		if not product:
			print "Product %s not in databse yet!" % productName
			
		print "Current stock is %d!" % product.stock
		productStock = self.inputProductStock()
		product.stock = productStock
		
		self.save()
	
	def valueOfAllProducts(self):
		collectedValue = 0.0
		for productName, product in self.database.iteritems():
			collectedValue += product.value()
		print "Value of all products is: %f" % collectedValue
	
	def stockOfAllProducts(self):
		stockOfAllProducts = 0
		for productName, product in self.database.iteritems():
			stockOfAllProducts += product.stock
		print "Stock of all products is: %d" % stockOfAllProducts

if __name__ == "__main__":
	
	print "Input database filename:"
	databaseFilename = raw_input()
	
	database = ProductDatabase(databaseFilename)
	
	choise = 0
	choises = {
		1 : database.printDB,
		2 : database.addProduct,
		3 : database.deleteProduct,
		4 : database.changeStockAndSave,
		5 : database.changePriceAndSave,
		6 : database.changePrice,
		7 : database.valueOfAllProducts,
		8 : database.stockOfAllProducts
	}
	
	while (choise != 9):
		print
		print "1. Print database"
		print "2. Add product"
		print "3. Delete product"
		print "4. Change stock and save"
		print "5. Change price and save"
		print "6. Change price"
		print "7. Value of all products"
		print "8. Stock of all products"
		print "9. Exit"
		print "Choose:"
		choise = raw_input()
		print
		try:
			choise = int(choise)
		except ValueError:
			choise = 0
		if choise in choises:
			choises[choise]()[/PHP]

---

