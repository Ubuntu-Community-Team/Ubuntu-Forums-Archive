---
title: "[Python]Local Code inside Functions"
date: 2008-04-16
forum: Programming Talk
---

### Post by swatto on 2008-04-16
Hi all,

If a piece of code calls a function can the function that is called access parts of the code outside the function so that an event can happen.  Like if the user clicks a button it calls the function and then uses the variable inside the function to store data that is then passed to a widget (the widget is already created outside of the function)

I don't really know if im making myself clear. :confused:

Thanks to anybody who can understand what im on about and provide an answer.

I realise that variables created inside a function are local to that function only unless they are global.

---

### Post by Can+~ on 2008-04-16
> **swatto said:**
> Hi all,

If a piece of code calls a function can the function that is called access parts of the code outside the function so that an event can happen.  Like if the user clicks a button it calls the function and then uses the variable inside the function to store data that is then passed to a widget (the widget is already created outside of the function)

I don't really know if im making myself clear. :confused:

Thanks to anybody who can understand what im on about and provide an answer.

I realise that variables created inside a function are local to that function only unless they are global.

I didn't get the question. So I'll shoot what I think is the answer

If you're building the whole widget inside a class, you can hand the self to access the content inside the instance of the class.

[PHP]class scopeTest:
	foo = 120
	
	def __init__(self):
		print self.foo	#Prints 120
		
	def anotherFunc(self):
		foo = 5
		print self.foo	#Also prints 120, since self is passed to it.
		print foo		#Prints 5, the one in the local scope
	
	def talkToOutside(self):
		functionOutside(self) #Handing self explicit

#Function outside the class
def functionOutside(reference):
	print reference.foo
	
		
a = scopeTest()
a.anotherFunc()
a.talkToOutside()	#Works[/PHP]

Functions inside the class always receive self. When calling outside, you need to handle self explicitly if you want to interact with the current instance of the class.

If you're working without classes, then you'll need to handle values by reference, putting them inside, like singletons ({ }, [ ]). When working with things like widgets or GL, it's safer and easier to store things inside of a class.

---

### Post by swatto on 2008-04-16
Thanks for your reply - Maybe I will look at building the GUI on a class - but I really don't understand how to use classes - I only know what they are.  The tutorials I have read don't explain how or where to use them :(

---

### Post by Can+~ on 2008-04-16
> **swatto said:**
> Thanks for your reply - Maybe I will look at building the GUI on a class - but I really don't understand how to use classes - I only know what they are.  The tutorials I have read don't explain how or where to use them :(

Object Oriented programming is what you should look for.

[http://www.freenetpages.co.uk/hp/alan.gauld/tutclass.htm](http://www.freenetpages.co.uk/hp/alan.gauld/tutclass.htm)

OOP is used mostly.. everywhere. Segregate all the code in functional sections, working each individually as cells. This way, you can just call your own function library (or classes for that matter) and don't care what happens inside them (when working properly). Using classes with graphic libraries is always a good idea, since it isolates the graphical stuff from the actual code.

---

### Post by themusicwave on 2008-04-16
Swatto,

To simply answer your question yes a function can access things outside of it self.  What you are dealing with here is called Scope.  In programming the Scope of a variable or function is the area of the program in which it is defined.  In C style languages scopes are denoted with {} in python they are denoted by tabs.

As long as the function you are calling is within the same scope(tab depth in python) this will work.

For example this is totally valid:

[PHP]
def someFunction():
    print "Function was called"

def buttonCmd():
   someFunc()

[/PHP]

If this is in relation to our previous thread about TKinter and your text editor please feel free to ask me detailed questions there.

[http://ubuntuforums.org/showthread.php?t=749279]("http://ubuntuforums.org/showthread.php?t=749279")

Also if you provide the code that has the error I can help you out.

---

### Post by pmasiar on 2008-04-16
> **swatto said:**
> I realise that variables created inside a function are local to that function only unless they are global.

Not always. You can have: 
- local variables, allocated at the stack, destroyed when function exits
- global, accessible to all (and dangerous for side effects by some obscure function - you cannot protect them)
- static (accessible only inside function, but remaining to be "alive" between calls.
- objects, like singleton object which will keep single copy of itself and share it with all functions who need access.
- generator function, which will 'yield' new value every time it is called
- closures, when function 'remembers' values from the environment and maintain a copy of them (very iffy explanation I know :oops: )

So I am not sure which one you want.

Static variable or yield might the simplest solution (without any OO magic).

---

### Post by stevescripts on 2008-04-16
Maybe a simple(minded) classless example might help

Note here, tinkering around with Python is new to me...

```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("PlusOne")

root.resizable(0, 0)

def mycommand():
	temp = w.cget("text")
	temp = temp + 1
	w.configure(text=temp)

w = Label(root, text=0, fg="red", width=16)

w.grid(row=0, column=0)

b = Button(root, text="Add 1", command=mycommand )

b.grid(row=0, column=1)

root.mainloop()

```

Save the code, as say plus1.py, and chmod +x

Hope this is helpful to someone.

Steve

---

### Post by themusicwave on 2008-04-16
Just so you all know this was in reference to a previous thread swatto had opened.

[http://ubuntuforums.org/showthread.php?t=749279]("http://ubuntuforums.org/showthread.php?t=749279")

I was helping him learn how to make a text editor in TKinter and python.

Perhaps  a merge is in order?

---

