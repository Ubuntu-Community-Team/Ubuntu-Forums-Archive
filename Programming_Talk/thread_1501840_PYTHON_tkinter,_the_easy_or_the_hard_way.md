---
title: "PYTHON: tkinter, the easy or the hard way?"
date: 2010-06-04
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-06-04
Hello Forum,

I have learnt recently to use Tkinter on Python especially thanks to [this tutorial]("http://www.builderau.com.au/program/soa/A-Quickstart-to-building-GUI-based-applications-in-Python/0,339024614,339272995,00.htm").
Now i am looking at improving my skills and i came across other tutorials, [like this one]("http://sebsauvage.net/python/gui/").

Now i am curious because the second tutorial tells me how to create a main window, namely like that:
[PHP]#!/usr/bin/python
# -*- coding: iso-8859-1 -*-

import Tkinter

class simpleapp_tk(Tkinter.Tk):
    def __init__(self,parent):
        Tkinter.Tk.__init__(self,parent)
        self.parent = parent
        self.initialize()

    def initialize(self):
        pass 

if __name__ == "__main__":
    app = simpleapp_tk(None)
    app.title('my application')
    app.mainloop()[/PHP]

While i can do the same (thanks to the former tutorial) like this:
[PHP]#!/usr/bin/python

from Tkinter import *

root = Tk()

root.mainloop()
[/PHP]

So obviously this is confusing. Am i missing something by using the first tutorial or is it rather that the person who did the second can't really program and keep it simple?

You've guessed i prefer the former. I'm curious of your opinion.

Thanks

---

### Post by wmcbrine on 2010-06-04
Well, they aren't *quite* equivalent, and there are a few things I prefer in the second tutorial's version. But, yeah, I'd call it "overengineered". I'm sure its author would say that, while it doesn't really add anything at this "hello world" level, it teaches better habits for use with larger programs, to keep them more maintainable. I'm not sure I agree.

Probably someone from a Java background. I think some people just get nervous if they don't have "enough" code, even if it's just boilerplate. :)

But make sure you understand the purpose of each and every line in both versions before you reject the second tutorial's version. There *is* a logic behind it, even if I don't necessarily agree with it.

---

### Post by Can+~ on 2010-06-04
Even though I'm not a java purist, and I usually prefer the quick and easy method, I'm in favor of the first one, simply because it doesn't clutter the namespace with junk.

The first one uses inheritance, then calls it's superclass constructor, and runs itself (I would've put the title as a parameter, though). But I don't get that "Parent" variable thing, probably because I don't know about TK. Also, the [FONT="Courier New"]__name__ == "__main__"[/FONT] is a simple python test to check if you're running the application directly (True), or being imported (False).

The second one, treats all the current namespace as it was the whole TK application, messy, but really straightforward.

You won't understand the first one, if you don't know the ABC's of how Object Orientation works in python, specifically, inheritance and operator overloading (assuming by the empty "initialize" method). If you have any questions about this two, just ask here.

---

### Post by juancarlospaco on 2010-06-04
TKinter is very nice.

This is not a TK problem, but a Python problem.

The first code is prepared for Windows, for the Encoding.

Maybe the first was assisted by an coding application IDE.

This is my underconstruction Python-TKinter App (on Spanish, yes the Analog clock works):

[IMG]http://img189.imageshack.us/img189/4093/pantallazou.jpg[/IMG]

:)

---

### Post by jesuisbenjamin on 2010-06-05
Hi there,

Thanks for your responses. To be honest i am not very familiar with object oriented programming, so i cannot really see the benefit of creating a class and an instance of that class in this context. It seems the code is simply duplicating what Tk by itself is already able to do. But as i said, i am not familiar with this, it might be so that i may need this kind of programming skill as i improve.

---

### Post by wmcbrine on 2010-06-05
Yeah, exactly, you need to understand object-oriented programming before you can reject it. :D

---

