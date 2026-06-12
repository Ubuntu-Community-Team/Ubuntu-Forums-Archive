---
title: "python advice for a C# developer..."
date: 2008-05-28
forum: Programming Talk
---

### Post by kragen on 2008-05-28
The last time I picked up python I absolutely loved it. Somehow everything was so simple, everything just worked!

Since then I've spent a great deal of time doing C# development on windows. I properly figured out how object oriented programming worked and I've started coming up with neat design patterns.

So when I re-installed Ubuntu not long ago I was really looking forward to having another go at python with my newfound knowledge of oo, but in all honesty I'm running into problems...

Compared to the rigorous "define everything" nature of C#, python is just so immensely different so and my current way of thinking really isn't working that well for me. Every now and then I do something really neat which just wouldn't have been possible in C# without loads of messing about, but the rest of the time I'm trying to do what I would have done in C#, and python is starting to look like a kids toy next to a JCB.

For example, I'm use to the practice "one file per class", I find it makes things more readable, but in python I have to put

```

import Vector
from Vector import Vector (or *)

```

at the top of my file for every class I want to use!

I'm guessing there is a better way of writing my Import statements, but should I be using fewer files or what?

Also, I've been trying to create a Vector class (as you can see above), but I cant seem to get overloads working, and without them I'm really struggling. I've just about figured out how to emulate an overload if both overloads have the same number of arguments - by testing to see what type of object I'm looking at - but I find that really ugly, especially for a language where your not supposed to have to worry about what type of object something is.

Am I missing a feature of python here, or are there better ways for dealing with problems which don't use overloads?

I get the impression that I'm in the wrong mode of thinking at the moment - I'm trying to make everything flexible and re-usable by strongly defining everything. I can see thats probably not the right thing to do, but I cant see what is!

Oh and I'm badly missing visual studio, but thats another issue...

Any tips or advice would be greatly appreciated!

---

### Post by Lau_of_DK on 2008-05-28
Hey,

I hate to sound like a broken record, but have you considered giving Lisp a go?

From a C#-Point-of-View(tm) I think there are 2 reasons to really like Python. 1) Its batteries included, so you can build powerfull apps quickly, 2) The language is more flexible including Generator Expressions and Lambdas. 

The downside to Python is, like you say, that it does feel a bit like a kids toy and it has a nasty syntax compared to C# (in my honest oppinion and you can disagree if you like).

If you can live w/o the ALL of the batteries and if you can handle a steep learning curve, with the promised result of incredible flexibility and power, you should try Lisp. I would always recommend a new comer, or someone considering trying Lisp reading the first 3 chapters of [this book]("http://gigamonkeys.com/book/") [<-Link] while playing with REPL (sorta, Lisps command prompt).

Like the overload problem you mentioned, wouldn't be a problem in Lisp, its flexible to the 10th degree.

/Lau

---

### Post by Wybiral on 2008-05-28
It sounds like you're programming C# or Java in Python... Don't. Not everything has to be in one big class. Think of the module itself as a sort of a class, more than just a namespace. Group classes together in them. Having a single class in one module seems like a waste to me.

---

### Post by xlinuks on 2008-05-28
> **kragen said:**
> The last time I picked up python I absolutely loved it. Somehow everything was so simple, everything just worked!

Since then I've spent a great deal of time doing C# development on windows. I properly figured out how object oriented programming worked and I've started coming up with neat design patterns.

So when I re-installed Ubuntu not long ago I was really looking forward to having another go at python with my newfound knowledge of oo, but in all honesty I'm running into problems...

Compared to the rigorous "define everything" nature of C#, python is just so immensely different so and my current way of thinking really isn't working that well for me. Every now and then I do something really neat which just wouldn't have been possible in C# without loads of messing about, but the rest of the time I'm trying to do what I would have done in C#, and python is starting to look like a kids toy next to a JCB.

For example, I'm use to the practice "one file per class", I find it makes things more readable, but in python I have to put

```

import Vector
from Vector import Vector (or *)

```

at the top of my file for every class I want to use!

I'm guessing there is a better way of writing my Import statements, but should I be using fewer files or what?

