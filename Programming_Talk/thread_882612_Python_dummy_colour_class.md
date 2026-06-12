---
title: "Python dummy colour class"
date: 2008-08-07
forum: Programming Talk
---

### Post by soxs on 2008-08-07
Hi, I just started to learn Python (2.5) and I got around one thing that doesn't stop bothering me.

I tried to make a colo(u)r (dummy) class whichwill return me string in a give colour. To do that properly, I tried to do it like:

```
 class Colour(object):
    """
        returns colo(u)red text
    """
    def red(self,str):
        return "\033[31m"+string+"\033[0m"
    def green(self,str):
        return "\033[32m"+string+"\033[0m"
    def blue(self,str):
        return "\033[34m"+string+"\033[0m"
    def lightblue(self,str):
        return "\033[31m"+string+"\033[0m"
```

And I want it to call like:
Colour.green()
but I am only able to call it like
Colour().green()

Is there a way to make that possible without setting it to a local variable?
Another option would be to make a module, but I don't know how.

---

### Post by Bachstelze on 2008-08-07
Usually, classes are not used directly, and work is done on *instances* of those classes:

```

class Colour(object):
    """
        returns colo(u)red text
    """

    def __init__(self, text="") :
        self.__text = text

    def red(self) :
        return "\033[31m"+self.__text+"\033[0m"
    def green(self):
        return "\033[32m"+self.__text+"\033[0m"
    def blue(self):
        return "\033[34m"+self.__text+"\033[0m"
    def lightblue(self):
        return "\033[31m"+self.__text+"\033[0m"

bar = Colour("bar")
print bar.green()

```

That way, you can for example have multiple instances of the Colour class, each with a different text :

```
bar = Colour("bar")
baz = Colour("baz")
print bar.green()
print baz.blue()

```

That's the whole point of OOP. Otherwise, you can as well use standard procedural programming ;)

---

### Post by Wybiral on 2008-08-07
> **HymnToLife said:**
> That's the whole point of OOP. Otherwise, you can as well use standard procedural programming ;)

Yeah, this design would make more sense as functions than a class... Although you might want to put it into a module (especially if you want to support other means of coloring things).

---

### Post by soxs on 2008-08-07
> **HymnToLife said:**
> Usually, classes are not used directly, and work is done on *instances* of those classes:

```

class Colour(object):
    """
        returns colo(u)red text
    """

    def __init__(self, text="") :
        self.__text = text

    def red(self) :
        return "\033[31m"+self.__text+"\033[0m"
    def green(self):
        return "\033[32m"+self.__text+"\033[0m"
    def blue(self):
        return "\033[34m"+self.__text+"\033[0m"
    def lightblue(self):
        return "\033[31m"+self.__text+"\033[0m"

bar = Colour("bar")
print bar.green()

```

That way, you can for example have multiple instances of the Colour class, each with a different text :

```
bar = Colour("bar")
baz = Colour("baz")
print bar.green()
print baz.blue()

```

That's the whole point of OOP. Otherwise, you can as well use standard procedural programming ;)

I know I could do it like that, but this is a little "unhandy".
How can I make a module, what EXACTLY is a module?? I am just starting to get used to python and lack knowledge in almost every respect

---

### Post by Wybiral on 2008-08-07
> **soxs said:**
> I know I could do it like that, but this is a little "unhandy".
How can I make a module, what EXACTLY is a module?? I am just starting to get used to python and lack knowledge in almost every respect

Make a folder, then put a file named "__init__.py"

Put your code in that file.

Then you can, from a lower directory, use "import foldername" and "foldername.function()"

You can have your color functions in this module, not in a class since they don't need to share data or remain as an instance.

(if it's a small enough module, you can just make a file "something.py" and use "import something" from the same directory)

---

### Post by soxs on 2008-08-07
this was exactly the style of usage I was searching for

---

