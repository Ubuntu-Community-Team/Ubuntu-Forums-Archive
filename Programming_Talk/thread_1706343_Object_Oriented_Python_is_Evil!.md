---
title: "Object Oriented Python is Evil!"
date: 2011-03-13
forum: Programming Talk
---

### Post by kevin11951 on 2011-03-13
I have been learning Python for the last few weeks using "A Byte of Python" (Python 2 version), and I understood everything and was amazed how easy Python was...  Until chapter 11...

...Object Oriented Programming with Python!

I am so lost its not even funny!  

Here is the example I am working with to try and understand it:

[PHP]
class SchoolMember:
'''Represents any school member.'''
def __init__(self, name, age):
self.name = name
self.age = age
print '(Initialized SchoolMember: %s)' % self.name
def tell(self):
'''Tell my details.'''
print 'Name:"%s" Age:"%s"' % (self.name, self.age),
class Teacher(SchoolMember):
'''Represents a teacher.'''
def __init__(self, name, age, salary):
SchoolMember.__init__(self, name, age)
self.salary = salary
print '(Initialized Teacher: %s)' % self.name
def tell(self):
SchoolMember.tell(self)
print 'Salary: "%d"' % self.salary
class Student(SchoolMember):
'''Represents a student.'''
def __init__(self, name, age, marks):
SchoolMember.__init__(self, name, age)
self.marks = marks
print '(Initialized Student: %s)' % self.name
def tell(self):
SchoolMember.tell(self)
print 'Marks: "%d"' % self.marks
t = Teacher('Mrs. Shrividya', 40, 30000)
s = Student('Swaroop', 22, 75)
print # prints a blank line
members = [t, s]
for member in members:
member.tell() # works for both Teachers and Students
[/PHP]

Does anyone have any tips for learning Object Oriented programming?

---

### Post by bapoumba on 2011-03-13
Moved to PT.

---

### Post by lykeion on 2011-03-13
Man, Python code without indentation is really a pain to read, but I'm not gonna comment on the code (I think your book does that already).

As a Java developer I find OO natural, but I can understand that people used to procedural programming can't make any sense of it at first. And most of the simple schoolbook examples of OO aren't really helpful either. It's mostly in larger programming projects that you can see the benefits of OO.

