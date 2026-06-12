---
title: "[Python]Why is this program behaving unexpectedly??"
date: 2011-09-23
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-09-23
```

import random,sys
a,guess,x=0,0,0
while(a!=5):
        if(x==0):
            x=int(random.random()*100)
            print x
        if (x!=guess):
            print "Enter your guess:"
            guess=raw_input("x:")
        else :
                print "Good guess :)"
                sys.exit(1)
        

        if (a==4):
            print "The rand num was ",x
            pass
        
        
        a=a+1
print guess,x

```No matter what u enter your guess is never correct... :confused:

---

### Post by Bachstelze on 2011-09-23
Because with raw_input, the input is stored in a string. You need to convert it to an int.

---

### Post by Dhiraj Thakur(Invincible) on 2011-09-23
> **Bachstelze said:**
> Because with raw_input, the input is stored in a string. You need to convert it to an int.
+1
and that was quick :P
anyway is there any other way  by which i can only have an int value from the user??

---

### Post by Bachstelze on 2011-09-23
With Python 2 you can use input(). However, this is discouraged for security reasons, because then the user can enter any Python code, it will be executed (which is why it was removed in Python 3).

---

### Post by Dhiraj Thakur(Invincible) on 2011-09-23
> **Bachstelze said:**
> With Python 2 you can use input(). However, this is discouraged for security reasons, because then the user can enter any Python code, it will be executed (which is why it was removed in Python 3).
Besides that..??

---

### Post by ofnuts on 2011-09-23
> **Dhiraj Thakur(Invincible) said:**
> Besides that..??
```

x=None
try
    x=int(raw_input('X:'))
except:
    print ('input not integer')

if x:
    .... 

```

---

### Post by karlson on 2011-09-23
> **Dhiraj Thakur(Invincible) said:**
> Besides that..??

Just for my curiosity is this a test? or there is a reason you can't use 
```

int(raw_input('x: ')

```

---

### Post by nvteighen on 2011-09-23
Python is dynamically typed... yes... but it's strongly typed too, meaning that types are not implicitly converted: things are the type they are, always. Perl, instead, is an example of weak-dynamic typed discipline; C is an example of weak-static. This means that you always have to be very careful about what type(s) functions return or take as an argument.

Be aware that, by transforming the input string to a number in just one step would allow you to reduce the guess and x variables to one single variable.

---

