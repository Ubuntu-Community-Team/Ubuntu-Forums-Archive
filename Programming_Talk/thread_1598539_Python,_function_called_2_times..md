---
title: "Python, function called 2 times."
date: 2010-10-16
forum: Programming Talk
---

### Post by cgroza on 2010-10-16
So I have this functions in python that write some lines to a file. The file is used as a config file. But when the second function finishes running the first one is called again. This should not be happening because the first function is not called in the second function. Here is some code.


```
def sel():
 try:   
    print("Enter:\n1 to Install.           5 to Clean.")                   
    print("2 to Remove.            6 to Enter Custom Command.")
    print("3 to Upgrade.           7 to Fix Broken Pakckages.")
    print("4 to Update.            8 to Manage Log File.")
    print("q to Quit.              9 to enter Settings Wizard. ")
    sel1=raw_input('1/2/3/4/5/6/7/8/q/: ')
    if sel1 == '1':
         install()

    elif sel1 == '2':
         remove()
   
    elif sel1 == '3':
        upgrade()
        

    elif sel1 == '4':
        update()

    elif sel1 == '5':
        maintain()
    
    elif sel1 == "6":
        customapt()
    
    elif sel1 == "7":
        fixbroken()
    
    elif sel1 == "8":
        manlog()
    
    elif sel1 == "9":
        logparam()
        notifyparam()
        
    
    elif sel1 == 'q':
         quit()
                 
    else:
         os.system('clear')
         sel()  




def logparam():
    os.system("clear") 
    logset=raw_input("1 to Enable Log\n2 to Disable Log:")
    if logset == "1":
        conf = open(configfile,"w")
        conf.write("")
        conf.close()
        
        conf = open(configfile,"a")
        conf.write("log=enabled\n")
        conf.close()
    
    elif logset == "2":        
        conf = open(configfile,"a")
        conf.write("log=disabled\n")
        conf.close()
    
    else:
        os.system("clear")
        logparam()



def notifyparam():
    os.system("clear")  
    notifyset=raw_input("1 to Enble Notifications.\n2 to Disable Notifications.")
    logset=raw_input("1 to Enable Log\n2 to Disable Log:")
    if notifyset == "1":        
        conf = open(configfile,"a")
        conf.write("notification=enabled\n")
        conf.write("EOF")
        conf.close()
        
        
    
    elif notifyset == "2":        
        conf = open(configfile,"a")
        conf.write("notification=disabled\n")
        conf.write("EOF")
        conf.close()
        
    
    else:
        os.system("clear")
        notifyparam()   
    
    print("Program must be restarted for changes to take effect.")
    raw_input("Press <enter> to continue.")
    os.system("clear")
    sel()
```


The sel function calls logparam(), and then notifyparam(), but after notifyparam finishes logparam is called again. Why? THanks

---

### Post by Tony Flury on 2010-10-16
you have logparam and notifyparam functions calling themselves - was that intended ?

And the bit that calls sel is indented actually as part of notify param

So if you call sel - it call notifyparam -> which calls sel - etc ...

---

### Post by cgroza on 2010-10-17
I got it. No function was called. Just a accidentally misplaced raw_input(). Thanks.
The function calls itself in case the user gives bad input. So the function starts again and gives the user another chance and so on.

---

### Post by worksofcraft on 2010-10-17
> **cgroza said:**
> I got it. No function was called. Just a accidentally misplaced raw_input(). Thanks.
The function calls itself in case the user gives bad input. So the function starts again and gives the user another chance and so on.

Hey cgroza, you should let ppl know it been sorted so they don't come explain what you already know... go under thread tools and click "mark thread as solved" ;)

---

### Post by Tony Flury on 2010-10-18
> **cgroza said:**
> I got it. No function was called. Just a accidentally misplaced raw_input(). Thanks.
The function calls itself in case the user gives bad input. So the function starts again and gives the user another chance and so on.

In my opinion it is far better to use loops rather than recursion for these sorts of thing - recursuion has it uses, but i think it is the wrong solution for just reprompting users to enter the right value.

---

### Post by simeon87 on 2010-10-18
> **Tony Flury said:**
> In my opinion it is far better to use loops rather than recursion for these sorts of thing - recursuion has it uses, but i think it is the wrong solution for just reprompting users to enter the right value.

This also makes sense because a function is if you want to call a piece of code from multiple locations elsewhere in the code. This is not what you want to do, you simply want to do something again. Which is why you can use a while loop. Recursion should not be used here because there is nothing to recurse on, the recursive call here simply means 'do it again'.

---

### Post by Vox754 on 2010-10-18
> **simeon87 said:**
> This also makes sense because a function is if you want to call a piece of code from multiple locations elsewhere in the code. This is not what you want to do, you simply want to do something again. Which is why you can use a while loop. Recursion should not be used here because there is nothing to recurse on, the recursive call here simply means 'do it again'.
I agree.

Incidentally, I found a pretty example right in the Python documentation: [4.7.1. Default Argument Values](http://docs.python.org/tutorial/controlflow.html#default-argument-values)

```

def ask_ok(prompt, retries=4, complaint='Yes or no, please!'):
    while True:
        ok = raw_input(prompt)
        if ok in ('y', 'ye', 'yes'):
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise IOError('refusenik user')
        print complaint

```

---

### Post by cgroza on 2010-10-25
Thanks for the tips. Lately im using loops because of your advice.

---