I only browsed through this article briefly, but it seems like a good intro to OO for Python programmers: [http://www.voidspace.org.uk/python/articles/OOP.shtml](http://www.voidspace.org.uk/python/articles/OOP.shtml)

---

### Post by cgroza on 2011-03-13
At the beginning think of the class as an real life object. Lets take an animal, a dog.
A dog can bark, walk, eat, chase cats...

Thats it. This simplifies things a lot for me. If this feature was absent I would go crazy calling functions to modify the state of global variables..

---

### Post by Vaphell on 2011-03-13
it's very simple.
SchoolMember is an abstract class that holds things common for both subclasses (Teacher, Student) so you don't have to duplicate code for each subclass - namely name, age, _init_() that fills data fields in and tell() that prints out info about the object. Teacher and Student are further upgraded to provide additional class-specific details like salary and marks - as you can see their versions of _init_() and tell() invoke SchoolMember versions of _init_() and tell() first to cover the basics and then fill in additional data.
```
class Teacher(SchoolMember):
  def __init__(self, name, age, salary): <- _init_ of Teacher
    SchoolMember.__init__(self, name, age) <- this is _init_ of parent class reused
    self.salary = salary <- this is Teacher specific bit
```


```
t = Teacher('Mrs. Shrividya', 40, 30000)
s = Student('Swaroop', 22, 75)
```
here 2 objects are created - first one is Teacher, second - Student. Parameters match those listed in _init_ definition and are used as defined to fill the blanks (remember that in python all functions that work with instance of the class have default 'self' pointing to the instance as 1st param in their definition, actual parameters start from position #2)

```
members = [t, s]
```
create a list made of these 2 objects
```
for member in members:
  member.tell()
```
for each elem in the list use elements own tell() function to print out complete info - Teacher.tell() for t and Student.tell() for s.

---

### Post by Quake on 2011-03-13
Yeah, Objects can be daunting at first, it took me a while to grab the Concept.

Think about a Revenue department, put it in a box. That box can be created as many time as possible to make different tasks with the same people calculating the revenue.

Example: 
Imagine a Revenue box named: bob. The box contains all the financial data and people to do the job.

What if you want to calculate the financial revenue of Mary? Well, you can create a a revenue box named Mary. This box will contains all the financial data and people to do the job.

As you can see, we can create as many revenue boxes without rewriting the methods to do those two jobs.

Sorry if my English is hard to follow as it's not my first language.

---

### Post by juancarlospaco on 2011-03-13
I use Randomness Oriented Python programming...

---

### Post by LemursDontExist on 2011-03-14
> **kevin11951 said:**
> Does anyone have any tips for learning Object Oriented programming?

My main suggestion would be, don't force the issue!  This code looks as if it's trying to teach class inheritance, which, while sometimes very useful, is best learned when you need it, rather than in some abstract example.  The key concept from inheritance is that you can take an existing class and modify or extend it to make a new one if you need to.  Remember that, and you can come back and learn how to do it when you need it!

An object is just a discrete name space with attached functions which you can make copies of.  It's a useful tool for avoiding code duplication, and for making self-contained, easily testable code.

Contrary to what some people think(such as the people who made Java), object oriented programming should not be a programming style which you learn, and then apply to every single problem you meet.  Objects are useful tools for writing good code, and that's all.  Learn the idea of objects, and try to be alert for places where it's a useful tool, but, again, don't force it!

---

### Post by kpkeerthi on 2011-03-14
It takes years to learn & apply proper OOP. Stick with it.

---

### Post by andrew1992 on 2011-03-14
Have you had any experience with OOP before, or are you learning it for the first time with Python? And could you tell us what do you and don't understand so far?

---

### Post by kevin11951 on 2011-03-14
> **andrew1992 said:**
> Have you had any experience with OOP before, or are you learning it for the first time with Python? And could you tell us what do you and don't understand so far?

Python is the first language I am learning, and this is the first time I am learning Python itself...

I am learning using "A Byte of Python", and I have been able to get through the entire book and under stand most of it (except OOP)...  I have written example scripts that use if..else statements, os.system calls, variables, raw_input/input, and functions...

---

### Post by kevin11951 on 2011-03-14
Here is one of the more complex ones i've written so far (well, complex for me anyway):

edit: Forgot to mention what this does, its for mapping network drives in Windows...

[PHP]def mount():

    letter = str.lower(raw_input('\nEnter Drive Letter\n(You may also enter * for automatic assignment): '))

    if letter == '*':

        pass

    else:

        letter = letter + ':'

    server = raw_input('\nEnter Server Host: ')

    share = raw_input('\nEnter Share Name: ')

    persistent = raw_input('\nWould you like this share to be "persistent"? (y/n): ')

    if persistent == 'y':

        persistent = 'yes'

    else:

        persistent = 'no'

    print '\nPlease Wait...\n'

    import os
    
    os.system(r'net use {0} \\{1}\{2} /persistent:{3}'.format(letter,server,share,persistent))

    raw_input('Press <enter> to exit...')

print '\nThis tool will map the specified network drive.'

cont = raw_input('\nAre you sure you want to continue? (y/n): ')

if cont == 'y':
    mount()
else:
    pass[/PHP]

---

### Post by andrew1992 on 2011-03-14
Alright, that all looks good. So when it comes to OOP specifically then, like with your first post, is there anything in particular that stumps you about the concept? For example:

[LIST]
[*]Do you think you understand what a class is and when it would be beneficial to implement one?
[*]Do you understand the difference between a "function" and a "method"?
[*]Do you understand the difference between global, class, instance, and local variables?
[/LIST]
And so on. Share with us what you are comfortable with and uncomfortable with! :)

---

### Post by kevin11951 on 2011-03-14
> **andrew1992 said:**
> Alright, that all looks good. So when it comes to OOP specifically then, like with your first post, is there anything in particular that stumps you about the concept? For example:

[LIST]
[*]Do you think you understand what a class is and when it would be beneficial to implement one?
[*]Do you understand the difference between a "function" and a "method"?
[*]Do you understand the difference between global, class, instance, and local variables?
[/LIST]
And so on. Share with us what you are comfortable with and uncomfortable with! :)

