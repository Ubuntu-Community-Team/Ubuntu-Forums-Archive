---
title: "User input in GUIs versus the command-line"
date: 2009-08-28
forum: Programming Talk
---

### Post by kumoshk on 2009-08-28
Here's something like what I want to do (in a GUI, such as one made with WxPython):

Using only one text control for input and only one for output, I would like to ask the user about twenty unique questions (one at a time), and store the answers in a list of strings. (This is just an example of the sort of thing I need. I need a dynamic answer&#8212;so something that will only work for a certain number of questions won't help.)

Now, this would be extremely easy on the command-line, but I need a way of doing this, just as flexibly, in a GUI.

Any ideas?

If you instantly think the solution looks simple, you probably haven't actually tried this. The problem with user input in GUIs is that the event loop is always running, and there's only one function to respond to it. On the command-line, however, it only runs (in your program) when you call the raw_input function, and you can easily give a different response every time.

Now, I've already done tons and tons *with* designing around this lack of functionality, but I've come to the point where I actually need this.

I'm trying to make it so I can program as if it were from the command-line, only have the result happen in a GUI, instead.

---

### Post by wmcbrine on 2009-08-28
I'm sorry, but I do think it's simple. The event loop is not an obstacle.

You make an Entry() widget (that's what it would be in Tkinter or PyGTK, anyway), and you bind an event handler to the return key (and maybe to a button). Throw up your first question, and then start the event loop.

In the event handler, you do this:

1. Read the result from the widget.
2. If it's the last question, exit, or whatever.
3. Clear the widget.
4. Set new question (possibly depending on the result of step 1).
5. Return.

Oh, and you need a flag to keep track of where you are between calls to the event handler. That's about it.

---

### Post by kumoshk on 2009-08-28
> **wmcbrine said:**
> &#8230;2. If it's the last question, exit, or whatever.

&#8230;

Oh, and you need a flag to keep track of where you are between calls to the event handler. That's about it.

Step 2 and the part about flags don't seem entirely clear&#8212;so I'm not sure if you understood my need or not, yet.

Creating the wx.TextCtrl (entry widgets) isn't the problem. Reading from and writing to them isn't the problem. The problem is changing the event handler to a different one (without disrupting it, such that when you exit the inner one then the outer one continues in its progress where it left off), and I need to be able to have any number of 'different ones' on top of each other (in a recursive fashion).

The problem is also syntax. I'm making a single program that is meant to use multiple GUIs, as well as the command-line. Therefore, I need to make input functions compatible with my program, which input functions are called (not coded) exactly the same way so that people who extend the program don't have to change anything special about the code when switching between GUIS (and the command-line). Therefore, the input function needs to appear to function exactly the same way to the end user no matter the interface.

One easy solution I see would be to embed a command-line prompt into the GUI, somehow. Is there a way to do that in WxPython?

Feeding user input to the command-line (behind the scenes) could also be a solution, but I'm not sure how to do that, either.

Also, it's good to know that this program is enormous&#8212;that's why I need a dynamic solution. If I have to add a new flag manually every time I add another input, this isn't going to work.

---

### Post by kumoshk on 2009-08-28
I found something that works for what I was looking for, although it changes the experience a little:

```
mystring=wx.GetTextFromUser(message, caption, etc)
```

It works fine for the special occasions when I need to ask a bunch of questions (without me having to iterate through a bunch of options, while still allowing me to use my TextCtrl normally).

I can make an input method with that compatible with the command-line's raw_input.

---

### Post by smartbei on 2009-08-29
You can also have the event handler be a simple function that takes a function from a list of functions, calls it, and removes it from the list. In this way you get a different method in the order you want.
```

real_event_handlers = [real_handler1, real_handler2, real_handler_3, ...]
def handler(*args):
    try:
        real_event_handlers.pop()(*args)
    except IndexError, e: ## The list is out of functions:
        # Do Something!

```

---

### Post by kumoshk on 2009-08-29
> **smartbei said:**
> You can also have the event handler be a simple function that takes a function from a list of functions, calls it, and removes it from the list. In this way you get a different method in the order you want.

That would be cool; however then my syntax would have to be different. I mean, my code would have to be in functions, instead of just directly following the statement. Admittedly, I could set the command-line way to be function-oriented, too, though.

---

