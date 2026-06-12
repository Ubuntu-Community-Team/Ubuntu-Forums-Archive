---
title: "a simple question (for python)"
date: 2006-02-08
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-08
I have one class named test_class.py. I have another class called test_main.py. Following are the codes for them. I call test_class.py within test_main.py and creats an object of it. I get an error "object not callable".

Please help

```


#!/usr/bin/python
#Filename: test_class.py

class test_class:	
	def __init__(self, age):
		self.age = age		
		print self.age

```

```

#!/usr/bin/python
#Filename: test_main.py

import test_class.py

p = test_class(25)

```

---

### Post by Wallakoala on 2006-02-08
Simple:
When you import a module, you always leave the .py out.
So you would do ```
import test_class
```

---

### Post by krypto_wizard on 2006-02-08
This is the error I got.
```

 'module' object is not callable

```

I have created one class. I want to create the objects of thge first class in second file. How can I get this done ?

Any help is appreciated

[QUOTE=Wallakoala]Simple:
When you import a module, you always leave the .py out.
So you would do ```
import test_class
```[/QUOTE]

---

### Post by Wallakoala on 2006-02-08
[QUOTE=krypto_wizard]This is the error I got.
```

 'module' object is not callable

```

I have created one class. I want to create the objects of thge first class in second file. How can I get this done ?

Any help is appreciated[/QUOTE]

Oh, I see your problem. What you want to do is either one of the following:
at the top of test_main instead of "import test_class"
```
from test_class import test_class
```
basically what that does is tell it that you want to import that class from test_class
you could also do this instead of "p = test_class(25)"
```
p = test_class.test_class(25)
```
what you are doing now is telling it that you want to make "p" the module itself, which is not what you want to do. You have to tell it that you want "p" to be the class within the module.

---

### Post by krypto_wizard on 2006-02-08
thanks, it worked

is there any place where such basic questions are answered. I felt so stupid to ask that dumb question


[QUOTE=Wallakoala]Oh, I see your problem. What you want to do is either one of the following:
at the top of test_main instead of "import test_class"
```
from test_class import test_class
```
basically what that does is tell it that you want to import that class from test_class
you could also do this instead of "p = test_class(25)"
```
p = test_class.test_class(25)
```
what you are doing now is telling it that you want to make "p" the module itself, which is not what you want to do. You have to tell it that you want "p" to be the class within the module.[/QUOTE]

---

### Post by Wallakoala on 2006-02-08
It wasn't a dumb question at all. But what source are you learning python from? It might be good to pick up a book (I recommend *Learning Python* from O'reilly) because they answer these questions most of the time. There are also various tutorials on the web such as *Dive into Python* and *A Byte of Python*. Most of the time, these questions can be answered through these sources, but it never hurts to post in a forum if you cannot find the answer.

---

### Post by krypto_wizard on 2006-02-08
Thanks

[QUOTE=Wallakoala]It wasn't a dumb question at all. But what source are you learning python from? It might be good to pick up a book (I recommend *Learning Python* from O'reilly) because they answer these questions most of the time. There are also various tutorials on the web such as *Dive into Python* and *A Byte of Python*. Most of the time, these questions can be answered through these sources, but it never hurts to post in a forum if you cannot find the answer.[/QUOTE]

---