I guess I am lost on the first one, fuzzy on the second, and pretty good with the third (except class)...

Also, I don't understand the __stuff__ all over the place, plus the "self" thing...

---

### Post by cgroza on 2011-03-14
> **kevin11951 said:**
> I guess I am lost on the first one, fuzzy on the second, and pretty good with the third (except class)...

Also, I don't understand the __stuff__ all over the place, plus the "self" thing...
The self prefix makes the variable global within the class.

---

### Post by andrew1992 on 2011-03-14
> **kevin11951 said:**
> I guess I am lost on the first one, fuzzy on the second, and pretty good with the third (except class)...

Also, I don't understand the __stuff__ all over the place, plus the "self" thing...

Alright, well that's a good place to start then. As pointed out by some of the other members of the forum, a class is a rather convenient way of representing **objects** throughout a program. For example, let's say you are making a 2-D platform game that has many of the same type of enemies (for example the good ol' Goombas from the Mario games).  At any time in the game, there will likely be several Goombas roaming about. Instead of manually having to create a swarm of variables to represent all the properties of the different Goombas, and to save the hassle of trying to keep track of them all, it would just be easier to store them into a Goomba **class**!  The Goomba object might have certain properties: position, state (i.e. walking, jumping, etc), and perhaps some various others. The Goomba might also have some sort of actions that change its properties: jumping, dying, etc. These would be functions defined inside the class called **methods** that directly change the state of the Goomba, like its position. After defining the Goomba class, every time we want to create a Goomba, all we have to do is this:
```
newGoomba = Goomba()
```
Wasn't that easy? newGoomba is what is called an **instance** of the Goomba **class**. In this way, you can think of a **class** as a blueprint or prototype for a type of object that does nothing until an **instance** is created, which is a specified implementation of that object. 

After creating an instance of the Goomba class, you can do whatever you'd like with it:
```

newGoomba.walk_left()
newGoomba.jump()
newGoomba.kill()

```
by defining the internal workings of an object only once, everything else is just taken care of afterwards! You tell your program only once what is meant by a jump. 

Leaving aside some technical details, the above example was used just to show the benefit of using classes. Read through that and post back if you have any questions on it, and if we're good to go we can get into some more details with this '__ __' business.

---

### Post by forrestcupp on 2011-03-14
Suffer through it. Object Oriented ideas are used in a lot of languages. If you learn it in Python, it will make learning other languages, like C++, Java, or C#, much easier later.

---

### Post by kevin11951 on 2011-03-14
My first attempt:

[PHP]
class Dog:
    def Bark(self, words):
        
        import os
        
        os.system('espeak "{0}"'.format(words))
                
Dog().Bark('Hello World!')
[/PHP]

edit: added __init__:

[PHP]
class Dog:
    def __init__(self, words):
        
        self.words = words
        
    def Bark(self):
        
        import os
        
        os.system('espeak "{0}"'.format(self.words))
                
Dog('Hello World!').Bark()
[/PHP]

---

### Post by andrew1992 on 2011-03-14
> **kevin11951 said:**
> My first attempt:

[PHP]
class Dog:
    def Bark(self, words):
        
        import os
        
        os.system('espeak "{0}"'.format(words))
                
Dog().Bark('Hello World!')
[/PHP]

edit: added __init__:

[PHP]
class Dog:
    def __init__(self, words):
        
        self.words = words
        
    def Bark(self):
        
        import os
        
        os.system('espeak "{0}"'.format(self.words))
                
Dog('Hello World!').Bark()
[/PHP]

Well, I'm glad you tried using the __init__ method. Remember a couple of things:
- You should create a dog first!
```
puppy = Dog("Hello, world!")
```
- Although in this case, passing words into __init__ gets the job done, if we want our brand new puppy to be able to bark something other than just a hello to the world, it might be a better idea to have "words" as an argument for the Bark method instead:
```

def Bark(self, words):
    print words

```

I wasn't really sure what you were trying to do with the os.system call, but if you just want to print the dogs barked words to the screen, print does exactly that.

---

### Post by Arndt on 2011-03-14
> **forrestcupp said:**
> Suffer through it. Object Oriented ideas are used in a lot of languages. If you learn it in Python, it will make learning other languages, like C++, Java, or C#, much easier later.

GUI interface packages are usually built in an object oriented way. I'm not sure if the best way is to learn object orientation is by using such a GUI package, or to be prepared when you go there.

---

### Post by andrew1992 on 2011-03-14
How about the following class definition:

```

class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self, words):
        print words

```

This allows for greater flexibility! Can you see why?

```

bigDog = Dog("Hoover")
smallDog = Dog("Fancy Pants")

```

Now you can create many dogs, and distinguish them by their names! The name attribute can give you control over what the dog's bark sounds like.  For example later on, if you don't know exactly what dog you're dealing with:
```

if dog.name == "Hoover":
    dog.bark("ROOOOUUUGHHHH")
else:
    dog.bark("yaaaap!")

```

It might be hard at this point to visualize in advance how to best prepare your objects, but try to get into the habit of thinking ahead and seeing how your objects might play into the rest of your program!

EDIT: I should clarify that the last bit of code I wrote wouldn't work with just the code I wrote above; it is there simply to show you that you might not always know exactly what dog you're working with (for example, a function that takes a dog as an argument), and so using instance variables like self.name can help you identify which object you're working with :)

---

### Post by kevin11951 on 2011-03-14
.

---

### Post by andrew1992 on 2011-03-14
> **kevin11951 said:**
> Where exactly would I put "puppy = Dog("Hello, world!")", and how would I call it?
You can put it wherever you need it, as long as it's after the class definition! When you want to make the dog actually bark, you would just do (with your class definition):

```

puppy.Bark()

```

And with my class definition, where I said bark should take an argument:

```

puppy.bark("Hello, world!")

```

---

### Post by andrew1992 on 2011-03-14
The brilliant thing about object oriented programming is that, once you come to terms with it (the hardest part indeed!), it is very much like dealing with real-life objects. Using the Dog example, consider this dialogue between two friends at school:

"Aw man, one of my dogs was barking all night, it was so annoying."
"Which one was barking?"
"Fancy Pants."
"Oh yeah, that's an annoying bark alright."

See? Just like in our programming example, the second speaker was able to determine the sound of the dogs bark because of its name! Most of the time OOP can be likened to real life situations.

---

### Post by cgroza on 2011-03-14
> **kevin11951 said:**
> My first attempt:

[PHP]
class Dog:
    def Bark(self, words):
        
        import os
        
        os.system('espeak "{0}"'.format(words))
                
Dog().Bark('Hello World!')
[/PHP]edit: added __init__:


Imports go at the top of the file. There is no reason in the world to put them in functions or classes.

---

### Post by LemursDontExist on 2011-03-14
> **cgroza said:**
> The self prefix makes the variable global within the class.

Actually, 'self' isn't special in any way, it's just a convention.  When you have a method of a class it gets passed the object itself as the first variable (unless you declare them as class methods or static methods). So:

```
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self, words):
        print "{0} barks '{1}'".format(self.name, words)
```

and

```
class Dog:
    def __init__(puppy, name):
        puppy.name = name

    def bark(puppy, words):
        print "{0} barks '{1}'".format(puppy.name, words)
```

behave identically.

That said, using 'self' to refer to the object is a very good convention, and it would be pretty silly not to do it.

---

### Post by kevin11951 on 2011-03-15
I know more than I did yesterday, and I will know more tomorrow...


How about this one:

[PHP]class Cat:
    def __init__(self, name):
        self.name = name

    def meow(self, words):
        print self.name, 'said', words

pk = Cat('pk')

pk.meow('MEOW!')[/PHP]

The idea is to create a "Cat" called PK, and make it say "MEOW!"...

Does the "pk = Cat('pk')" line create a new instance (of Cat?), or am I misunderstanding?

---

### Post by Tony Flury on 2011-03-15
> **kevin11951 said:**
> I know more than I did yesterday, and I will know more tomorrow...


How about this one:

*.... code deleted - see above ....*

The idea is to create a "Cat" called PK, and make it say "MEOW!"...

Does the "pk = Cat('pk')" line create a new instance (of Cat?), or am I misunderstanding?

Yes - that is exactly right.

---

### Post by andrew1992 on 2011-03-15
> **kevin11951 said:**
> I know more than I did yesterday, and I will know more tomorrow...


How about this one:

[PHP]class Cat:
    def __init__(self, name):
        self.name = name

    def meow(self, words):
        print self.name, 'said', words

pk = Cat('pk')

pk.meow('MEOW!')[/PHP]

The idea is to create a "Cat" called PK, and make it say "MEOW!"...

Does the "pk = Cat('pk')" line create a new instance (of Cat?), or am I misunderstanding?

This is excellent! You're getting the hang of this.  That line sure does create a new instance of Cat. The great thing about classes is you can have as many instances as you'd like:

```

firstCat = Cat("Felix")
secondCat = Cat("Sammy")
thirdCat = Cat("Garfield")

```

And so on. Of course, you could pick better variable names to store the cats ;)

