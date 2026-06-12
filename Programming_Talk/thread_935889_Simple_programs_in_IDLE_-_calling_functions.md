---
title: "Simple programs in IDLE - calling functions?"
date: 2008-10-02
forum: Programming Talk
---

### Post by elbarto_87 on 2008-10-02
Hi all,
I have created 2 simple programs in IDLE. "encrypt" moves the characters of a string by a certain specified amount and "aencrypt" lists all the possiblites that a string could represent.

I have saved the 2 files in the default idle directory. When I start idle, I have to open each script run the module before I can call the functions from the interpreter. I was just wondering if there was an easier way to do this? Obviously it is no big deal since I am only dealing with 2 functions in this instance, but If I have a library of scripts it would be convenient to import all the scripts so all the commands were available.

I have included my 2 scripts just for kicks. Im sure you could do this in less lines as I have seen in the python challenge but im still learning the python syntax and think this is a good exercise to learn with.

Thanks

Elbarto

```
def encrypt(string=0,num_shift=0):
    if string == 0 and num_shift == 0:
        string = raw_input("Enter the string to shift:")
        num_shift = int(raw_input("Enter phase shift [pos or neg] :")) 
    new_word = ""
    for x in string:
             
        if ord(x)>=65 and ord(x)<=90:
            new_ord = (ord(x)+num_shift)
            if new_ord > 90:
                new_ord = new_ord - 26
            elif new_ord < 65:
                    new_ord = new_ord + 26
        elif ord(x)>=97 and ord(x)<=122:
            new_ord = (ord(x)+num_shift)
            if new_ord > 122:
                new_ord = new_ord - 26
            elif new_ord < 97:
                    new_ord = new_ord + 26
        else:
            new_ord = ord(x)

        new_word = new_word + chr(new_ord)
    print(new_word)
```


```
def aencrypt(string=0):
    if string == 0:
        string = raw_input("Enter the string to interate solution:")
    for i in range(1,27):
        new_word = ""
        for x in string:            
            if ord(x)>=65 and ord(x)<=90:#in capital range
                new_ord = (ord(x)+i)
                if new_ord > 90:
                    new_ord = new_ord - 26
                elif new_ord < 65:
                    new_ord = new_ord + 26
                    
            elif ord(x)>=97 and ord(x)<=122:#in lower case region
                new_ord = (ord(x)+i)
                if new_ord > 122:
                    new_ord = new_ord - 26
                elif new_ord < 97:
                    new_ord = new_ord + 26
            else:
                new_ord = ord(x)
            new_word = new_word + chr(new_ord)
        print new_word, "{Letter Shift Required = ",  i, " or ", i - 26, "}"
       
```

---

### Post by Greyed on 2008-10-02
Just move them into a single file.  Import that file then call each one as if it were from a class.

---

### Post by elbarto_87 on 2008-10-02
Thanks for the response Greyed.
Is there anyway I can keep them in seperate files but asign them to thier own class or something so I could do something along the lines of

```
from myclass import*
```

Or have I misunderstood the purpose of classes?

---

### Post by Greyed on 2008-10-02
Take a look at how to lay out a class as a directory instead of a single file.

---

### Post by pmasiar on 2008-10-02
IIUC, you can do (assuming code is in modules called as those functions, and is in the same directory as the program calling it):

```

from encrypt import encrypt
from aencrypt import aencrypt

#your code here

```

---

### Post by Erdaron on 2008-10-02
You can put files containing those functions into Python/Lib/site-packages, and then call them from any python script by using the import statement.

You can also put a .pth file in the site-packages folder, this file containing a path to where you keep those files. Name of the .pth file does not have to correspond to actual library names. In fact, it can point to a location of multiple libraries.

What we're dealing with here is functions from a library (or module). Which is basically another program from which you can pluck the functions you need.

A class is a whole other bag of fish. It's a data structure with functions designed to deal with that specific structure. It's kind of like an uber-function, in that it itself can contain multiple functions (and they are now called methods). If all you need is a couple of straight-forward operations, then I think using a class is overkill.

---

### Post by Greyed on 2008-10-02
Classes simple to setup in Python.  In fact one of the example uses is as a simple data container.

[http://www.python.org/doc/2.6/tutorial/classes.html#odds-and-ends](http://www.python.org/doc/2.6/tutorial/classes.html#odds-and-ends)

Besides, when one is doing an encrypt and possible decrypt those are related and would probably end up in a class anyway.  

Regardless what I was thinking of was a package, as described here:
[http://www.python.org/doc/2.6/tutorial/modules.html#packages](http://www.python.org/doc/2.6/tutorial/modules.html#packages)

It is essentially a class on the file system and is exactly what he wants; the ability to have a single import but have the code in different files.  Personally I would not use packages since jumping around a single file with related functions/classes is far easier for me than trying to jump around dozens, if not hundreds, of files.

---

### Post by elbarto_87 on 2008-10-08
Thanks alot for all of the responses. I had a look at the link you posted greyed, I think that will work for me nicely as that is pretty much exactly what I am looking for. I think I have a lot to learn before I attempt to learn classes. 


Thanks for all your help,

Regards Elbarto

---

