---
title: "[SOLVED] Mutating Strings Within A Class (Python)"
date: 2008-07-13
forum: Programming Talk
---

### Post by Glaxed on 2008-07-13
[Edit: Finished code at the end of this post.]
Hey guys!,

I'm in the middle of writing a class that allows for more flexible string usage in Python (yes, it's possible).
Although Python implements strings **extremely** well, it's missing string mutation.
It seems as though the developers chose not to implement it (even in py3k), though for what reason, I do not know.

My problem is this; how do you re-assign the value of an object (from within the scope of a function) in a class (that inherits string properties)?
To simplify;

(class) -> string object
(class) - (function) -> modify string object

The goal is not to mutate the object (that's impossible), the goal is to re-assign the value attributed to the object.

Here is an outline;

[php]class semi_mutable_str (str):

# define a class that inherits native str properties

    def __init__(self, value):
        self.str = value

    def rm(self, pos):
        '''Remove the character in self.str at pos.'''
        new = self.str[0:pos]
        new += self.str[pos+1:len(self.str)]
        self.str = new
        del new
        return self.str

>>> variable = semi_mutable_str ("aaa aba abb bbb b a")
>>> variable
"aaa aba abb bbb b a"
>>> variable.rm(0)
>>> variable.str
"aa aba abb bbb b a"
>>> variable
"aaa aba abb bbb b a"
[/php]

Note that variable.str has been appropriately changed, but when I call variable, I get what I started with.
How do I change the value that is returned when I call 'variable'?
That is my question.

Thank you very much for reading, and your time.
Regards
[B]
EDIT[/B] -> Finished Class:
```

#!/usr/bin/env python

# Mutable strings meet Python 2.x.
# v.1.3 - vminch@gmail.com

# A very big thank-you to Lster and boblemur on Ubuntuforums!
# Because of their advice, I could piece together some hackery
# at the end to make this all work!

# Member Functions:
# rm
# rm_phr
# purge
# asgn
# asgn_r
# set
# set_phr

# Please read the documentation in each function for details, or email me.

class m_str(str):
    '''m_str is a Python 2.x class created to extend the uses of string objects.
       It inherits all of the str class's properties as well! :D.
    '''
    def __init__(self, content):
        '''Initialize the m_str.'''
        self.str = content
    
    def rm(self, pos):
        '''Remove the character in self.str at pos (position).
           Note: m_str(s) start indexing at 0.
        '''
        new = self.str[0:pos]+self.str[pos+1:len(self.str)]
        self.str = new
        del new
        return self.str
    
    def rm_phr(self, phr, new=""):
        '''Remove ALL INSTANCES of phr or char (phrase) from self.str. Leaves whitespace.
           To remove whitespace, simply obj.rm_phr(' ')
        '''
        lphr=len(phr)
        if phr in self.str:
            loc = self.str.find(phr)
            self.str = self.purge(loc, lphr)
            loc = self.str.find(phr)
            self.rm_phr(phr=phr, new=new)
        else:
            return self.str
    
    def purge(self, loc, lphr):
        '''Helpher function to the recursive self.rm_phr.
           Removes a chunk of self.str that
           starts at loc (location) is lphr (lenght of phrase) long.
        '''
        if loc == 0:
            new = self.str[lphr:len(self.str)]
        else:
            new = self.str[0:loc]+self.str[loc+lphr:len(self.str)]
        return new
            
    def asgn(self, phr, pos=0):
        '''Assign char/phr to self.str at pos.
           The existing char will be SCOOTED TO THE RIGHT.'''
        if pos == 0:
            new = phr+self.str
        else:
            new = self.str[0:pos]+phr+self.str[pos:len(self.str)]
        self.str = new
        del new
        return self.str

    def asgn_r(self, phr):
        '''Assign char/phr to self.str to the right side of the string.'''
        self.asgn(phr, pos=len(self.str))
        return self.str
    
    def set(self, pos, char):
        '''Set pos in self.str to char.
           The existing char will be deleted.
        '''
        if len(char) != 1:
            return self.str
        if pos == 0:
            new = char+self.str[1:len(self.str)]
        if pos > 0:
            new = self.str[0:pos]+char+self.str[pos+1:len(self.str)]
        self.str = new
        del new
        return self.str 
    
    def set_phr(self, pos, phr):
        '''Set pos:lphr in self.str to phr.
           The existing phr will be deleted.
        '''
        lphr = len(phr)
        if pos == 0:
            new = phr+self.str[lphr:len(self.str)]
        if pos > 0:
            new = self.str[0:pos]+phr+self.str[pos+lphr:len(self.str)]
        self.str = new
        del new
        return self.str 
            
    def __str__(self):
        return self.str

```

---

### Post by LaRoza on 2008-07-13
> **Glaxed said:**
> Hey guys!,

I'm in the middle of writing a class that allows for more flexible string usage in Python (yes, it's possible).
Although Python implements strings **extremely** well, it's missing string mutation.
It seems as though the developers chose not to implement it (even in py3k), though for what reason, I do not know.

Strings are immutable in many languages (most languages?).

---

### Post by Lster on 2008-07-13
[QUOTE=LaRoza]Strings are immutable in many languages (most languages?).[/QUOTE]

It's still an annoyance though. Coming from C, where string mutation is possible, it is sometimes quite annoying to have to create a new string instead of changing one character.

Glaxed, I think you may be referring to this function:

[http://pyref.infogami.com/__str__](http://pyref.infogami.com/__str__)

---

### Post by LaRoza on 2008-07-13
> **Lster said:**
> It's still an annoyance though. Coming from C, where string mutation is possible, it is sometimes quite annoying to have to create a new string instead of changing one character.


It makes more sense to me to return a new string using simple functions: [http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

---

### Post by Lster on 2008-07-13
[QUOTE=LaRoza]It makes more sense to me to return a new string using simple functions: [http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)[/QUOTE]

If the new string takes O(n) to create and O(n) memory to store this can change the complexity of some algorithms. But I doubt it's often critical - however you envisage it I guess! :)

Have a look at the University of Exeter algorithm on to see what I mean:

[http://www.bearcave.com/random_hacks/permute.html](http://www.bearcave.com/random_hacks/permute.html)

---

### Post by boblemur on 2008-07-13
read about __str__() methods, they are what you want if you wana not have to go object.str

for example when you go

a = "test"
a
will echo "test"

the __str__() is what does that...

rember python is smart...

>>> a = "test"
>>> a[:12]
'test'
>>> a[15:12]
''

slicing outside the string gives a blank string hence you can write your functions like this...


def rm(self,pos):
   self.str = self.str[:index] + [index + 1:]
   return self.str

def asn(self,phrase,index):
   self.str = self.str[:index] + phrase + str[index+1:]
   return self.str

---

### Post by pmasiar on 2008-07-13
Strings are immutable (exactly like integers and floats) so they can be used as dict key. List of characters is mutable (tuple is not).

---

### Post by Lster on 2008-07-13
[QUOTE=pmasiar]Strings are immutable (exactly like integers and floats) so they can be used as dict key. List of characters is mutable (tuple is not).[/QUOTE]

That's a good point. Essentially that is what a string is in C, and so if you needed those kinds of properties, maybe a list would be more appropriate... That is a small qualm I've had with Python: it is difficult to tell what complexity each function has.

---

### Post by Glaxed on 2008-07-13
I was able to make the class work exactly as I had wanted to! Thank you!

(The finished class is at the bottom of the first post!)
Should I attatch it?

---

### Post by Lster on 2008-07-13
Congrats! :KS

---