---

### Post by andrew1992 on 2011-03-15
> **LemursDontExist said:**
> Actually, 'self' isn't special in any way, it's just a convention.  When you have a method of a class it gets passed the object itself as the first variable (unless you declare them as class methods or static methods). So:


It does have special meaning, let's not try to confuse the original poster. I know that using the name "self" is just a convention (I've seen people use "me" or "this" for those coming from a C++ or C# background), but some name has to be used as the first argument of methods to carry out this same purpose. So let's just go with "self is very important". 

The "self" pointer is used to distinguish between local and instance variables. For example, consider the following two cases:

```

class Dog:
    def __init__(self, name):
        self.puppyName = name

    def bark(self, words):
        print self.puppyName + " says: " + words

```

```

class Dog:
    def __init__(self, name):
        puppyName = name

    def bark(self, words):
        print puppyName + " says: " + words

```

Would both of these work? If not, which one, and why not?

---

### Post by cgroza on 2011-03-15
> **LemursDontExist said:**
> Actually, 'self' isn't special in any way, it's just a convention.  When you have a method of a class it gets passed the object itself as the first variable (unless you declare them as class methods or static methods). So:

```
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self, words):
        print "{0} barks '{1}'".format(self.name, words)
```and

```
class Dog:
    def __init__(puppy, name):
        puppy.name = name

    def bark(puppy, words):
        print "{0} barks '{1}'".format(puppy.name, words)
```behave identically.

