---
title: "Python doubt"
date: 2008-12-28
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-12-28
I wanted to know the difference between a class and a function.

I mean both of them return something, and take in arguments. Then what is the difference.

---

### Post by 7raTEYdCql on 2008-12-28
I had to ask one more thing as far as designing a program is concerned.

When i design the program i will fit it in one script1.py. But suppose i want to design the GUI for the script(using pyGTk) then the two will be mixed together. Just asking.

---

### Post by Greyed on 2008-12-28
A function cannot hold data which is callable outside itself.

[php]
>>> class spam():
...     def __init__(self):
...         self.ham = 9
...
>>> a = spam()
>>> a.ham
9
[/php]By the same token functions cannot have other functions defined in them be accessible to the outside.  Nor can you inherit a function from another function.

[php]
>>> class ham(spam):
...     def spam(self):
...         print self.ham
...
>>> b = ham()
>>> b.spam()
9
[/php]There's more but that should suffice.

---

### Post by catchmeifyoutry on 2008-12-29
A function is a body of instructions to the computer; given some input a result is calculated, and that's it. A function is free to return anything.
A class, on the other hand, is a structured collection of data with associated methods (functions defined in the class self) to manipulate the data in a useful way. When you create a class it doesn't "return" just anything, you only obtain an object of the particular class: an instance of the structured data.

Classic example would be a contact database in which there is a class Person representing contact information. The data fields in the class are name, phone_number, email (for example). In the DB are multiple instances of this class, one for every known contact.
There could also be function to manipulate the DB such as to remove a contact, edit a contact, export the data to a file. These actions themselves are not data structures like the Person class.

---

### Post by 7raTEYdCql on 2008-12-29
Then can i say that "class" of python correponds to "structures & unions" of C.

---

### Post by Greyed on 2008-12-29
No.  A class is in a class of its own.

---

### Post by slavik on 2008-12-29
> **i.mehrzad said:**
> Then can i say that "class" of python correponds to "structures & unions" of C.
exactly.

in C++, the struct is the same as in C, except you can put functions inside. class simply changes the default scope (from public to private).

---

### Post by catchmeifyoutry on 2008-12-29
Yes, very good, except that it is a more powerful concept because of class inheritance and the use of methods.
I'm sure you can google many tutorials of classes and their usage in python.

I would encourage you to read up on the use of classes and object oriented programming (OOP) at a certain point, especially if you have experience in C and are also interested in learning C++ or Java which make extensive use of OOP (as does python).

---

### Post by kostkon on 2008-12-29
> **catchmeifyoutry said:**
> I would encourage you to read up on the use of classes and object oriented programming (OOP) at a certain point, especially if you have experience in C and are also interested in learning C++ or Java which make extensive use of OOP (as does python).
+1
it will be very useful to you to understand the concepts of OOP, it will make to produce better software. And since you are using Python, a language that indeed supports OOP, it makes it even more necessary.

---

### Post by nvteighen on 2008-12-29
> **catchmeifyoutry said:**
> Yes, very good, except that it is a more powerful concept because of class inheritance and the use of methods.
I'm sure you can google many tutorials of classes and their usage in python.

Ehmm? C struct's can also be inherited. Ever did GTK+ programming in C? Of course, it's not an automatic inheritance and you have to use (spell) casts, but it's perfectly feasable.

---

### Post by catchmeifyoutry on 2008-12-29
> **nvteighen said:**
> Ehmm? C struct's can also be inherited. Ever did GTK+ programming in C? Of course, it's not an automatic inheritance and you have to use (spell) casts, but it's perfectly feasable.

But that then isn't class inheritance, is it?

---

### Post by nvteighen on 2008-12-29
> **catchmeifyoutry said:**
> But that then isn't class inheritance, is it?
It is. In GTK+, you have a class GtkWidget and GtkWindow is a child class of it. So, any GtkWindow is a GtkWidget... But GtkWidgets are GObjects, etc. You usually declare stuff as GtkWidget and cast up or down depending on what you need. Those casts are actually C preprocessor macros.

Of course, this inheritance is limited, as it is always public and because it is actually implemented on top of a a low-level trick (how structures are allocated in memory). The "methods" are just functions with a naming convention.

That's why PyGtk and even gtkmm are much nicer to work with. "Real" GTK+ in C is a pain and is a great example of a library that overgrows the language it is implemented in. I mean, yes, GTK+ had to be implemented either in C or C++ as it is a system library, but for normal use, I'd rather use its bindings unless there's a really good reason not to.

---

### Post by catchmeifyoutry on 2008-12-29
> **nvteighen said:**
> It is. In GTK+, you have a class GtkWidget and GtkWindow is a child class of it. So, any GtkWindow is a GtkWidget... But GtkWidgets are GObjects, etc. You usually declare stuff as GtkWidget and cast up or down depending on what you need. Those casts are actually C preprocessor macros.

Of course, this inheritance is limited, as it is always public and because it is actually implemented on top of a a low-level trick (how structures are allocated in memory). The "methods" are just functions with a naming convention.

That's why PyGtk and even gtkmm are much nicer to work with. "Real" GTK+ in C is a pain and is a great example of a library that overgrows the language it is implemented in. I mean, yes, GTK+ had to be implemented either in C or C++ as it is a system library, but for normal use, I'd rather use its bindings unless there's a really good reason not to.

Hmm, interesting, I indeed never went that far with C structs (or GTK programming in C).
Still, I think this discussion is a bit out of scope of the explanation I was trying to give to the original post (concerning python). I will look up C struct usage again, maybe it will come in handy some other time.

---

### Post by pmasiar on 2008-12-29
> **catchmeifyoutry said:**
> Hmm, interesting, I indeed never went that far with C structs (or GTK programming in C).

Before OOP was syntax feature, it was just a "design pattern" in C. It's common that some language need to implement something in code (as design pattern) while other do it directly. OOP is just little bigger "pattern" than others.

---

### Post by Greyed on 2008-12-30
> **pmasiar said:**
> Before OOP was syntax feature, it was just a "design pattern" in C. It's common that some language need to implement something in code (as design pattern) while other do it directly. OOP is just little bigger "pattern" than others.

What a wonderful way to explain higher level languages vs. lower level languages.  :D

---

