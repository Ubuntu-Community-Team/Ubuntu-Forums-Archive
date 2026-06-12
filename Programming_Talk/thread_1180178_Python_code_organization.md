---
title: "Python code organization"
date: 2009-06-06
forum: Programming Talk
---

### Post by Volt9000 on 2009-06-06
I'm in the process of converting a project I wrote in C# to Python.

I noticed when I wrote the C# program, I didn't do a very good job of separating the GUI code from the rest of the code. In the code of my main form/window/frame, I've written code to do data processing stuff.

I'd like to correct this in my Python program. Currently my Python program is structured as follows:

Main module
- just calls the GUI module, which displays the interface

GUI module
- sets up the GUI elements and event handlers

Data module
- contains class definitions for data structures

In the GUI module I have event handlers set up to take care of menu selections and whatnot. My question is, should I implement the data processing in the GUI module, implement it in the main module, or implement it in a completely separate module?

---

### Post by simeon87 on 2009-06-06
> **Volt9000 said:**
> In the GUI module I have event handlers set up to take care of menu selections and whatnot. My question is, should I implement the data processing in the GUI module, implement it in the main module, or implement it in a completely separate module?

Not in the GUI module I'd say. Is the main module used for anything other than setting things up and launching the application? If so, I wouldn't put it there either. It would make sense to have a separate module that performs operations on the data. On the other hand, you could also place them in the data module; not everything is a class in Python so you could have some functions in the data module that perform common operations. If it's a large program, you could distribute the functions that are somehow related over several modules. In the GUI module, you can then call the right function to perform some operation on the data.

---

### Post by Volt9000 on 2009-06-06
Alright, thanks for your input.

I think I'm going to go with the third option: implementing the code in a separate module altogether, just to further separate the data definitions and processing.

---

### Post by Tony Flury on 2009-06-09
What I have done is encapsulated the Gui in a well defined Class, with its own defined interface; and the class interface is in terms of high level construct.

That way my application logic (data processing) does not know anything about the GUI, and the GUI knows nothing about the data processing.

In theory (i have a design and not the code), I could completely redesign my GUI - do away with a lot of buttons, use menus instead of toolbars etc and not have to change my application logic - in fact I could (and probably will) develop a CLI version of the application, using exactly the same application code - and just a different version of the GUI code.

---

### Post by blackxored on 2009-06-09
Short answer: MVC

put a package under ui: that's your gui (View)
put a package under core: that's your data processing (Controller)
put a package under model: that's your plain data

That's how I'm used to. It's personal, but you asked for advice.

---

