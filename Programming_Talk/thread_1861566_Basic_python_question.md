---
title: "Basic python question"
date: 2011-10-15
forum: Programming Talk
---

### Post by WinterMadness on 2011-10-15
this has got me pretty confused.

im looking at code here, and im tryng to translate it to another language and i cant figure out what this syntax means.

```
if not (self.neighbor.advance() == True
```

self is like this
neighbor is a variable used in the constructor as far as I can tell, and advance is a function that gets recursed.

How on earth can a variable like neighbor use advance() like that, what does it even mean?

---

### Post by Bachstelze on 2011-10-15
Looks like you are not familiar with object-oriented programming. Read up on it.

---

### Post by WinterMadness on 2011-10-15
No, im familiar with OOP. I am not familiar with how a variable can use a function in that way. Ive never seen it done that way, ive been programming for a few years. 

if I were to take a variable of the type int and use a dot after it, I get functions associated with the int type, not functions that are part of the current class. Same concept. I want to know what python is actually doing here. Please dont give dismissive answers. They dont help anyone, ever.

Keep in mind advance() is a function IN THE CLASS from THAT code, hence the "recursion" I talked about.

---

### Post by Bachstelze on 2011-10-15
Show the code then, because what you say is not very clear...

---

### Post by WinterMadness on 2011-10-15
Constructor of the class(I assume):
```
def __init__(self, col, neigh):
       self.row = 1
       self.column = col
       self.neighbor = neigh
```


Code that exists in the class 
```
   def advance(self):
   # moves queen one row ahead, or fails and resets
       if self.row < numcolumns:
          self.row = self.row + 1
          return self.findSolution()

       if not (self.neighbor.advance() == True):
          return False
```

Where the constructor code is, is in fact the first time the term neighbor comes up. the self.neighbor.advance() is probably some kind of short hand(im guessing). But im not familiar with python much at all.

---

### Post by Bachstelze on 2011-10-15
The constructor assigns to self.neighbor the value of the parameter neigh. neigh can be anything, so if it is of some type that provides an advance() method, self.neighbor.advance() will invoke that method.

---

### Post by WinterMadness on 2011-10-15
okay, so it seems that its probably not recursing there, and the datatype has a function associated with it known as advance()

any idea what type that may be? Im looking on google and im not having much luck, thanks for the help as well

I use the type function to figure out and it just says <type 'instance'>

---

### Post by cgroza on 2011-10-15
You need to dig deeper in that code.
I would start by looking for a place where the class that receives the argument is instantiated. I would expect its argument instantiation to be somewhere around there.

---

### Post by WinterMadness on 2011-10-15
```
 def **[COLOR="Red"][SIZE="3"]canAttack[/COLOR][/SIZE]**(self, testRow, testColumn):
   # supposed to return true if I can be attacked by my neighbor
       if self.row == testRow:
          # print "I can attack my own row"
          return True

       columnDiff = testColumn - self.column
       if ((self.row + columnDiff) == testRow) or ((self.row - columnDiff) == testRow):
          # print "I can attack on the diagonal"
	  return True

       **[SIZE="3"]result = self.neighbor.canAttack(testRow, testColumn)[/SIZE]**
       return result
```

Theres more code. Keep in mind, every bit of code ive shown thus far is part of the same class.

so as far as instantiation goes, it hasnt been yet, and the constructor code was already posted. Sorry, but I dont know python.

---

### Post by cgroza on 2011-10-15
That code does not instantiate any class.

---

### Post by WinterMadness on 2011-10-15
I didnt say it did... Im just asking what its doing because I am translating the code to another language, and im stuck on the syntax of python.

---

### Post by JDShu on 2011-10-15
What do you not understand? It looks like neighbor is an attribute of whatever that class is. An attribute can be anything, an int, a string, or an instantiation of a user defined class. If that attribute happens to have a method, then you can call that method.

---

### Post by WinterMadness on 2011-10-15
> **JDShu said:**
> What do you not understand? It looks like neighbor is an attribute of whatever that class is. An attribute can be anything, an int, a string, or an instantiation of a user defined class. If that attribute happens to have a method, then you can call that method.

The function its calling is part of the class that im trying to translate.

example:

```
class queen:

   def __init__(self, col, neigh):
       self.row = 1
       self.column = col
     **[SIZE="4"]  self.neighbor = neigh[/SIZE]**
    
   def [SIZE="4"][COLOR="Red"]canAttack(self, testRow, testColumn):[/COLOR][/SIZE]
   # supposed to return true if I can be attacked by my neighbor
       if self.row == testRow:
          # print "I can attack my own row"
          return True

       columnDiff = testColumn - self.column
       if ((self.row + columnDiff) == testRow) or ((self.row - columnDiff) == testRow):
          # print "I can attack on the diagonal"
	  return True

       result = self**[COLOR="Black"][SIZE="3"].neighbor[COLOR="Red"].canAttack[/COLOR][/SIZE][/COLOR]**(testRow, testColumn)
       return result
```

