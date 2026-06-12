---
title: "Absolute Python beginner"
date: 2010-07-02
forum: Programming Talk
---

### Post by Mike128 on 2010-07-02
Hi all,

Last night I finally sat down and started to read through guides to Python, I installed it and set about seeing what I could make it do with my own very limitted programming experience.

I must say I was very pleased with the simplicity of it, I don't have so much experience elsewhere that it seemed alien to me at all. The thing is I've no idea how to do a loop at all.

attached is what I've come up with so far, I intend to expand it considerably to do a lot more stuff like statistical analysis, velocity calculations and things but I figured start with the easy stuff first.

Could someone with a few moments let me know how to do this? I just want it to start from the beginning again if the user wishes to run another calculation.

Thanks muchly

-Mike128

---

### Post by Bachstelze on 2010-07-02
You want a while loop:

[php]#area/volume calculator
#really crappy I know
#don't hate me


choice = 1

#intro message
print "hi there!"

#main loop
while choice == 1:
    print "what would you liked calculated?"
    print "1 area"
    print "2 volume"
    print "0 quit"
    #determines what we're all about
    calculation = input(">")

    #this section is if we're doing areas
    if calculation == 1:
        print "what kind of shape is it?"
        print "1 rectangle"
        print "2 circle"
        print "3 triangle"
        shape = input(">")
        if shape == 1:
            height = input("Enter the height: ")
            width = input("Enter the width: ")
            arear = width*height
            print "The area is",arear
        elif shape == 2:
            radius = input("what is the radius?")
            areac = 3.14159*(radius**2)
            print "The area is",areac
        elif shape == 3:
            height = input("Enter the height: ")
            width = input("Enter the base: ")
            areat = (width*height)*0.5
            print "The area is",areat
    #this one if we're doing volumes
    elif calculation == 2:
        print "what kind of shape is it?"
        print "1 cuboid"
        print "2 sphere"
        shape = input(">")
        if shape == 1:
            height = input("Enter the height: ")
            width = input("Enter the width: ")
            length = input("Enter Length: ")
            areac = width*height*length
            print "The area is",areac
        elif shape == 2:
            radius = input("Enter the radius: ")
            areas = 3.14159*(radius**2)*(4/3)
            print "The area is",areas
    #after the result is printed I want to be able to give the option to begin again
    #unfortunately I have no idea how to do that.
    print "Thankyou, would you like another?"
    print "1 yes"
    print "2 no"
    choice = input(">")

print "Goodbye"
[/php]

Here's a simpler example to show what a while loop does:

[php]>>> n = 0
>>> while n < 10:
...     print n
...     n = n+ 1
... 
0
1
2
3
4
5
6
7
8
9
>>> 
[/php]

It's called a while loop because your program will just "loop" in it as long as the condition that follow the while keyword is true. Only when this condition becomes false is the program allowed to exit the loop. In the shor example above, it's when n becomes equal to 10. In your program, it's when choice becomes equal to anything other than 1.

The next step is to properly validate your input, because as it is, the user can do some really nasty things. ;)

---

### Post by Mike128 on 2010-07-02
Yeah I'm going for baby steps here, I was going to try and add conditions so if people start messing around by throwing in values that shouldn't be there it'll display an error message and not just go mad. 

Thanks muchly it really is appreciated :)

---

### Post by nvteighen on 2010-07-02
What Python are you using? If it's 2.x, you should use raw_input() instead of input()... The reason is that in those versions, input() is used to get a Python expression which is parsed and then stored into a string, while raw_input() just gets a normal string.

In order to understand this, please take a look at this Python shell session (don't bother about the weird version number of my Python... it's because of Debian's transition to Python 2.6):
```

ugi@UGI:~$ python
Python 2.6.5+ (release26-maint, Jun 16 2010, 12:01:44) 
[GCC 4.4.4] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> raw_input_string = raw_input("if a == b")
if a == b
>>> raw_input_string = raw_input()
if a == b
>>> input_string = input()
if a == b
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<string>", line 1
    if a == b
     ^
SyntaxError: invalid syntax
>>> input_string = input()
9 + 9
>>> input_string
18
>>> 

```

As you see whatever you type into an input() request needs to be valid Python, while raw_input() just takes the user's input literally without doing anything else.

In Python 3.x, AFAIK, input() is exactly the same as raw_input() and the raw_input() name was dropped.

---

### Post by Mike128 on 2010-07-03
I tried to do what you said nvteighen but couldn't get it to work, also I can't get any of the math commands found [http://docs.python.org/library/math.html](http://docs.python.org/library/math.html) to work. Can anyone tell me how to use them properly? I added a section that used factorials and had to look up how to define my own function to do it and I'll be damned if i'm going to work out how to define my own logs and trig stuff.

If someone could help me out again I'd be most thankful :)

---

### Post by Bachstelze on 2010-07-03
The math module is just that: a module. YOu have to import it before you can use the functions it contains. Put this at the beginning of your code:

```
import math
```

Then you can use math.sqrt(), math.exp(), etc..

---

### Post by Mike128 on 2010-07-03
ah awesome, thankyou.

---

### Post by nvteighen on 2010-07-04
> **Mike128 said:**
> I tried to do what you said nvteighen but couldn't get it to work ...

Hm... all you have to do is replace **input()** by **raw_input()**... unless you're using Python 3.x, where you should keep the code intact.

Please, check your Python version:
```

$ python --version

```

---

### Post by Mike128 on 2010-07-04
Ah cool ok, I was just being an idiot. 

Let me check I have this right, input () will allow me to enter a number or recognised python command only where as raw_input() will allow me to enter in anything I want like names and units and things?

---

### Post by Bachstelze on 2010-07-04
> **Mike128 said:**
> 
Let me check I have this right, input () will allow me to enter a number or recognised python command only where as raw_input() will allow me to enter in anything I want like names and units and things?

Technically, input() will also allow you to enter anything, but if what you enter is not a valid Python expression, your program will throw an error. raw_input() on the other hand just stores whatever you enter into a string, so you can enter whatever you want without the program going nuts.

---

### Post by Mike128 on 2010-07-04
Ok so whilst it's not a problem in the making if someone makes a mistake with the input and types out the option rather than the number assigned to it all will go wrong? (on my phone so can't check)

---

### Post by Bachstelze on 2010-07-04
> **Mike128 said:**
> Ok so whilst it's not a problem in the making if someone makes a mistake with the input and types out the option rather than the number assigned to it all will go wrong? (on my phone so can't check)

It's deeper than that. With input(), Python will just execute whatever the user throws at it. What if the user enters this?

```
import shutil; shutil.rmtree('~')
```

Do not try, it will delete your whole home directory. Python will execute this without any questions. This is why you should never use input() in Python 2.x.

---

### Post by Mike128 on 2010-07-04
Ah ok, thanks. That could have been an ****. I'll go through and sort that then., not really a worry for a while yet though

---