Also, I've been trying to create a Vector class (as you can see above), but I cant seem to get overloads working, and without them I'm really struggling. I've just about figured out how to emulate an overload if both overloads have the same number of arguments - by testing to see what type of object I'm looking at - but I find that really ugly, especially for a language where your not supposed to have to worry about what type of object something is.

Am I missing a feature of python here, or are there better ways for dealing with problems which don't use overloads?

I get the impression that I'm in the wrong mode of thinking at the moment - I'm trying to make everything flexible and re-usable by strongly defining everything. I can see thats probably not the right thing to do, but I cant see what is!

Oh and I'm badly missing visual studio, but thats another issue...

Any tips or advice would be greatly appreciated!

What you've run into runs virtually anyone who (kinda) dumps one language for a new one. I'm in the same position as you - trying to move from Java to C++, I found things I miss a lot I had/have in Java and there are features in C++ I've long been looking for but Java didn't deliver.
Thus regardless of what you're looking for - you'll always have to deal with a trade-off.
As to Visual Studio - I'm not aware of such a thing for Linux, there is Eclipse which is generally very flexible but not very intuitive, and there's NetBeans which seems to be viceversa and has actually a visual editor for GUI components "a la Borland Delphi or Visual Studio", however I prefer to code by hand the GUI.

---

### Post by kragen on 2008-05-28
Thanks for the replies guys!

I've gotta admit, programming in a small lightweight editor for once (like gedit) is very nice. In fact, its not so much the big features of VS that I'm missing (like auto-completion), its the little things, like the way pressing "Home" at the very start of a line jumps you to the first carat after the indent.

I've had a quick look at lisp and it looks interesting - its completely foreign to anything I've used before, but it seems to have good reviews. I'll definitely give it a try.

I have another more specific python question though, I tried doing this earlier

```

MyList = list()
MyList.MyProperty = 12

```

It failed and I cant work out why, I thought I was able to add properties / attributes onto classes as and when I pleased - I certainly seem to be able to do this with all the classes I create.

---

### Post by days_of_ruin on 2008-05-28
> **kragen said:**
> Thanks for the replies guys!

I've gotta admit, programming in a small lightweight editor for once (like gedit) is very nice. In fact, its not so much the big features of VS that I'm missing (like auto-completion), its the little things, like the way pressing "Home" at the very start of a line jumps you to the first carat after the indent.

I've had a quick look at lisp and it looks interesting - its completely foreign to anything I've used before, but it seems to have good reviews. I'll definitely give it a try.

I have another more specific python question though, I tried doing this earlier

```

MyList = list()
MyList.MyProperty = 12

```

It failed and I cant work out why, I thought I was able to add properties / attributes onto classes as and when I pleased - I certainly seem to be able to do this with all the classes I create.

Do "print MyList".You will see that all that does is define a as an empty list.

---

### Post by skullmunky on 2008-05-29
I'm pretty new to python too, so I try to do everything as if I was still in C++.  For the multi-file-thing, I *think* what you are supposed to do is that you put all your source files into a folder, which becomes the name of your 
"package", e.g.:

```

awesome/
   main.py
   gui.py
   logick.py
   magick.py

```

then inside each one,

```

from awesome import *

```

except you also need two more things - it does not in fact import *, which as far as i can tell from the docs is Windows' fault for some reason, so instead you have to make an __init__.py file inside awesome/ too:

```

from main import *
from gui import *
from logick import *
etc

```

the other thing you have to deal with is that main.py will get imported repeatedly which will create problems so you have to have this weird construction:

```

def main():
    #actual main function

if __name__ == 'main':
    main()

```

if someone who actually knows python can verify that, that would probably be good...

the thing that's hardest to get used to with python, after C++ et al, is that my programs don't visually look right - they're too short and don't have enough punctuation.  

About overloading - I think you can't do that, because without type signatures on functions there's nothing to overload.  

See if the existing data structures will work for you instead of having to write your own vector class; you may be able to quickly move on to fun things instead.

---

### Post by pmasiar on 2008-05-29
> **kragen said:**
> 
For example, I'm use to the practice "one file per class", I find it makes things more readable, but in python I have to put

```

import Vector
from Vector import Vector (or *)

```

at the top of my file for every class I want to use!

One file per class - is for languages like java or C#. You are not restricted like that in Python, you can share data between classes in a module if you need to. Do whatever makes sense, don't bring restrictions valid in one language into another.