I dont understand the syntax of whats happening. As you can clearly see, there is a function called canAttack. There is a variable IN THE EXACT SAME CLASS AS THE ONE IM WORKING ON called neighbor, thats called in the constructor.

How can a variable call a function like that? 

I dont know how else to put this. There is some kind of recursion going on, and ive never seen code that allowed a variable to call a function that does not belong to it.

So to make this even clearer, lets assume that everything im talking about is in the same class(because thats how it is in ALL the code ive shown), lets say you had a variable of type int named x. you also programmed your OWN function that does something called getSomething()

Essentially what I see happening is x.getSomething();

the function getSomething does NOT belong to x, and in most languages this code couldnt possibly work. However, I can assure you the code(THE PYTHON CODE) im looking at not only compiles but actually works. 
So again, how can neighbor call the function canAttack()?

---

### Post by Vaphell on 2011-10-15
oh man

somewhere in the program you most likely have

neigh = SomeClass( args )
q = Queen( a, b, neigh )

so the neighbor variable you see inside the queen class is a reference to a different object, that happens to have canAttack() and advance() methods. My bet is that it could be any chess piece though i don't understand why Queen doesn't inherit from some abstract ChessPiece class.

---

### Post by WinterMadness on 2011-10-15
If this helps, ill just post the entire code. I didnt want to do this because I thought people would assume that I was just looking for them to do everything for me, when im just looking for one thing. Thankfully the code isnt very long.

```
[SIZE="3"]import sys

# definitions needed for older python versions
# True = 1
# False = 0

class queen:

   def __init__(self, col, neigh):
       self.row = 1
       self.column = col
       self.neighbor = neigh
    
   def canAttack(self, testRow, testColumn):
   # supposed to return true if I can be attacked by my neighbor
       if self.row == testRow:
          # print "I can attack my own row"
          return True

       columnDiff = testColumn - self.column
       if ((self.row + columnDiff) == testRow) or ((self.row - columnDiff) == testRow):
          # print "I can attack on the diagonal"
	  return True

       result = self.neighbor.canAttack(testRow, testColumn)
       return result

   def advance(self):
   # moves queen one row ahead, or fails and resets
       if self.row < numcolumns:
          self.row = self.row + 1
          return self.findSolution()

       if not (self.neighbor.advance() == True):
          return False

       self.row = 1
       # print "Q back at (" + str(self.column) + "," + str(self.row) + ")"
       result = self.findSolution()
       return result


   def findSolution(self):
   # searches for solution

       # print "trying (" + str(self.column) + "," + str(self.row) + ")"
       while self.neighbor.canAttack(self.row, self.column):
           if not self.advance():
              return False
       return True


   def display(self):
   # prints out position of all queens

       self.neighbor.display()
       print "Q at (" + str(self.column) + "," + str(self.row) + ")"

class sentinelqueen:

   def canAttack(self, testRow, testColumn):
       # print "Sentinel queens cannot attack"
       return False

   def findSolution(self):
       return True

   def advance(self):
       # print "Sentinel queens cannot advance"
       return False

   def display(self):
       pass

# MAIN PROGRAM CODE

if len(sys.argv) > 1:
   numcolumns = int(sys.argv[1])
else:
   numcolumns = 8

Q = sentinelqueen()

for x in range (1,numcolumns+1):
   Q = queen(x, Q)
   result = Q.findSolution()

if result:
   Q.display()
else:
   print "No solution."[/SIZE]
```

---

### Post by JDShu on 2011-10-15
There is no recursion. The neighbor attribute is just another piece on the chessboard. That piece happens to also have a method named canAttack.

---

### Post by satsujinka on 2011-10-15
> **WinterMadness said:**
> I didnt say it did... Im just asking what its doing because I am translating the code to another language, and im stuck on the syntax of python.

It's not the python syntax that's screwing with you. The person who wrote that code is just completely insane.

---

### Post by WinterMadness on 2011-10-16
Well, I figured it out. Thanks to everyone who tried to help.

The lack of specified types in Python can really be confusing sometimes. Later on in the code, the queen type was instantiated and actually passed its self as an argument, and that cleared everything up for me. Weird.

---

### Post by nvteighen on 2011-10-16
> **WinterMadness said:**
> 
The lack of specified types in Python can really be confusing sometimes. Later on in the code, the queen type was instantiated and actually passed its self as an argument, and that cleared everything up for me. Weird.

This wouldn't have been really better if it was C or C++... I mean, you'd know the name of the type, but you'd still have to backtrack what *neigh* is supposed to be.

Today's lesson: people should document their code, specially if they're handing it out to other people or publishing it somewhere.

---

### Post by ofnuts on 2011-10-16
> **nvteighen said:**
> This wouldn't have been really better if it was C or C++... I mean, you'd know the name of the type, but you'd still have to backtrack what *neigh* is supposed to be.

Today's lesson: people should document their code, specially if they're handing it out to other people or publishing it somewhere.Somehow, you always hand out the code to yourself, 6 months later, and lacking sleep, and so should comment accordingly all these clever things that are written when your brain in in top gear.

---

