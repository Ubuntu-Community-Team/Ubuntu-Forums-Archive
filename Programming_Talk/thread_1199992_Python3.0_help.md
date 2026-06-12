---
title: "Python3.0 help"
date: 2009-06-29
forum: Programming Talk
---

### Post by danny37415 on 2009-06-29
I've been reading A Byte of Python (the python3.0 version) and I do all the examples in them myself. I haven't had any trouble until now and was wondering if anyone could help me. I typed everything out exactly as in the book and tried to execute it and got this error.

Traceback (most recent call last):
  File "objvar.py", line 42, in <module>
    droid1 = Robot('R2-D2')
  File "objvar.py", line 14, in __init__
    print('Initializing {0}'.format(self.name))        
AttributeError: 'str' object has no attribute 'format'
Exception exceptions.AttributeError: "'str' object has no attribute 'format'" in <bound method Robot.__del__ of <__main__.Robot instance at 0xb7dd2c0c>> ignored

Then I copied and pasted the example code from the book and got the same results.


Here's the code I typed out
```

#!/usr/bin/python3.0
# Filename : objvar.py

class Robot:
    '''Represents a robot with a name'''
    
    # A class variable, counting the number of robots.
    population = 0
    
    def __init__(self, name):
        '''Initializes the data.'''
        
        self.name = name
        print('Initializing {0}'.format(self.name))        
        # When this person is created, the robot
        # adds to the population
        Robot.population += 1
        
    def __del__(self):
        '''I am dying'''
        print('{0} is being destroyed'.format(self.name))
        
        Robot.population -= 1
        
        if Robot.population == 0:
            print('{0} was the last one.'.format(self.name))
        else:
            print('There are still {0:d} robots working'.format(Robot.population))
            
    def sayHi(self):
        '''Greeting by the robot'''
        
        print('Greetings, my masters call me {0}.'.format(self.name))
        
    def howMany():
        '''Prints the current population'''
        
        print('We have {0:d} robots.'.format(Robot.population))
    
    howMany = staticmethod(howMany)
    
droid1 = Robot('R2-D2')
droid1.sayHi()
Robot.howMany()

droid2 = Robot('C-3PO')
droid2.sayHi()
Robot.howMany

print('\nRobots can do some work here.\n')
print('Robots have finished their work. So let\' destroy them.')

del droid1
del droid2

Robot.howMany()

```

Also, does anyone have any other good python tutorials I could look at?

---

### Post by Can+~ on 2009-06-29
```
-----@-------:~/Desktop$ python3 objvar.py 
Initializing R2-D2
Greetings, my masters call me R2-D2.
We have 1 robots.
Initializing C-3PO
Greetings, my masters call me C-3PO.

Robots can do some work here.

Robots have finished their work. So let' destroy them.
R2-D2 is being destroyed
There are still 1 robots working
C-3PO is being destroyed
C-3PO was the last one.
We have 0 robots.

```

No problems here.

---

### Post by danny37415 on 2009-06-29
I think I know what is wrong. I executed the script with SPE and it gives me that error. It's probably executing it with python 2.whatever that's the default on my computer. I just did it through the terminal and it worked.

Now, does anyone know how to change the which version of python is used in SPE? (Stani's Python Editor)

---

### Post by unutbu on 2009-06-29
Edit: Oops, you already figured out the problem. :) (and I don't know how to configure SPE...)

---

### Post by danny37415 on 2009-06-29
Well I know how to execute through the terminal. I just need to know how to tell SPE how to execute it using python 3.0 and not 2.5. I guess it uses the python command because when I went to do it in the terminal I had to change the executable thing with the chmod command.

Edit: Replied to soon I guess. Thanks anyways

---