Your import is wrong, use first line or second, but you don't have to use both. IMHO "import *" is so wrong: whole point is to know what module defines what name, "import *" just kills it.

> I've just about figured out how to emulate an overload if both overloads have the same number of arguments - by testing to see what type of object I'm looking at 

That's wrong. In Python, you should not ever test for type. You check if instance has methods you want to use - duck-typing.

> Oh and I'm badly missing visual studio, but thats another issue...

Get paid-for IDE like WingIDE or Komodo. TANSTAFL!

---

### Post by pmasiar on 2008-05-29
> **Lau_of_DK said:**
> 
The downside to Python is ... that it does feel a bit like a kids toy and it has a nasty syntax compared to C# (in my honest oppinion and you can disagree if you like).

Yes, I would disagree. I wonder about your sanity if you find Python syntax nasty compared with C#

and don't get me started about "toy language" badge? Google, ILM and NASA use "toy language"? IMHO it more says that you are not mature enough to judge things as they are, instead as you like/dislike them. There is nothing toylike in a language which allows me to finish my job sooner.

---

### Post by days_of_ruin on 2008-05-29
If you want to have all your modules in a separate directory,
use ```
import sys
sys.path.append("path") # folder where your modules are
import module #one of your modules
```

---

### Post by kragen on 2008-05-29
> **pmasiar said:**
> One file per class - is for languages like java or C#. You are not restricted like that in Python, you can share data between classes in a module if you need to.

Yeah, I've noticed that and its confused the hell out of me! I'm talking about things like:

```

def Main():
    print myvariable

myvariable = "Hello, World!"
Main()

```

or even,

```

class MyClass:
    def Main(self):
        print myvariable

myvariable = "Hello, World!"

cls = MyClass()
cls.Main()

```

This is worlds apart from C# / C++ where myvariable would have been out of scope. From guesswork I think I've figured out that myvariable is "global" to that module (as its not defined in a class or method), but I cant quite see why that would work, and this wouldnt:

```

def Main():
    myvariable = "hello world"

myvariable = "hello"
Main()
print myvariable

```

is the global passed by value within methods or something?

> That's wrong. In Python, you should not ever test for type. You check if instance has methods you want to use - duck-typing.

Hmm, so if I wanted to create some sort of Vector class which was capable of doing this:

```

myvec = Vector(10, 10)
anothervec = Vector(20, 20)
# I can do multiplication between vectors and ints by overriding __add__
myvec *= anothervec
# But I also want to be able to do dot (or cross) products with *
product = myvec * anothervec

```

How would you recommend doing this?

Thanks again for all the advice!
Oh yeah and...

> 
Yes, I would disagree. I wonder about your sanity if you find Python syntax nasty compared with C#

and don't get me started about "toy language" badge? Google, ILM and NASA use "toy language"? IMHO it more says that you are not mature enough to judge things as they are, instead as you like/dislike them. There is nothing toylike in a language which allows me to finish my job sooner.


lol!

---

### Post by pmasiar on 2008-05-29
> **days_of_ruin said:**
> If you want to have all your modules in a separate directory,
use ```
import sys
sys.path.append("path") # folder where your modules are
import module #one of your modules
```

I cannot warn strongly enough **against** such trickery. Whole point of importing is to know what name is coming from where, this will defeat it. Don't be lazy, spending seconds writing trivial import statement may save you hours debugging name clash. Python is happy to redefine any name to any type - just module what expected certain methods might be unhappy after name clash.

Consider it to be a price for dynamic typing: you better know what your names are, and where they came from.

---

### Post by days_of_ruin on 2008-05-29
> **pmasiar said:**
> I cannot warn strongly enough **against** such trickery. Whole point of importing is to know what name is coming from where, this will defeat it. Don't be lazy, spending seconds writing trivial import statement may save you hours debugging name clash. Python is happy to redefine any name to any type - just module what expected certain methods might be unhappy after name clash.

Consider it to be a price for dynamic typing: you better know what your names are, and where they came from.

How is that hiding where they came from?
I don't think you got what I was suggesting.
You would still manually import every module.Only thing this does is allow
you to import modules that aren't in the current directory, something every
python programmer does all the time with the standard modules.

---

