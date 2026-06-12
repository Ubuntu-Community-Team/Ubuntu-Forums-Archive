---
title: "Python 2.6: Running other .py?"
date: 2011-04-12
forum: Programming Talk
---

### Post by BlackRat90 on 2011-04-12
Hey, 
I was wondering if there is a function, or something, that would allow me to run another .py file from the script I am running? Sort of like "import", but being able to do it more then once.

Sort of like classes in Java or C, that allow you to break up the program into parts and have all the parts reference each other?

I have found semi-functional ways to do this using import by:
```

import stuff
...(Runs the stuff file)
del stuff
continues program, 
but being able to do "import stuff" again

```

Anyhow, I'm just curious for an more effective method.

---

### Post by sanguinoso on 2011-04-12
You can write classes in python. For example, ```
#!/usr/bin/python                                                               

class Test:
    one = 1

    def add_num(self,num):
        return self.one + num


print Test.one

tmp = Test()
tmp.one = 2
print tmp.add_num(3)

```

Self in python is almost like this in java. As you can see I create a new Test object set its one property to two (lol). Then call the add_num function. Run this to see the results.

---

### Post by BlackRat90 on 2011-04-12
I see what your saying. Its not quiet what I was thinking, but it did give me a better idea.

I had the idea to create a module which would define the action of the whole code as a function.
Module Greet
```

def intro(name,age):
     print "Hello",name,"who is",age,"years old!"
     print "My name is Bob!"
```

The script:
```

import Greet
myname = raw_input("Whats your name?")
myage = raw_input("Whats your age?")
Greet.intro(myname,myage)
```

What do you think about doing something like that? :p

---

### Post by sanguinoso on 2011-04-12
Good! You made a excellent conclusion from my example, that way you can define extra classes and methods and put them in other modules and import them just like you did. Much cleaner code that way don't you think?

---

### Post by BlackRat90 on 2011-04-12
Indeed, is will allow me and my friend to work on each part of the game we are building with out needing to constantly be integrating and merging code!

Now I can build with the Crafting module, while he works on the Fighting module!

---

### Post by LemursDontExist on 2011-04-12
If you're working on a collaborative project, I would strongly recommend you look into some sort of versioning software.  It will make your life immensely easier.

I personally like Git.

---

### Post by BlackRat90 on 2011-04-12
Ill look into it!
Thanks

---

