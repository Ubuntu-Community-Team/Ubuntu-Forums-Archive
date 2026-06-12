---
title: "Does anyone do their GUIs like this?"
date: 2010-01-11
forum: Programming Talk
---

### Post by SunSpyda on 2010-01-11
When I do GUIs, I have a way of doing them, but people keep telling me it's cryptic. Yet I think it's easier, since it makes the left-hand side of the code look like a 'tree' of containers.

It works with most languages/toolkits. I've tried it with may. Since this is a Ubuntu forum, I decided to show it in GTK :)

I do my GUI code like this. I haven't tested this, as I haven't got a Ruby interpreter atm. This can be made a lot shorter using Ruby's functional features, but the point of this more expanded one is that it shows a 'tree' of containers.
```

require 'gtk2'

class GtkGui
  include gtk

  def initialize
    @window = Window.new().add(
      VBox.new(false, 0).pack_start(
        HBox.new(false, 0).pack_start(
          Button.new('One')).pack_start(
          Button.new('Two'))).pack_start(
        HBox.new(false, 0).pack_start(
          Button.new('Three')).pack_start(
          Button.new('Four'))))
  end

  def launch
    @window.show_all
    main
  end
end

GtkGui.new.launch

```
See what I mean? I can clearly tell by looking at the side of the code what's inside what. So why do so many use the one-after-another style?

---

### Post by nvteighen on 2010-01-11
> **SunSpyda said:**
> When I do GUIs, I have a way of doing them, but people keep telling me it's cryptic. Yet I think it's easier, since it makes the left-hand side of the code look like a 'tree' of containers.

It works with most languages/toolkits. I've tried it with may. Since this is a Ubuntu forum, I decided to show it in GTK :)

I do my GUI code like this. I haven't tested this, as I haven't got a Ruby interpreter atm. This can be made a lot shorter using Ruby's functional features, but the point of this more expanded one is that it shows a 'tree' of containers.
```

require 'gtk2'

class GtkGui
  include gtk

  def initialize
    @window = Window.new().add(
      VBox.new(false, 0).pack_start(
        HBox.new(false, 0).pack_start(
          Button.new('One')).pack_start(
          Button.new('Two'))).pack_start(
        HBox.new(false, 0).pack_start(
          Button.new('Three')).pack_start(
          Button.new('Four'))))
  end

  def launch
    @window.show_all
    main
  end
end

GtkGui.new.launch

```
See what I mean? I can clearly tell by looking at the side of the code what's inside what. So why do so many use the one-after-another style?

There are several reasons: Sometimes it's better to have a name for a certain thing instead of having everything anonymous. For example, what if you after doing that want to get some data of one specific widget to store it somewhere else? As soon as you want to use something more than once, you're lost without a name (ok, you could use the containers' methods to grab stuff... but that gets quite cryptic and also makes your code less flexible).

There's another reason, which is actually historical/technical. You surely know all these toolkits are originally written in C or in C++, which don't have manual memory management. Specially in C, where you have to deal almost just with dynamic memory allocation (in C++ you can allocate a widget in the stack more easily), all widgets are required to be manually freed from memory so you need to give them a name in order to make e.g. gtk_widget_destroy(widget) call in GTK+. If you start creating stuff anonymously, you'll be leaking a quite good amount of memory. So, that pattern seems to have been translated into garbage collected languages; I've noticed PyGtk code is forcedly more C-ish than a regular Python code (e.g. you get a mixed OOP/procedural system because of how GTK+ callbacks work)... And I guess PyQt code also introduces more C++-isms into Python (I'm not that familiar with C++ in order to spot them). 

But, IMO, your idea is useful if handled with care. For example, in languages like Python or Ruby, one could easily declare all containers that way and then use names for "interesting" widgets that "deserve" a name (:p).

What I do is to create custom "constructors" (procedures that return the widget I want by taking all necessary arguments to have it like I want it to be, not constructors in the C++ sense), so that I modularize the GUI initialization process into a modular one. The whole initialization for widget X is made at "make_x()", including packaging and signal (initial) declaring. That way, I can reuse the make_x() procedure and I know that everything realted to "making an X" is done there and not somewhere else.

---

### Post by SunSpyda on 2010-01-11
The anonymous thing is true, but as you said, many just need to 'be there' rather than 'named and known'. I can think of a easy solution in Ruby that won't screw up the code size - just make a button function that returns a anonymous button instance, that has already had it's name set/event handling connected using a iterative solution (eg, use a function with a static iterator to use n passed to it to select the event function from a static list, and return a button which is connected... or something like that :) )

My C/GTK code is full of loops and arrays of GtkButton pointers and properties (names, event functions, etc). Then, a big loop just sets all the buttons up and then another frees them all by iterating through the pointers. I do this because I can't *stand* repetitive C coding, now I've used more 'clever' languages like Haskell and Ruby.

---

### Post by spupy on 2010-01-11
> **SunSpyda said:**
> 
See what I mean? **I can clearly tell by looking** at the side of the code what's inside what. So why do so many use the one-after-another style?

You can, but others can't. If it's only for you, OK, go ahead. But don't torture other people that will someday look at your code.

---

### Post by pelle.k on 2010-01-11
> You can, but others can't.
I think it's pretty elegant, actually. Too bad there is no "standard practice" for these kind of things. I mean to clearly mark relationship of the GUI elements represented in the code, using the code layout. That could be quite handy.
I guess if all GUI elements were done with say XML that would not upset the flow of the code, while giving you the ability to nest "naturally" within the XML.

---

### Post by worseisworser on 2010-01-12
> ..by looking at the side of the code what's inside what..

Ok, yeah, you might find Lisp interesting; this is done *all the time* in Lisp -- and people say the same things about it.   (edit: fwiw i don't agree with them)

---

### Post by spupy on 2010-01-12
> **worseisworser said:**
> Ok, yeah, you might find Lisp interesting; this is done *all the time* in Lisp -- and people say the same things about it.

Haha, I was wondering why his code seemed so familiar. :D

---

### Post by SunSpyda on 2010-01-12
> **spupy said:**
> Haha, I was wondering why his code seemed so familiar. :D

Ok, so I admit, that I did get the idea when I was programming Haskell ;)

---

### Post by nvteighen on 2010-01-12
Well... that's another possible flaw of this system... It's quite clear you got the idea from Functional Programming and as such, your system will work until you don't introduce state. As soon as you want to express state in your GUI, you'll run into issues unless you somehow implement monads in Ruby or Scheme streams (which are a bit limited to how much state they can simulate up).

---

### Post by Reiger on 2010-01-12
Looks like: java beans.

---

### Post by nrs on 2010-01-12
How would you deal with callbacks, etc? If it was inanimate, like a spacer or something, maybe.

---

### Post by worseisworser on 2010-01-13
> **nrs said:**
> How would you deal with callbacks, etc? If it was inanimate, like a spacer or something, maybe.

I'm sure he can assign IDs to each node in the tree on-the-fly when constructing using an argument to the constructor (new), then assign callbacks *based on those* IDs after the entire tree/layout code section is done.

This is how one assign callbacks when using e.g. Glade anyway, and anything else could get messy if the callbacks used are *inline code* (e.g. lambda) that aren't small in size.

---

