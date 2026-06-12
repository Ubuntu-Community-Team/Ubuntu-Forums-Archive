---
title: "Python: @staticmethod decorator"
date: 2010-10-19
forum: Programming Talk
---

### Post by CaptainMark on 2010-10-19
Im having trouble understanding the static method decorator, im a beginner and in the book im reading the static method decorator doesnt seem to do anything, there is some code in the book and it demonstrates the static methods which makes the decorator seem essential so i took it out to test and the code runs the same.
Are they just to make the static method more human readable or is this just a bad example or am i missing something else??
```
# Classy Critter
# Demonstrates class attributes and static methods

class Critter(object):
    """A virtual pet"""
    total = 0

    @staticmethod   
    def status():
        print("\nThe total number of critters is", Critter.total)
        
    def __init__(self, name):
        print("A critter has been born!")
        self.name = name
        Critter.total += 1
```forgot to mention, all the main text does is create an object Critter and invoke its status() method

---

### Post by StephenF on 2010-10-19
Regular methods can't be called without an instance.

Critter.status() can though and it can be called before any instances are created.

---

### Post by CaptainMark on 2010-10-20
but in this code i changed it so the first line of the main text prints the result of Critter.status() and it still runs and prints 0 critters, with or without the @staticmethod decorator

---

### Post by Tony Flury on 2010-10-20
test your code with this :

```

Critter.status()
a = Critter("a")
Critter.status()
b = Critter("b")
Critter.status()

```

With the static method in place and you can call status on the class (and not on "a" or "b" instances.

With the staticmethod decorator removed - the above code will not work, and status is only available as method on an instance

---

### Post by CaptainMark on 2010-10-21
This makes things worse, it works fine with the static method decorator removed (see below, ive used a terminal to cat it then run it so you can see) but according to all ive been told it shouldnt, i know what im supposed to do but i dont like not understanding why, ```
mark@mark-desktop:~/Documents/programming/tests$ cat classy_critter.py 
# Classy Critter
# Demonstrates class attributes and static methods

class Critter(object):
    """A virtual pet"""
    total = 0
    
    def status():
        print("\nThe total number of critters is", Critter.total)
        
    def __init__(self, name):
        print("A critter has been born!")
        self.name = name
        Critter.total += 1

#main
Critter.status()
a = Critter("a")
Critter.status()
b = Critter("b")
Critter.status()

input("\n\nPress the enter key to exit.")
mark@mark-desktop:~/Documents/programming/tests$ python3 classy_critter.py 

The total number of critters is 0
A critter has been born!

The total number of critters is 1
A critter has been born!

The total number of critters is 2


Press the enter key to exit.
mark@mark-desktop:~/Documents/programming/tests$ 

```

---

### Post by Queue29 on 2010-10-21
I never use @staticmethod since @classmethod is the one that actually behaves the way I want.

Anyway, here's some additional toy code that you can try to understand. 

```

class Critter(object):
        """A Virtual Pet"""
        total = 0 # class variable

        @classmethod
        def class_status(cls):
            print("The Total Number of Critters is: " + str(cls.total))

        @staticmethod
        def static_status():
            print("The Total Number of Critters is: " + str(Critter.total))
            
        def normal_status(self):
            print("The Total Number of Critters is: " + str(Critter.total))

        def noargs_status():
            print("The Total Number of Critters is: " + str(Critter.total))

        def __init__(self, name):
            print("A critter named: " + name + " has been born!")
            self.name = name
            Critter.total = Critter.total+1

if __name__ == "__main__":
    Critter.class_status() # should be 0
    a = Critter("a")
    Critter.class_status() # should be 1
    b = Critter("b")
    Critter.class_status() # should be 2
    
    c = Critter("c")
    Critter.static_status() # should be 3

    d = Critter("d")
    d.normal_status()       # should be 4

    e = Critter("e")
    Critter.noargs_status() # should fail
    e.noargs_status() # should fail
    
    Critter.normal_status() # should fail

```

---

### Post by Buttons840 on 2010-10-21
> **CaptainMark said:**
> This makes things worse, it works fine with the static method decorator removed (see below, ive used a terminal to cat it then run it so you can see) but according to all ive been told it shouldnt, i know what im supposed to do but i dont like not understanding why, ```
mark@mark-desktop:~/Documents/programming/tests$ cat classy_critter.py 
# Classy Critter
# Demonstrates class attributes and static methods

class Critter(object):
    """A virtual pet"""
    total = 0
    
    def status():
        print("\nThe total number of critters is", Critter.total)
        
    def __init__(self, name):
        print("A critter has been born!")
        self.name = name
        Critter.total += 1

#main
Critter.status()
a = Critter("a")
Critter.status()
b = Critter("b")
Critter.status()

input("\n\nPress the enter key to exit.")
mark@mark-desktop:~/Documents/programming/tests$ python3 classy_critter.py 

The total number of critters is 0
A critter has been born!

The total number of critters is 1
A critter has been born!

The total number of critters is 2


Press the enter key to exit.
mark@mark-desktop:~/Documents/programming/tests$ 

```

To my knowledge a class is just a name space really(?).  That's beside the point though.

Try calling a.status() and you'll get an error saying that 0 arguments were expect and 1 given.  I think one idea you might be missing is that static class method can be called using the class (Critter.status()) before any instances are created, but *static methods can, and often are, called using instances of the class (such as a.status()).*  As you have seen, calling a.status() does not work without the decorator.

---

