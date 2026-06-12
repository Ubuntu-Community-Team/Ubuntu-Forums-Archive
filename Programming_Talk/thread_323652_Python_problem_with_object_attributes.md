---
title: "Python problem with object attributes"
date: 2006-12-22
forum: Programming Talk
---

### Post by Ferio on 2006-12-22
So I've finally put myself to learn some Python; I'm following [A Byte of Python]("http://swaroopch.info/text/Byte_of_Python:Main_Page"), and now I'm in this [Class  and Object Variables section]("http://swaroopch.info/text/Byte_of_Python:Object_oriented_programming#Class_and_Object_Variables") in the OOP chapter. I already know the concept since I learnt some OOP years ago (mainly Java and .NET), so I go on and try my own Spanish version of the example:
```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Nombre del archivo: objvar.py

class Persona:
    '''Representa 1 persona.'''
    poblacion = 0    # Variable de clase
    
    def __init__(self, nombre):
        '''Inicializa los datos de la persona.'''
        self.nombre = nombre    # Variable de objeto
        print '(Inicializando %s)' % self.nombre
        
        # Cuando se crea esta persona, se añade a la población
        Persona.poblacion += 1
    
    def __del__(self):
        '''Me muero.'''
        print '%s dice adiós.' % self.nombre
        
        Persona.poblacion -= 1
        
        if Persona.poblacion == 0:
            print 'Soy el último.'
        else:
            print 'Todavía quedan %d personas.' % Persona.poblacion
            
    def di_hola(self):
        '''La persona saluda. Sí, es todo lo que hace'''
        print 'Hola, me llamo %s.' % self.nombre
        
    def cuantos_quedan(cls):
        '''Imprime la población actual.'''
        if Persona.poblacion == 0:
            print 'Nadie está vivo ahora.'
        elif Persona.poblacion == 1:
            print 'Sólo hay 1 persona aquí.'
        else:
            print 'Hay %d personas aquí.' % Persona.poblacion
    cuantos_quedan = classmethod(cuantos_quedan)
    
juan = Persona('Juan')
juan.di_hola()
Persona.cuantos_quedan()

raquel = Persona('Raquel')
raquel.di_hola()
Persona.cuantos_quedan()

juan.di_hola()
Persona.cuantos_quedan()

```
But instead of getting what was expected (as seen in the example), I get this:
```

(Inicializando Juan)
Hola, me llamo Juan
Sólo hay 1 persona aquí.
(Inicializando Raquel)
Hola, me llamo Raquel
Hay 2 personas aquí.
Hola, me llamo Juan
Hay 2 personas aquí.
Raquel dice adiós.
Exception exceptions.AttributeError: "'NoneType' object has no attribute 'poblacion'" in <bound method Persona.__del__ of <__main__.Persona instance at 0xb7ea1d4c>> ignored
Juan dice adiós.
Exception exceptions.AttributeError: "'NoneType' object has no attribute 'poblacion'" in <bound method Persona.__del__ of <__main__.Persona instance at 0xb7ea1d2c>> ignored

```
Which meaning I can't totally understand. I'm using Python 2.4, since it's the default Edgy version.

PS: please, don't tell me it's a typo, I've checked it twice and I'll feel quite ashamed :oops: Well, OK, just tell me if that's it, I'll try to behave as the mature person I am. No promise, but I'll try.

---

### Post by dwblas on 2006-12-22
Not understanding Spanish, I think you want self.poblacion instead of Persona.poblacion.  self. makes the variable global within the class.  Persona.poblacion means the program will try to import Persona and then find the variable there - in fact it would more likely be a function named poblacion.  Nothing named Persona was imported so it is a None Type.  If that doesn't work, post back.

---

### Post by Ferio on 2006-12-22
This is the output I get when I do as you say:
```

(Inicializando Juan)
Hola, me llamo Juan
Traceback (most recent call last):
  File "objvar.py", line 44, in ?
    Persona.cuantos_quedan()
  File "objvar.py", line 34, in cuantos_quedan
    if self.poblacion == 0:
NameError: global name 'self' is not defined
Juan dice adiós.
Soy el último.

```
If I have understood it right (and correct me if I am wrong, please), if I say *Persona.poblacion*, I'm speaking 'bout the class, but if I use *self.poblacion*, I'm speaking of an object. So, I can assign a different name to every object by using *self.nombre*, but keep the count of the global population by using *Persona.poblacion*. I couldn't tell what's wrong... (But that's just because I'm a Python newbie) ;)