That said, using 'self' to refer to the object is a very good convention, and it would be pretty silly not to do it.

Yes you are right, I wanted to highlight that not putting self as a prefix, the variable will become local in the function.

---

### Post by cgroza on 2011-03-15
> **andrew1992 said:**
> It does have special meaning, let's not try to confuse the original poster. I know that using the name "self" is just a convention (I've seen people use "me" or "this" for those coming from a C++ or C# background), but some name has to be used as the first argument of methods to carry out this same purpose. So let's just go with "self is very important". 

The "self" pointer is used to distinguish between local and instance variables. For example, consider the following two cases:

```

class Dog:
    def __init__(self, name):
        self.puppyName = name

    def bark(self, words):
        print self.puppyName + " says: " + words

``````

class Dog:
    def __init__(self, name):
        puppyName = name

    def bark(self, words):
        print puppyName + " says: " + words

```Would both of these work? If not, which one, and why not?
The second would not work because puppyName is a local variable inside __init__. The bark() has no way to know what that is.

---

### Post by andrew1992 on 2011-03-15
> **cgroza said:**
> The second would not work because puppyName is a local variable inside __init__. The bark() has no way to know what that is.

That's correct. Let's just make sure Kevin is all good with this ;)

---

### Post by kevin11951 on 2011-03-15
> **andrew1992 said:**
> That's correct. Let's just make sure Kevin is all good with this ;)

