---
title: "help on runtime defined functions (python)"
date: 2007-11-19
forum: Programming Talk
---

### Post by aquavitae on 2007-11-19
I am writing a program (in python) in which I want some scripting functionalily.  In particular, I want to be able to customize get and set functions for a class at runtime, something like this:
```

class MyClass:
   def __init__(self, get_scr):
      self.get_scr = get_scr
      self.data = []

   def __getitem__(self, index):
      # return exec(self.get_scr)

a = MyClass('return self.data[index]')

```
The idea is that the actual function body is stored in a string which can be changed at runtime.  However, the syntax I've used doesn't work - I can't use 'return' within the exec.  I'd thought of using eval, but sometimes I want more than one line of code in the function.

Any ideas of a better way of doing this, or something that will work?

---

### Post by pmasiar on 2007-11-19
There is many ways to do it, depending what ecaxtly you want. One way is closures and/or lambda. Simple way is just assign it. Function name is name exacly like any other variable. You can define many functions "constant bodies" (f1..f99), and then assign appropriate one to your "variable" at runtime.

```

def f1(x, y):
    return x + y

def f2(x, y):
    return x - y

if condition == 1:
    dynamic = f1 
else
    dynamic = f2

print dynamic(1,2)

```

Warning: just typed out out of top of my head, not even tried in shell. Should work tho, this is why I like Python: it fits my brains :-)

---

