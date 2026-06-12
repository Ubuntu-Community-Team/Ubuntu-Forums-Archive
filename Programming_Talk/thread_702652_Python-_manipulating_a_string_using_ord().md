---
title: "Python- manipulating a string using ord()"
date: 2008-02-20
forum: Programming Talk
---

### Post by sp0nge on 2008-02-20
I'm trying to manipulate strings of user input data, using ord() to assign the decimal value to each character in the string. I can return the values, but need to understand the best way to store the decimal values, manipulate them, and return the new values to a new string.

Any input or suggestions?

---

### Post by LaRoza on 2008-02-20
> **sp0nge said:**
> I'm trying to manipulate strings of user input data, using ord() to assign the decimal value to each character in the string. I can return the values, but need to understand the best way to store the decimal values, manipulate them, and return the new values to a new string.

Any input or suggestions?

Takes a string, and returns a list of the values of each letter.
[php]
def ord2(string):
    ord2 = []
    for letter in string:
        ord2.append(ord(letter))
    return ord2
[/php]

---

### Post by Wybiral on 2008-02-20
> **LaRoza said:**
> Takes a string, and returns a list of the values of each letter.
[php]
def ord2(string):
    ord2 = []
    for letter in string:
        ord2.append(ord(letter))
    retrun ord2
[/php]

O O, good place to drop a list comprehension:

```

def ord2(string):
    return [ord(letter) for letter in string]

```

EDIT:

Also, naming the variable the same as the function might cause some confusion :)

---

### Post by LaRoza on 2008-02-20
> **Wybiral said:**
> O O, good place to drop a list comprehension:

```

def ord2(string):
    return [ord(letter) for letter in string]

```

EDIT:

Also, naming the variable the same as the function might cause some confusion :)

Thanks, I will have to investige these "list comprehensions" some more. (They are new to me)

Not to mention I misspelled "return" (fixed it)

I think declaring a local variable in a function to be the functions name is a good idea, if the language permits it. It makes sense to have the return value of the function be the function's name. 

(You can guess what language I learned that from...)

---

### Post by Wybiral on 2008-02-20
> **LaRoza said:**
> Thanks, I will have to investige these "list comprehensions" some more. (They are new to me)

Not to mention I misspelled "return" (fixed it)

I think declaring a local variable in a function to be the functions name is a good idea, if the language permits it. It makes sense to have the return value of the function be the function's name. 

(You can guess what language I learned that from...)

List comprehensions are one of my favorite features in Python. You can do some really neat stuff with them (without having to set up a bunch of loops and be stuck with variables allocated outside the loops).

As far as the variables being named after the function, I see what you're saying, it's just that when I look at it I feel like the function is returning itself (which makes me uncomfortable for some reason).

---

### Post by LaRoza on 2008-02-20
> **Wybiral said:**
> 
As far as the variables being named after the function, I see what you're saying, it's just that when I look at it I feel like the function is returning itself (which makes me uncomfortable for some reason).

I typically use that convention. As popular as OO is, I prefer to think according to structured programming first. The variable name is only returned once, and is the only return in the function. Being that the variable is never used for anything else, it keeps the code readable and structured.

(The whole convention I use is from Fortran)

---

### Post by WW on 2008-02-20
Here is an example of a function that uses ord to convert each character to an integer, adds one to the integer, and puts the result back into a string:

```

import string

def add1(s):
    """
    Create a new string in which the ord value of each character is
    increased by one.
    """
    z = [chr(ord(x)+1) for x in s]
    return string.join(z,'')

```
**chr** is used to convert the integer to a character, and **string.join** builds the string from the array of characters.

---

### Post by sp0nge on 2008-02-20
Ok so there is a lot of great information here, but I'm still new to this so it's a bit over my head. 

```
z = [chr(ord(x)+1) for x in s]
    return string.join(z,'')
```

This sounds like we're on the same page. What I don't understand is how to associate 'z' with the sting entered by the user- Yes I do. Thanks for the input. Helped me a lot!

---

### Post by LaRoza on 2008-02-20
> **sp0nge said:**
> Ok so there is a lot of great information here, but I'm still new to this so it's a bit over my head. 

```
z = [chr(ord(x)+1) for x in s]
    return string.join(z,'')
```

This sounds like we're on the same page. What I don't understand is how to associate 'z' with the sting entered by the user.

We are writting functions to do the task. To use mine (for example):

[php]
s = ord2(raw_input("Enter string: "))
[/php]

Assuming the definition of ord2 is in the file (or imported), s will be the list of numbers.

---

### Post by ghostdog74 on 2008-02-20
```

>>> s="string"
>>> map(ord,s)
[115, 116, 114, 105, 110, 103]
>>>      

```

---

### Post by LaRoza on 2008-02-20
> **ghostdog74 said:**
> ```

>>> s="string"
>>> map(ord,s)
[115, 116, 114, 105, 110, 103]
>>>      

```

map() will be missing in the next version of Python, just to let you know.

Guido van Rossum : [http://www.artima.com/weblogs/viewpost.jsp?thread=98196](http://www.artima.com/weblogs/viewpost.jsp?thread=98196)

<edit>
Correction, it isn't going to be removed, anymore, but its behavior will change. I don't know if that matters in this instance.
</edit>

---

### Post by pmasiar on 2008-02-20
even simpler:
```


def add1(s):
    return ''.join( [chr(ord(x)+1) for x in s])

```

List comprehension is one of the coolest things in Python.

---

### Post by LaRoza on 2008-02-20
> **pmasiar said:**
> 
List comprehension is one of the coolest things in Python.

...and I just learned of them.

---

### Post by pmasiar on 2008-02-20
> **LaRoza said:**
> ...and I just learned of them.

Don't worry, I am told that other very cool Python feature is function decorators, and I have yet to truly grok them and use them in my own code (I do use decorators from libraries, like in TurboGears).

This is what I love on language like Python (and Perl has this feature, even if in lesser degree): you don't have to know the whole language (or suffer through snippets of opaque mumbo-jumbo code to set up  code you understand, like in Java) to be able to write perfectly usable code. Sometimes your beginner's Python code will be not using the best idioms, but will be perfectly understandable. And when you encounter new idiom, you can intuitively see how it works, even if you don't know yet how to make your own.

---

### Post by LaRoza on 2008-02-20
> **pmasiar said:**
> Don't worry, I am told that other very cool Python feature is function decorators, and I have yet to truly grok them and use them in my own code (I do use decorators from libraries, like in TurboGears).

This is what I love on language like Python (and Perl has this feature, even if in lesser degree): you don't have to know the whole language (or suffer through snippets of opaque mumbo-jumbo code to set up  code you understand, like in Java) to be able to write perfectly usable code. Sometimes your beginner's Python code will be not using the best idioms, but will be perfectly understandable. And when you encounter new idiom, you can intuitively see how it works, even if you don't know yet how to make your own.

I learned of the decorators recently, very cool.

The list comprehensions were easy to understand, even though I never saw them.

---

### Post by sp0nge on 2008-02-21
Thanks for all the input here, guys!

Both decorators and list comprehensions do sound interesting. I have intentions to review these once I have completed this project. This is my first original, practical program so I don't want to get ahead of myself. 

Great information, great lesson, and I'm well on my way to accomplishing my goal. Thanks for the help!

---

