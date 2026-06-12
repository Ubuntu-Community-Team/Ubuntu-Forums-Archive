---
title: "Python Question"
date: 2007-12-21
forum: Programming Talk
---

### Post by chris062689 on 2007-12-21
```
class calculator:
   total = 0
   add = " "
   def __init__(self, file=None):
      print 'Welcome to the calculator application.  Simply enter a number to add, to quit type QUIT.'
      add_prompt() # How do I get it to go to the add_prompt()
   def add_prompt(self, file=None):
      print 'Your total is currently '+total+'.'
      add = int(raw_input())
      try:
         total = int(total) + add
      except ValueError:
         if add == 'QUIT': end() #How would this go to the end()?
         else: self() #Would this go back to __init__()
   def end(self, file=None):
      print 'Your total is... '+total
calculator()

```


I just started learning python a day ago, and wanted to ask a few questions.
1) Is my code "standardized"?
2) Is it clean?
3) Is there anything you see that could be done better / more efficient?
4) How do I call the different "defs" (What would be the terminology to this?) that I have made from the __init__() one?

---

### Post by Nekiruhs on 2007-12-21
1) As far as standardization goes I'm not sure, but it looks good
2) A coulple line breaks after the end of def statments wouldn't hurt, but overall its nice
3) Instead of [PHP]print "Your total is... " + total[/PHP] (With space after ...) you could just do [PHP]print "Your total is...", total[/PHP] (Without the space) It makes it a bit more readable. Also spaces after operators makes it more readable too. As far as effiency of execution, I'm really not the guy to ask about that, I'm not sure of the algorithms.
4) The terminology is "function" or in this case a "method". Functions outside of a class (class blah()) are just called functions and are called like [PHP]foo(arg1, 3, "hi", value=False)[/PHP] Inside a class they are called methods. When you want to access a method from within the class code itself (IE another method of that class) you do [PHP]self.foo(arg1, 3, "hi", value=False)[/PHP] After you make an instance of that class [PHP]Bar = calculator()[/PHP] you would do [PHP]Bar.add_prompt(args)[/PHP]

Your code could look like this:
[PHP]
class calculator():
   total = 0
   add = ' '

   def __init__(self, file=None):
      print 'Welcome to the calculator application.  Simply enter a number to add, to quit type QUIT.'
      self.add_prompt() # Just add self after it

   def add_prompt(self, file=None):
      print 'Your total is currently', total + '.'
      add = int(raw_input())
      try:
         total = int(total) + add
      except ValueError:
         if add == 'QUIT': self.end() #Like this
         else: self.__init__() #This is how it would be done

   def end(self, file=None):
      print 'Your total is...', total

if __name__ == '__main__':
    Calc = calculator()
[/PHP]

---

### Post by LaRoza on 2007-12-21
I can see you are not used to OO programming.

Here is a small example:

[php]
class Person:
    def  __init__(self,name):
        self.name = name
    def sayName(self):
        print "Hi! I am ",self.name
[/php]

To use this class, you create an instance of it. To call a method of that class, use the . operator from the instance.
[php]
me = Person("LaRoza")
me.sayName()
[/php]

Run this, and unless I made a stupid error, it should be clear.

The __init__ method is a **contructor**.

---

### Post by chris062689 on 2007-12-21
Well, I realize I could do most of this calulator program could be done without OO programming, is that wise?

Also, I fixed up the code a bit.

```

class calculator:
	total = 0
	add = " "
	def __init__(self, file=None):
		print 'Welcome to the calculator application.  Simply enter a number to add, to quit type a character.'
	def add_prompt(self, file=None):
		print 'Your total is currently ',self.total,'.'
		self.add = raw_input()
		try:
			self.total = int(self.total) + int(self.add)
			self.add_prompt()
		except ValueError:
			if self.add == 'QUIT': self.end()
			else: self.add_prompt()
	def end(self, file=None):
		print 'Your total is... ',int(self.total)
Cal = calculator()
Cal.add_prompt()

```

---

### Post by Nekiruhs on 2007-12-21
It really doesn't hurt to be done in OOP, it works better if you want to use it in a later program, and it is good practice. Just one thing about your code though.
[PHP]
total = 3
print "Your total is...", total
# >>Your total is 3
print "Your total is... ", total
# >> Your total is..  3
[/PHP]
The comma adds the space separating for you. Don't use it before periods or where you don't want a space inserted. Take a look at the code I posted.

---

### Post by chris062689 on 2007-12-21
So I should use..
```
,
``` when I want a space..
and ```
+
``` when I don't want a space?

---

### Post by Nekiruhs on 2007-12-21
Exactly.

If you were to do
[PHP]print "Hi", "."[/PHP]
You would get
Hi .
You would want to do
[PHP]print "Hi" + "."
[/PHP]

Also in the print your total line, int(self.total) is unnecessary. total is already an int, if you wanted to add it to the string you could optionally do str(self.total) but you don't even have to do that.

You might want to read [this]("http://www.python.org/doc/essays/styleguide.html") too.

---

### Post by Martin Witte on 2007-12-22
on your question if your code is standardized: you can apply the rules in the python style guide, [http://www.python.org/dev/peps/pep-0008](http://www.python.org/dev/peps/pep-0008)

---