PS: *nombre* means *name*, *Persona* means *person*, and *poblacion* means *population*; the program just creates a Person class and some objects, while keeping the count of the population. When the objects are going to be destroyed because they're not gonna be used anymore, the customized *__del__* should return a different message, depending on *poblacion*'s value, and the problem seems to be there. Maybe I'm misunderstanding something?

---

### Post by Wybiral on 2006-12-22
Yeah, I'm really rusty with spanish, if you post what the purpose of the program is it will probably be easier to tell what everything is (even without knowing spanish) and I might be able to come up with some sort of solution or alternate way of doing things.

---

### Post by dwblas on 2006-12-22
Also post what you want the output to be.  You are correct at the end of the program where you have Juan = Persona( Juan ), but everything within the class should be self.whatever.  The error on line 34 occurs because you should have
def cuantos_quedan(self, cls):  i.e add a self parameter.  Without self, the compiler thinks that it is a function outside the class.

---

### Post by Ferio on 2006-12-23
It's kinda weird, I've just checked the code with the original one again and I've found no mistake, but mine doesn't run and his does! This is the original code (taken from [A Byte of Python]("http://swaroopch.info/text/Byte_of_Python:Object_oriented_programming#Class_and_Object_Variables")):
```

#!/usr/bin/env python
# File name: objvar.py

class Person:
    '''Represents a person.'''
    population = 0                      # class variable

    def __init__(self, name):
        '''Initializes the person's data.'''
        self.name = name                # object variable
        print '(Initializing %s)' % self.name

        # When this person is created, he/she adds to the population
        Person.population += 1

    def __del__(self):
        '''I am dying.'''
        print '%s says bye.' % self.name

        Person.population -= 1

        if Person.population == 0:
            print 'I am the last one.'
        else:
            print 'There are still %d people left.' % Person.population

    def say_hi(self):
        '''Greeting by the person.

        Really, that's all it does.'''
        print 'Hi, my name is %s.' % self.name

    def how_many(cls):
        '''Prints the current population.'''
        if Person.population == 0:
            print 'Nobody is alive as of now.'
        elif Person.population == 1:
            print 'There is just one person here.'
        else:
            print 'We have %d persons here.' % Person.population
    how_many = classmethod(how_many)


swaroop = Person('Swaroop')
swaroop.say_hi()
Person.how_many()

kalam = Person('Abdul Kalam')
kalam.say_hi()
Person.how_many()

swaroop.say_hi()
Person.how_many()
```
And its output:
```

(Initializing Swaroop)
Hi, my name is Swaroop.
There is just one person here.
(Initializing Abdul Kalam)
Hi, my name is Abdul Kalam.
We have 2 persons here.
Hi, my name is Swaroop.
We have 2 persons here.
Abdul Kalam says bye.
There are still 1 people left.
Swaroop says bye.
I am the last one.
```

---

### Post by Ferio on 2006-12-23
I've just posted below the original program (in English); it just creates a Person class, and then some objects, and the class has a counter to measure population. When the objects/persons are deleted/die, they print a message using the customized *__del__*, and the global counter is reduced.

I hope it helps, all I want is to know what I've done wrong!

---

### Post by Ferio on 2006-12-23
I've just posted the original program below, but it works! I can't find a typo in my own code, and I don't know where my problem is! :-?

---

### Post by dwblas on 2006-12-23
I don't see any difference either.  This example sucks.  It is bad programming IMO, so don't waste any more time on it, as you will probably never use anything like this.  I guess the author is trying to show everyone how smart he/she is, but instead is just confusing everyone.

---

### Post by Ragazzo on 2006-12-24
It must be something advanced. Take the original example and rename swaroop to juan :)

---

### Post by Ferio on 2006-12-24
Thanks for the advice, in fact I had been trying to find the mistake for too much time before I asked here and it's been a complete waste of time. I'll try with Dive Into Python, though it seems to be slightly outdated. Wish me luck, and thank you for your help!