### Post by Can+~ on 2008-05-29
> **kragen said:**
> This is worlds apart from C# / C++ where myvariable would have been out of scope.

It's the same deal on C:

[PHP]#include <stdio.h>
#include <string.h>

char myvariable[20]; // <-- global

void myFunction()
{
	printf("myvarialbe is: %s", myvariable);
}

int main(int argc, char** argv)
{
	strcpy(myvariable, "Hello world");
	
	myFunction();
	
	return 0;
}[/PHP]

*GASP!* myvariable is a global.

Let's try with a class on C++

[PHP]#include <iostream>

using namespace std;

string myvariable="hello world"; // <-- global

class FancyClass
{
	public:
	void myFunction()
	{
		cout << "myvariable is: " << myvariable; // Out of scope? Yeah, you wish.
	}
};

int main(int argc, char **argv)
{
	FancyClass myFancyInstance;
	
	myFancyInstance.myFunction();
	
	return 0;
}
[/PHP]

*DOUBLE GASP!* it works too.

---

### Post by kragen on 2008-05-29
> **Can+~ said:**
> It's the same deal on C:

[PHP]#include <stdio.h>
#include <string.h>

char myvariable[20]; // <-- global

void myFunction()
{
	printf("myvarialbe is: %s", myvariable);
}

int main(int argc, char** argv)
{
	strcpy(myvariable, "Hello world");
	
	myFunction();
	
	return 0;
}[/PHP]

*GASP!* myvariable is a global.

Let's try with a class on C++

[PHP]#include <iostream>

using namespace std;

string myvariable="hello world"; // <-- global

class FancyClass
{
	public:
	void myFunction()
	{
		cout << "myvariable is: " << myvariable; // Out of scope? Yeah, you wish.
	}
};

int main(int argc, char **argv)
{
	FancyClass myFancyInstance;
	
	myFancyInstance.myFunction();
	
	return 0;
}
[/PHP]

*DOUBLE GASP!* it works too.

Hmm, well by your very same logic, why does:

```

def Main():
    myvariable = "hello world"

myvariable = "hello"
Main()
print myvariable

```

print out "hello", not "hello world"?

I'm not really a C++ programmer, I just see a little of it at work. I didn't know C++ allowed you to declare variables outside the scope of a class.
Its certainly not allowed in C# :P

I am getting there with python though - I'm having a go at the programming challenge - Its slow, but its definitely becoming less awkward.

---

### Post by skeeterbug on 2008-05-29
> **kragen said:**
> Hmm, well by your very same logic, why does:

```

def Main():
    myvariable = "hello world"

myvariable = "hello"
Main()
print myvariable

```

print out "hello", not "hello world"?

I'm not really a C++ programmer, I just see a little of it at work. I didn't know C++ allowed you to declare variables outside the scope of a class.
Its certainly not allowed in C# :P

I am getting there with python though - I'm having a go at the programming challenge - Its slow, but its definitely becoming less awkward.


```

def Main():
    myvariable = "hello world"

```

That is a local variable. Use module.variable to access the global.

In a module named test_f
```

def Main():
    test_f.myvariable = "hello world"

test_f.myvariable = "hello"
Main()
print test_f.myvariable

```

---

### Post by Can+~ on 2008-05-30
> **kragen said:**
> Hmm, well by your very same logic, why does:

```

def Main():
    myvariable = "hello world"

myvariable = "hello"
Main()
print myvariable

```

print out "hello", not "hello world"?

Because python, instead of just jumping to edit a global variable, it creates it's own inside the scope. On the other hand, if you don't create a variable with the same name, and just go ahead and print it, Python will look inside the local scope, then the global scope.

As you can see, this is a security measure to avoid accidental changing, say that you had a global which holds a certain piece of data, you, by accident, name a variable with the same name inside a function, that would be catastrophic, debug hell. On the other hand, the guy (like you) that expected the global value to change, will also suffer from this, but now you know.

If you want to summon a global variable, then:

[PHP]def Main():
	global myvariable # ,variable2, variable3, ... variableN
	myvariable += " world" # You could also use myvariable = "hello world", this is just for a demonstration.

myvariable = "hello"
Main()
print myvariable[/PHP]

[http://docs.python.org/ref/global.html](http://docs.python.org/ref/global.html)

---

