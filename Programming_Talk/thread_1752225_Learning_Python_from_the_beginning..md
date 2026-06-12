---
title: "Learning Python from the beginning."
date: 2011-05-07
forum: Programming Talk
---

### Post by irv on 2011-05-07
I have done some programing in the past, and have decided to learn Python. I have python installed and if I start python and type in code at the prompt everything work great. But if I do the code in a text editor save the file as a .py make it executable and then try to run it in a terminal this is what I get.
> irv@irv-Inspiron-1521:~/py-files$ ./random.py
./random.py: line 5: import: command not found
./random.py: line 7: syntax error near unexpected token `('
./random.py: line 7: `for cntr in range(1,15):'
 
The code is this:
```
import random
# print 14 random integers
for cntr in range(1,15):
print random.randint(1,10)
```
What am I doing wrong? or what am I missing?

---

### Post by cgroza on 2011-05-07
You are missing a shebang, a piece of data that tells the os how to manage that file.
Ubuntu tries to interpret it wish bash. You need python.
Add this at the beginning of your file:

```
#!/usr/bin/env python
```

It should work.

---

### Post by trollger on 2011-05-07
I believe that the first line should be telling Ubuntu/Linux where python is installed usually like this

#!/usr/bin/python

I see you beat me to it.

---

### Post by sudoalb on 2011-05-07
I do not really know the meaning of the errors there, but I could make your code work as this: 
[PHP]#!/usr/bin/python
import random
# print 14 random integers
for cntr in range(1,15):
    print random.randint(1,10)[/PHP]

and 
[PHP]
python test.py 

me@me:~/python$ python test.py
2
2
7
9
9
9
9
4
2
2
3
7
9
8[/PHP]

---

### Post by simeon87 on 2011-05-07
> **sudoalb said:**
> I do not really know the meaning of the errors there, but I could make your code work as this: 
[PHP]#!/usr/bin/python
import random
# print 14 random integers
for cntr in range(1,15):
    print random.randint(1,10)[/PHP]

and 
[PHP]
python test.py 

me@me:~/python$ python test.py
2
2
7
9
9
9
9
4
2
2
3
7
9
8[/PHP]

If you execute it like that, 'python test.py', then the '#!/usr/bin/python' is not necessary because python already receives test.py as argument. If you wish to execute the script as stand-alone script, using '/', then you do need to add that line.

---

### Post by sudoalb on 2011-05-07
> **simeon87 said:**
> If you execute it like that, 'python test.py', then the '#!/usr/bin/python' is not necessary because python already receives test.py as argument. If you wish to execute the script as stand-alone script, using '/', then you do need to add that line.

Thanks.

---

### Post by cgroza on 2011-05-07
> **sudoalb said:**
> I do not really know the meaning of the errors there, but I could make your code work as this: 
[PHP]#!/usr/bin/python
import random
# print 14 random integers
for cntr in range(1,15):
    print random.randint(1,10)[/PHP]and 
[PHP]
python test.py 

me@me:~/python$ python test.py
2
2
7
9
9
9
9
4
2
2
3
7
9
8[/PHP]
Those errors are spit from bash trying to interpret a python script.
It's is like reading chinese in latin.

---

### Post by irv on 2011-05-07
Ok I see what I was missing so my code is this now:
```
#!/usr/bin/env python
#=======================================
# random.py
# Module example using the random module
#=======================================
import random
# print 14 random integers
for cntr in range(1,15):
	print random.randint(1,10)
```

and here is my error now:
> irv@irv-Inspiron-1521:~/py-files$ ./random.py
Traceback (most recent call last):
  File "./random.py", line 6, in <module>
    import random
  File "/home/irv/py-files/random.py", line 9, in <module>
    print random.randint(1,10)
AttributeError: 'module' object has no attribute 'randint'

my error seem to be in the import random, This should be a built in Module.

---

### Post by irv on 2011-05-07
Now when I go right into python and run it I get this:
```
irv@irv-Inspiron-1521:~/py-files$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import random
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "random.py", line 9, in <module>
    print random.randint(1,10)
AttributeError: 'module' object has no attribute 'randint'
>>> 

```

---

### Post by cgroza on 2011-05-07
> **irv said:**
> Now when I go right into python and run it I get this:
```
irv@irv-Inspiron-1521:~/py-files$ python
Python 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import random
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "random.py", line 9, in <module>
    print random.randint(1,10)
AttributeError: 'module' object has no attribute 'randint'
>>> 

```
You need to use random.randrange(1,10)
The error says that randint does not exists in that module, so you can't use it.

---

### Post by irv on 2011-05-07
> **cgroza said:**
> You need to use random.randrange(1,10)

My problem is it will not import random.

---

### Post by cgroza on 2011-05-07
> **irv said:**
> My problem is it will not import random.
Just by looking at the traceback, random is imported fine.
OK, I see it, the error occurs during the import.

---

### Post by tgm4883 on 2011-05-07
> **irv said:**
> My problem is it will not import random.

Out of curiosity, is your filename random.py? If so, you might try changing that.

:EDIT:

A quick test here shows that is likely the issue. Rename the file and don't forget to delete random.pyc

---

### Post by cgroza on 2011-05-07
Ok, to solve the problem, rename your source file from random.py to some other name(ex: my_random.py).

---

### Post by cgroza on 2011-05-07
> **tgm4883 said:**
> Out of curiosity, is your filename random.py? If so, you might try changing that.

:EDIT:

A quick test here shows that is likely the issue. Rename the file and don't forget to delete random.pyc
Beat me to it.:):)

---

### Post by irv on 2011-05-07
made the change and this is what I get:
>  File "./random.py", line 6, in <module>
    import random
  File "/home/irv/py-files/random.py", line 9, in <module>
    print random.randrange(1,10)
AttributeError: 'module' object has no attribute 'randrange'


---

### Post by tgm4883 on 2011-05-07
> **irv said:**
> made the change and this is what I get:

change it back to randint, and see my above post

---

### Post by cgroza on 2011-05-07
> **irv said:**
> made the change and this is what I get:
Did you remove the random.pyc too?

---

### Post by irv on 2011-05-07
That was it, I renamed it.
> irv@irv-Inspiron-1521:~/py-files$ ./random-test.py
3
3
5
3
3
5
2
1
3
9
6
9
4
9


What a way to start to learn a new language. But I guess it was a good lesson learn. Thanks for all the help with this one. I will mark it solved.

---

### Post by tgm4883 on 2011-05-07
> **irv said:**
> That was it, I renamed it.


What a way to start to learn a new language. But I guess it was a good lesson learn. Thanks for all the help with this one. I will mark it solved.

Yep, the thing is you basically were calling your own module. Looking at it another way, you just found out how to create a module and import it :)

---

### Post by irv on 2011-05-07
> **tgm4883 said:**
> Yep, the thing is you basically were calling your own module. Looking at it another way, you just found out how to create a module and import it :)
Yes, that is a good way to look at it. I remember some years ago taking some class in computer design, and we were working on some trainer using machine code. We had one trainer that wasn't working right. We ended up tearing it apart and testing some of the chips and we found a bad one. Change it and everything worked. That was back in the days when you would change chips on a board. Now we just change the board.
Thanks again for the help.

---