---

### Post by Ferio on 2006-12-24
Imagine that I do it and it doesn't work... A Python conspiracy against me? :D

---

### Post by dwblas on 2006-12-26
What doesn't work?  Dive Into Python, or trying the original program again.  Don't spend any more time on that sorry program.  Dive Into Python isn't the newest but it's  good book to learn programming with and will show you how to do everything in a general sense, i.e. no game programming, etc.  You can also try here 
[http://swaroopch.info/text/Byte_of_Python:Main_Page](http://swaroopch.info/text/Byte_of_Python:Main_Page)
and [http://www.mindview.net/Books/TIPython](http://www.mindview.net/Books/TIPython)

---

### Post by pmasiar on 2006-12-27
> **Ferio said:**
> ... learn some Python; I'm following A Byte of Python and now I'm in this Class  and Object Variables section in the OOP chapter. I already know the concept since I learnt some OOP years ago (mainly Java and .NET)

My advice is little late (I was on vacation) but better late than never.  :-)

Let me suggest you to skip OOP stuff for now. Unlike java, you can program in python using procedural approach and modules with no OO problems. You can try  OO again later when you will be more familiar with python debugging. Go and solve some simple non-OO tasks. I have some tasks in [http://learnPython.pbwiki.com/](http://learnPython.pbwiki.com/)

If you are still stuck, let me know and I look closer.

---

### Post by Ferio on 2006-12-28
I left this program apart some days ago, now I'm into different Python stages, but... It was taken from the first link you have typed. Maybe I'll try with the other one.

---

### Post by Ferio on 2006-12-28
This is the feeling I've ever had with programming, you know? I learnt some C some years ago, while in University, and every other language I've learnt after that has turned odd in the end because of the OOP approaching. It'll take me time to master it.

I'll have a look at your wiki.

---

### Post by knaveman on 2008-03-13
I know this thread is old and DEAD, but I just got to this problem in the book and spent a couple of hours working on it and finally ended up with a workaround. Just in case anyone was wondering how to make the damn thing work. I added the text in red.



> **Ferio said:**
> It's kinda weird, I've just checked the code with the original one again and I've found no mistake, but mine doesn't run and his does! This is the original code (taken from [A Byte of Python]("http://swaroopch.info/text/Byte_of_Python:Object_oriented_programming#Class_and_Object_Variables")):
```

#!/usr/bin/env python
# File name: objvar.py

class Person:
    '''Represents a person.'''
    population = 0                      # class variable

    def __init__(self, name):
        '''Initializes the person's data.'''
        self.name = name                # object variable
        print '(Initializing %s)' % self.name

        # When this person is created, he/she adds to the population
        Person.population += 1

    def __del__(self):
        '''I am dying.'''
        print '%s says bye.' % self.name

        Person.population -= 1

        if Person.population == 0:
            print 'I am the last one.'
        else:
            print 'There are still %d people left.' % Person.population

    def say_hi(self):
        '''Greeting by the person.

        Really, that's all it does.'''
        print 'Hi, my name is %s.' % self.name

    def how_many(cls):
        '''Prints the current population.'''
        if Person.population == 0:
            print 'Nobody is alive as of now.'
        elif Person.population == 1:
            print 'There is just one person here.'
        else:
            print 'We have %d persons here.' % Person.population
    how_many = classmethod(how_many)


swaroop = Person('Swaroop')
swaroop.say_hi()
[COLOR="Red"]swaroop[/COLOR].how_many()

kalam = Person('Abdul Kalam')
kalam.say_hi()
[COLOR="Red"]kalam[/COLOR].how_many()

[COLOR="Red"]del kalam[/COLOR]
swaroop.say_hi()
[COLOR="Red"]swaroop[/COLOR].how_many()
```
And its output:
```

(Initializing Swaroop)
Hi, my name is Swaroop.
There is just one person here.
(Initializing Abdul Kalam)
Hi, my name is Abdul Kalam.
We have 2 persons here.
Hi, my name is Swaroop.
We have 2 persons here.
Abdul Kalam says bye.
There are still 1 people left.
Swaroop says bye.
I am the last one.
```

---

