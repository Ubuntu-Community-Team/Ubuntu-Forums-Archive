---
title: "Python + GTK (&amp;/-) Console"
date: 2006-12-08
forum: Programming Talk
---

### Post by gummibaerchen on 2006-12-08
Hello,

in several Threads here, people wanted GUIs for console programs, or created already GUIs for these.

Now, I thought it would be good to create a Starterkit in Python.

I thought of 3 Tabs:
- Command
- Output
- Input Action

So in the first Tab user can insert shell commands. Whatever they like, later the program will do this automatically of course.

In the second Tab you see the output of that commands / all the last commands.
For example if someone give 'echo "asdf"' in the first tab, here you see then 'asdf'.

The third Tab contains some actions. For example some 3 commands.
If output is
adsf -> Dialog Box pops up
123 -> Window resizes
quit -> Program closes

I think that would be a good start, and the GUI-Creators would have a good start for interacting with Console Programs.

Anyone knows something like this? Anyone who could help creating a program like this?

---

### Post by Tomosaur on 2006-12-08
I don't really understand this. What'd be the point? Isn't it just easier for the user to type into the actual console?

---

### Post by gummibaerchen on 2006-12-08
> **Tomosaur said:**
> I don't really understand this. What'd be the point? Isn't it just easier for the user to type into the actual console?

It's just to have the basic functions for executing shell commands and work with the output.

In the end, it's a Starterkit for _GUI_ Programmers.

---

### Post by Tomosaur on 2006-12-08
I mean, how does this help with creating GUIs? All it's doing is redirecting stdout to a window.

---

### Post by gummibaerchen on 2006-12-08
> **Tomosaur said:**
> I mean, how does this help with creating GUIs? All it's doing is redirecting stdout to a window.

Because the people who would use this, don't know how to work with stdout, and so they would have a basis to work with.

They program is not the big thing, it's the code inside they would need.

Any better ideas?

---

### Post by Tomosaur on 2006-12-08
I think we're misunderstanding each other here lol. Here's how I'm imagining this:

EDIT: Actually scrap that, it looked horrible. Basically it was a 'diagram' of how I'm seeing it, which in essence is nothing more than the terminal is currently doing.

Now, when I think of this, I see it as doing no more than the terminal currently does, in which case, what's the point? There's nothing here which helps anyone, it just makes getting the output of a command more complicated. My question is 'what is the application actually supposed to do?'. I'm not trying to sound critical, I just really don't understand what the purpose of the program is.

---

### Post by gummibaerchen on 2006-12-08
Because it's **works** with the in and output.

Yes, at this stage the program has no real sense, buts it should be only a basis.

For example the guy around here who is actually creating a gnome-vpnc interface, would need this for python.

And I think other would you it as well.

---

### Post by gummibaerchen on 2006-12-23
Is there any GTK Interface for the "interactive python console" around?

Rhythmbox and Epiphany have this as plug-ins, but stand-alone would be nice.

Thanks

EDIT:
[http://www.loria.fr/~rougier/pub/Software/pycons.py](http://www.loria.fr/~rougier/pub/Software/pycons.py)

Looks nice, thought only there would be something smaller than 600 Lines of Codes

---