### Post by smartbei on 2007-11-19
You were close pmasiar, missing a colon after the else (I am always making mistakes like that on the forums too when I want to reply but don't have time to check the code).

About the original question though - to me this sounds like a case where you need to rethink your programs architecture. Perhaps you could give a bit more information so we could recommend a better way to solve the problem. re-writing a function at runtime does not seem like the best structure for a program.

---

### Post by aquavitae on 2007-11-20
Thanks pmasiar, the point is though, that I want the function to be customizable by the user so I'm not sure if assigning a function definition like that would work... but maybe I can still do something with it.

> **smartbei said:**
> You were close pmasiar, missing a colon after the else (I am always making mistakes like that on the forums too when I want to reply but don't have time to check the code).

About the original question though - to me this sounds like a case where you need to rethink your programs architecture. Perhaps you could give a bit more information so we could recommend a better way to solve the problem. re-writing a function at runtime does not seem like the best structure for a program.
You're probably right.  What I basically want it a list type class who's __getitem__ function returns a tuple *(value, value_as_a_string)*, where *value_as_a_string* is the value as it should be displayed on screen, and *value* is the actual value in the list. The __setitem__ function has a validation procedure in which the value passed to it may be changed or rejected depending on some criteria.  The program itself it basically a specialised spreadsheet - each of these lists represents a column.  The idea is that the way in which the column handles data can be changed through scripting by the used, i.e. the __setitem__ and __getitem__ functions can be changed at runtime.

In case anyone is interested the program is actually intended to set up bills of quantities (used by quantity surveyors and engineers) which is something like a very large account.  I've got it hosted at [http://code.google.com/p/boq/]("http://code.google.com/p/boq/").

---

### Post by smartbei on 2007-11-20
Here is how I think I would do this:
Apprantely, your program stores information as columns (each column is a list (class)) and you want __getitem__(i) to return a tuple of the actual value at i and a representation of that in string form. I suggest that the class would look like this:
```

class Column:
	def __init__(self):
		pass
		#initcode
	
	def __getitem__(self, i):
		return self.data[i].get()

	def __setitem__(self, new):
		return self.data[i].set(new)

```

self.data should be an internal list that holds instances of classes. For example, there would be a class named "number" that has its own get and set methods defined, and a class named "string", and a class named "date", "time", "currency", etc.

For example, the class number might be:
```

class Number:
	def __init__(self, init_num=0):
		self.num = init_num
		if init_num == 0:
			self.str_num = ""
		else:
			self.str_num = str(init_num)
	def set(self, a):
		if 'int' in str(type(a)):
			self.num = a
			self.str_num = str(a)
			return True
		elif 'str' in str(type(a)):
			try:
				self.num = int(a)
				self.str_num = str(self.num)
				return True
			except:
				return False
		return False
	def get(self):
		return (self.num, self.str_num)

```
And so on for date, time, etc. 

Well, I hope that was clear. Note that none of this was checked for syntax or run. It should be correct but a couple errors may well be present.

---

### Post by aquavitae on 2007-11-20
Hmmm, not a bad idea as another level of abstraction, but I still want to be able to change the behaviour of the functions at runtime.  The column types you mentioned (i.e. string, number, etc) are some common ones I've included as built in, but its quite probably that a user would want to add a coumn to control, for example, the number of decimals of an adjacent number column. In this case the get function of the number column should be something like (pseudocode-ish):
```

def get(self, item):
   return self.data[item], str(round(self.data, adjacent_data))

```
The idea is to provide a selection of commonly used column types, but still to allow for more complex, customised ones through scripting.

Perhaps, as you suggested, my design isn't good...

After a bit of experimentation I'v come up with this:
```

class FuncScript:

   __attrs = ['args', 'script']

   def __init__(self, script, local_names):
      self.__func = None
      self.args = local_names.keys()
      # Add a def statement including arguments, change tabs to spaces and indent the funciton body.
      self.script = 'def _func(' + ', '.join(args) + '):\n' + re.sub('\t', '  ', re.sub('^', '  ', script))
      exec(self.script, globals, locals + {'_func' : self.__func})
      
   def __call__(self, locals):
      ''' Call the function with arguments specified in locals'''
      passed_args = [(locals[arg] if arg in locals.keys() else None) for arg in self.args ]
      return self.__func(*tuple(passed_args))
      
   def __getattr__(self, attr):
      ''' Get self.args or self.script'''
      if attr in __attrs:
         return self._attr[attr]
      else:
         raise AttributeError, 'No attribute named ' + attr
         
   def __setattr__(self, attr, value):
      ''' Set an attribute and recreate the function. '''
      if attr in __attrs:
         self._attr[attr] = value
         exec(self.script, globals, locals + {'_func' : self.__func})
      else:
         raise AttributeError, 'No attribute named ' + attr

```
I haven't tested it or even really read through it so its probably full of errors.  The class is supposed to take a string argument which contains the function body, and a list of possible arguments to the function.  A 'def' statement is prepended to the function body to make it syntactically correct, and this is then assigned to a local variable which can be called as a normal function. (Thanks pmasiar for the idea of assigning it to a variable:)) This serves the purpose I want, but it still seems a bit clumsy.

---

### Post by pmasiar on 2007-11-20
> **aquavitae said:**
>  I want the function to be customizable by the user 

look at built-in functions, eval. You can pass it a string, it gets compiled to code. I bet you can define functions there, at least lambdas, and possibly plain functions. Try it and let us know.

---

### Post by aquavitae on 2007-11-20
> **pmasiar said:**
> look at built-in functions, eval. You can pass it a string, it gets compiled to code. I bet you can define functions there, at least lambdas, and possibly plain functions. Try it and let us know.
eval can only compile an expression.  You can define a lambda (because python sees it as an expression), but not an actual function. I tried a few variations on it to see if it would work, but I get syntax errors.  I could use it if I could guarentee that the function body could always be writted as an expression, but that means I wouldn't be able to use any loops or conditionals.

---

### Post by pmasiar on 2007-11-20
OK, next one down in built-ins is execfile(). It allows you to compile a module. You can reload module dynamically and rebind names.

---

### Post by aquavitae on 2007-11-20
I think execfile works basically the same as exec, just takes a file argument instead of a string. Since the function definition I want will be stored in a string it makes more sense to stick with exec.  Assuming, that is, that I understand the working of execfile properly...

---

### Post by smartbei on 2007-11-20
No, aquavitae, with the program structure I proposed there would be a class FPNumber (floating point number) that would have as one of the attributes the rounding place, and that would be used in the get method. That way, there would be no need to change the actual code.

The only case in which there would be a need for a change in the get function would be a case where the type is not related to the class type - trying to represent a float with an integer class, etc. The idea is that each class is  a certain type and can represent all the different options a user would want. If they want to add a new user-defined type there are two options:

[LIST=1]
[*]Use a general type class that would use something like a regex like is possible in Excel: ($###.##) would be parsed to print floating point numbers with resolution to two decimals and a dollar sign in front.
[*]Have users define a whole new class.
[/LIST]

What I would do is make it very simple for the user to add classes - For example, try to abstract away everything but what the user needs. You could have a class Basic that has the basic attributes all classes need and over-rideable get ansd set methods. Then, users could just have:

```

class MyPersonalFPNumber (Basic):
	def set(self, val):
		#user validation code
		self.val = val #self.val is inherited from Basic
	def get(self):
		return (self.val, "123" + str(self.val) + "$_") #just an example obviously.

```

The basic class is a good idea anyway since that would make it very simple to switch a cell in the column's value.

I don't see any way to make it similar than that, either for the user or for you, without sacrificing maintainability and ease-of-use.

EDIT: Fixed a bit of code. Again, not syntax checked so usual dislaimers apply.

---

### Post by aquavitae on 2007-11-21
I see what you mean... it would certainly be neater for columns that just need some text formatting, and using regular expressions would make it really powerful too.  But how about a linked column?  Don't know how much of the code you looked at - a linked column is one whose value depends on data in another column.  E.g. the get function from an amount column would return rate_column * quantity_column, format_as_currency(rate_column * quantity_column).  Or, an even more complicated situation is that of the units column.  The way it sould behave is that if the units column is empty, most of the other columns should not display anything (i.e. return value, str(value) if units != '' else '').  Now that I think about it though, my method would be even worse in this situation (really messy!).  What would you suggest in this case?  

Btw, the reason I'm so keen on being able to easily rewrite the functions is that a while ago I wrote a similar program in c++ which we are using at work.  I found really quickly that a column layout that made sense to some of us didn't make sense to others, and they suddenly wanted the column actions changed.  So now I'm rewriting it in python (because its faster and easier to write) and I'm trying the get the design as versitile as possible.

Thanks for all the help so far!

---

### Post by smartbei on 2007-11-21
Well, have you thought about using Excel or Calc? :D

From what I understand from your latest post, you don't need intracolumn granularity - the whole column is the same type. Meaning you would have a UnitsColumn, an AmountColumn, etc.

One way to do it (assuming that the layout of the columns in the application might change but the actions of the columns themselves stay mostly the same) would be to have a AddTwoColumn which would add the appropriate cells in two other user-specified columns, etc. This could work if you have it very easy to define new columns - perhaps as a runtime imported module holding the base classes and extra user-written extension classes.

Lastly, you could take a leaf from Excel's book and define a simple language that would parse the value of the columns. This is a different way I guess of doing what you are trying to do (redefining the function). For example: Col1 = $SUM($C2, $C3)*4. The $ sign could be used to symbolize an entity to simplify parsing. Then, you would define the function sum as:
```

class ComplexColumn:
	def __init__(self):
		self.func=None
	def set(self,s):
		s=str(s)
		self.parse(s)
	def get(self,i):
		if self.func != None:
			return self.func(i)
		else:
			return None
	def parse(self,s):
		pass
		#parsing code

```
The idea being that self.parse will set self.func to a lambda (not sure if that would work in this situation but something of the sort). You would have to write a string parser for this, but that shouldn't be too difficult. I guess this looks to me like the best idea.

---

### Post by aquavitae on 2007-11-21
> **smartbei said:**
> Well, have you thought about using Excel or Calc? :DThat's what's generally used at the moment, but there are huge problems with it - mainly, its difficult getting consitent formatting, adding a row means manually changing every page break, and its too easy to make a mistake in a formula in one cell.

> 
From what I understand from your latest post, you don't need intracolumn granularity - the whole column is the same type. Meaning you would have a UnitsColumn, an AmountColumn, etc. Actually, don't want!  I want to restrict it so that the column cannot change formula halfway down.

> 
One way to do it (assuming that the layout of the columns in the application might change but the actions of the columns themselves stay mostly the same) would be to have a AddTwoColumn which would add the appropriate cells in two other user-specified columns, etc. This could work if you have it very easy to define new columns - perhaps as a runtime imported module holding the base classes and extra user-written extension classes.
 Assumption correct, but I don't quite get it - could you explain more?
Lastly, you could take a leaf from Excel's book and define a simple language that would parse the value of the columns.[/QUOTE]Like I said, I really don't want the formula to change within a column.But for a column only method (e.g. col1 = col2 * col3) that's basically what I was going for in the first place, using python as the language.

The more I think about it though, the more I think that exec(script) is really not the right way to do it - its fine now, but will get really messy and complicated later when I'm trying to do something like I mentioned before with UnitsColumn.

---

### Post by smartbei on 2007-11-21
About what you wanted more explanations about:
The idea was to create several columns that have all the functionality you need - An AmountColumn for example. It would have the user able to choose which columns it links to, and then it would do just that. You wouldn't be able to customize it. You could have it change place in the window, the user would just need to choose what columns for it to use in its calculations.

The other idea (with specifying a parseable script for each column) is a lot more extensible. With this idea it would be trivial to add both new functions and different kinds of columns. I personally think this is the way to go - since in the future it should be easy to add features to. BTW - there are libraries that simplify the parsing of strings and mini programming languages - though I can't seem to find one ATM.

The parse function would cunstruct a lambda that would calculate the formula. For example:
```

s = "$C1 + $C2*$C3" #column parseable string
#bunch of string parsing and error checking...
return lambda i: self.document.column1.get(i)+self.document.column2.get(i)*self.document.column3.get(i)

```
The self.document.column business probably doesn't fit with your application architecture but you get the idea.

The parseable script would control the internal value of the column, NOT it's display. It's display would need to be specified either by using some sort of regular expression syntax, or by having a couple built-in display formats (Shouldn't be a problem - you only have like 5 display formats probably - integer, floating point, currency, string...).

So you would have a ComplexColumn class that would have the methods as I described above (in the previous post) and also an attribute specifying how it should be displayed. It's get method would use that attribute to display it correctly.

How does that sound?

---

### Post by aquavitae on 2007-11-21
But how is ```
parse("$C1 + $C2*$C3")
``` different from
```
eval("C1 + C2*C3", {"C1": self.column[1], "C2": self.column[2], "C3": self.column[3]})
```
The second is more simple as it doesn't require any extra parsing.  Either way, I'm limited to fairly simple code... but I suppose that's not too bad.

That's a good point about returning strings - I obviously hadn't thought it out properly! But apart from that, I seem to be back where I started :).

---

### Post by smartbei on 2007-11-21
Well, in the beginning you wanted to change the actual code of your program. This way, that code is not changed and you are parsing a string the user can enter in the gui of your program, at runtime. In addition, this makes it very easy to save a document - for each column just save it's parseable string, its data type and the values of its cells (if the column is not linked). 

Thus you have a simple, very extensible program. The one thing I would be worried about is protecting member variables that you don't want users to access. Otherwise, they might accidentally overwrite something important and cause your whole application to crash.

I actually didn't know about the extra options available to eval, so that makes it even easier.

---

### Post by aquavitae on 2007-11-21
Yes, the extra arguments to eval will protect hidden variables.  But I think I might use the class I wrote above with exec instead of eval.  I'd like to keep the option open for control structures, and the only difference is I need a return statement.  I think this is what I wanted to do in the beginning, I just didn't explain too well, but its helped clear it up so I can see what to do now.  Thanks for the help!

---

### Post by sridev on 2009-12-23
Hi anyone pls let me know how to fetch the HTML code of a webpage and identify an element in the webpage using Python

---

### Post by CptPicard on 2009-12-23
The urllib2, BeautifulSoup libraries.

What made you post this in a random, unrelated thread that is over two years old? :(

---