I have been doing experiments with OOP in Python all day, and this is my latest creation:

Also, the mixed syntax of "," "+" and .format is just me messing around...

[PHP]# Allows you to create a "Human" object, and "born", "eat", and "die" it...

class Human:
    
    population = 0
    
    def __init__(self, name):
        self.name = name
        
    def born(self):
        print self.name, 'has been born...'
        Human.population += 1
        print 'The number of people is:', Human.population
        print
        
    def eat(self, food):
        print self.name, 'has eaten', food + '...'
        self.food = food
        print
        
    def die(self):
        print self.name, 'has died from eating {0}...'.format(self.food)
        Human.population -= 1
        print 'The number of people is:', Human.population
        print
        
kevin = Human('Kevin')

kevin.born()

kevin.eat('pizza')

marco = Human('Marco')

marco.born()

kevin.die()

raw_input('Press enter to exit...')[/PHP]

Produces:

```

Kevin has been born...
The number of people is: 1

Kevin has eaten pizza...

Marco has been born...
The number of people is: 2

Kevin has died from eating pizza...
The number of people is: 1

Press enter to exit...

```

---

### Post by Vaphell on 2011-03-16
nice :)
i think you should merge _init_() with born() because logically they describe pretty much the same event and _init_ can print out the happy news just as well - unless you go into minute details that construction of human object happens 9 months before the birth and those methods really need to be separate ;-)

---

### Post by andrew1992 on 2011-03-16
Looks like you're getting the hang of this! A quick pointer:

- Although this is arguably not a programming tip, it's best to always think about what kind of stuff you can put in your __init__ method so you don't have to call certain methods manually. Is a human ever "initialized" without being born first? ;)

EDIT: Looks like Vaphell beat me to it :)

---

### Post by kevin11951 on 2011-03-16
Cool, I did that now, thank you...

Quick question:

What is "*self*"?  And why does everything have to have it?

---

### Post by andrew1992 on 2011-03-16
> **kevin11951 said:**
> Cool, I did that now, thank you...

Quick question:

What is "*self*"?  And why does everything have to have it?

Before I can answer this, do you know the difference between instance and local variables? See a few posts back where I gave two examples, one of which works and the other does not.

---

### Post by LemursDontExist on 2011-03-16
> **kevin11951 said:**
> Cool, I did that now, thank you...

Quick question:

What is "*self*"?  And why does everything have to have it?

When you define a method in a class, python passes the instance itself as the first argument to the method.  So, if I have a Andrew1992's class,

```
class Dog:
    def __init__(self, name):
        self.puppyName = name

    def bark(self, words):
        print self.puppyName + " says: " + words
```

Then the following are identical:

```
rover = Dog("Rover")
rover.bark("Woof!")
```

```
rover = Dog("Rover")
Dog.bark(rover, "Woof!")
```

Specifically, calling a method from an instance, passes the instance as the first argument.  So anything you could do with 'rover', you can do with 'self' inside the function declaration.  I could for instance define a new class:

```
class BadDog:
    def __init__(self, name):
        self.puppyName = name

    def bark(self, words):
        print self.puppyName + " says: " + words

    def pee(self):
        print self.puppyName + " pees on the rug."

    def bark_and_pee(self, words):
        self.bark(words)
        self.pee()
```

and then:

```
>> spot = BadDog("Spot")
>> spot.bark_and_pee("Woof!")
Spot says:Woof!
Spot pees on the rug.
```

Also, as I said above, there's nothing special about 'self' as a variable name, you could make the first argument 'puppy' and it would run the same.

---

### Post by cgroza on 2011-03-16
> **LemursDontExist said:**
> When you define a method in a class, python passes the instance itself as the first argument to the method.  So, if I have a Andrew1992's class,
Also, as I said above, there's nothing special about 'self' as a variable name, you could make the first argument 'puppy' and it would run the same.

Still, it is better to follow the convention to make the code less confusing.

---

### Post by Vaphell on 2011-03-16
consider this example
[php]var = "global variable"

class Obj:
  def __init__(self):
    self.var = "object"

  def some_method(self):
    var = "local variable"
    print "some_method()"
    print "%s = %s" % ( "var", var )
    print "%s = %s\n" % ( "self.var", self.var )

  def some_other_method(self):
    print "some_other method()"
    print "%s = %s" % ( "var", var )
    print "%s = %s\n" % ( "self.var", self.var )
    
o = Obj()
o.some_method()
o.some_other_method()[/php]

output:
```
some_method()
var = local variable
self.var = object

some_other method()
var = global variable
self.var = object

```

as you can see depending on circumstances var alone produced 2 different results and only self.var was consistent. These are 3 different scopes:
- global where variable is higher in program hierarchy than the code that calls it and is usable without any declaration in the place of call
- local when variable lives only during the execution of a function to act as a temporary store of some value
- object member identified as an element of 'self', available in every place where 'self' is given

self kills any ambiguity that may arise, you see self and you can be sure that you work with object members not with local/global variables not being a part to the object itself. Self is a handle of the object you operate on, if you want to manipulate the object, you have to have that handle. Other languages often assume 'self' or 'this' implicitly and you can skip them but python devs chose the way of zero ambiguity and you have to always declare it and use it.

---

### Post by andrew1992 on 2011-03-16
So long story short on this "self" business: It is used to store information about the state of the **instance**, instead of some temporary information that gets lost after a method finishes its business. It lets the value be passed around anywhere within the instance, rather than used only inside a single method and then destroyed.

Do you have any other questions so far?

---

### Post by kevin11951 on 2011-03-17
> **andrew1992 said:**
> So long story short on this "self" business: It is used to store information about the state of the **instance**, instead of some temporary information that gets lost after a method finishes its business. It lets the value be passed around anywhere within the instance, rather than used only inside a single method and then destroyed.

Do you have any other questions so far?

Just one:  Why is Python so easy? 
# Not a real question ^

Thank you all for your help, in a few days I went from never programming a line of code to understanding OOP.  That is a testament to both Python's ease, and all of this community's help...  Thank you!

---

### Post by andrew1992 on 2011-03-17
You're quite welcome! Enjoy continuing to learn Python.

---

### Post by ikt on 2011-03-17
> **kevin11951 said:**
> I have been learning Python for the last few weeks using "A Byte of Python" (Python 2 version), and I understood everything and was amazed how easy Python was...  Until chapter 11...

...Object Oriented Programming with Python!

I am so lost its not even funny!  


Oh wow!

I'm glad I wasn't the only one who got hit like a freight train after getting through the earlier parts of a byte of python smoothly.

---

### Post by kevin11951 on 2011-03-17
> **ikt said:**
> Oh wow!

I'm glad I wasn't the only one who got hit like a freight train after getting through the earlier parts of a byte of python smoothly.

I know, and the author was so vague about the who OOP thing...  (Almost like he didn't understand it himself... ;))

---

