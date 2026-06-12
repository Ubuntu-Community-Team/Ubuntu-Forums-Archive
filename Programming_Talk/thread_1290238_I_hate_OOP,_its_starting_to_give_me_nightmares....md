---
title: "I hate OOP, its starting to give me nightmares..."
date: 2009-10-13
forum: Programming Talk
---

### Post by J V on 2009-10-13
I just don't get OOP, never have, probably never will...

I have tried to use mvc to organize my OOP into something that isn't just a list of functions, and also works...

Getting to the point: I have no idea how I should go about writing this application.

First a small login window pops up where you can create, edit, delete, or login to an account.

Once you login the main window appears where most of the work is done.

Other windows can be opened from this main window, but it will remain there until the end of the application.

Now my first problem is, that I want (Or at least, I think I want) there to be a head model and controller for the entire app, so that the login window can be an offshoot, and everything will work...

The problem is that this means the model and controller have to create children for the login window, but the view has to be connected to the children rather than the top-levels.

If that happens then I have to create views with the controller? What the hell?

I thought they were all supposed to be seperate?

I don't get this at all...

Small demo:
```
m = myModel()
v = myView()
c = myController()

class myModel:
    #create sub-model for login form
class myController:
    #create sub-controller for login form
class myView:
    #do whatever it is that a view does
class subModel:
    #work the profile selector
class subController:
    #and this has to patch the whole application together or something?!
```Sorry if I'm confusing you, as you can see I don't have any idea what I'm doing...

---

### Post by korvirlol on 2009-10-13
What language are you doing this in?

Im not really sure if i understand what youre getting at here, so my apologies if this answer isnt helpful.

I'd probably start with a parent class called Window, which implements the most basic and essential aspects of all windows (resize, move, etc) and force virtual functions that must be inherited by children objects. You could then create subclasses, like, LoginWindow or MainEventWindow that implements the above virtual functions in their own way (for their own exection), and other functions needed by then.

You could then create some sort of window decorator class(or probably class hierarchy) that Window Objects create. This might be something like, parent class: WindowObject, with subclasses, Button and ScrollBar. 

I dont know what you mean by a window controller? Maybe some sort of data structure that stores all of the currently created Window objects(vector, array)?

Ive mainly had experience with OOP in c++ and this is where a lot of my answers are coming from

---

### Post by J V on 2009-10-13
I'm writing in python with pyGTK and gtkmvc modules, gtkmvc is designed to keep programmers from making non-OO like mistakes...

It means there should only be one way to do what I'm trying to do, unfortunatley, I still screwed up :|

[http://sourceforge.net/apps/trac/pygtkmvc/wiki](http://sourceforge.net/apps/trac/pygtkmvc/wiki)

---

### Post by benj1 on 2009-10-13
object are just there to help you split up the code, its not hard but i know what you mean, books always seem to describe it interms of shapes or colours, which for me made it as clear as mud.

basically for this project you will probably want at least two classes (i dont really know what youre wanting to do, but broadly speaking...) a gtk one and a behind the scenes one(more if you have completely separate, unrelated pieces of behind the scenes code), those can be kept completely separate from each other appart from the passing of objects, the main advantage is supposedly so that to can say swap out gtk for qt bindings without having to go through all of your code etc, plus you then have well define communication channels between classes.

---

### Post by TheBuzzSaw on 2009-10-13
You really have to have the proper exposure to OOP in order to understand its benefits. There are many design patterns you can use to get the job done.

If you use OOP well, it can save you a ton of work. The idea is that you can change an object's underlying behavior without having rewire how all the other objects talk to it. By giving each object a clear objective (no pun intended), it can likely be used in multiple cases and maybe even reused in future projects.

It is worth researching. I cannot count the number of times that OOP has saved me. I later realize I coded something wrong, so I go back, gut out the object, recode it, and everything works fine (I don't have to go anywhere else in the code and change anything because the object's purpose was still the same).

---

### Post by hessiess on 2009-10-13
OOP is just a paradigm for doing stuff, not a magical technique that fixes everything;) It is verry good for some things, like game dev, and very bad for a lot of other things.

---

### Post by J V on 2009-10-13
3 completely conflicting answers, one even more confused OO noob :)

Ok, lets say I do want to do OOP, and I'm using the MVC template, all I want is to have a parent model and controller for the entire app, and open 2 windows without one being above the other...

Does anyone know how I do this? I don't want to have to do some "self.parent.parent.parent.parent.newObj" code later on in the program yknow?

---

### Post by nvteighen on 2009-10-13
I think you (the OP) are confusing a lot of things and that way making your path to OOP much harder than it really is.

1) OOP is just about organizing your code thinking about objects that have some propierties and do some actions... and interact with eachother. That's it. Some languages like Python will give you explicit syntactic devices to handle OOP in an easier way than without them.

2) MVC is not OOP. Moreover, MVC is a really hard thing to learn if you don't have OOP clear. Try some simpler: Create a class that holds the implementation and a class that holds the user interface; design the first one that way that you can imagine the second is a human that executes the code in the implementation class as if it were "typing" into a shell.

3) OOP is not the programming silver-bullet, neither any of the remaining paradigms or design patterns is. OOP is useful because we humans tend to think in terms of objects, but sometimes is much better to think in terms of stateless functions (functional programming) or in terms of data (logical programming)... or in terms of code itself (metaprogramming). IMO, the best thing for a lot of problems is a combination of OOP with standard procedural programming.

4) GTK+ is a pretty monstrous thing. And it's a place were I drop my general advice of "learn the higher level first". IMO, PyGTK is easier to learn having dealt with C GTK+ because PyGTK, even though it has done a great job translating it into Python, it shows a lot of C-isms that make PyGTK code slightly weird compared to "idiomatic Python". (Curiously, PyQt didn't gave me that impression of C++-isms... though I confess I haven't worked that much with Qt in general than with GTK+).

I hope you're working with the PyGTK API docs at your side...

---

### Post by mehaga on 2009-10-13
If you don't get OO, you won't understand it by learning MVC :)

[This]("http://oreilly.com/catalog/9780596007126") is 'a brain-friendly' book about design patterns, which might help you understand OO better.

Like someone else already said, MVC is a paradigm that can be implemented in many ways. 
It simply means separation of your app into M, V and C, but by itself it doesn't tell you how to implement that separation. 

MVC can be implemented as a combination of some basic design patterns (e.g. observer, strategy, command...), so it might be helpful to understand them first. 

You said "...I have to create views with the controller? What the hell?", but that actually is one way of doing it. 
[Read this]("http://martinfowler.com/eaaDev/uiArchs.html").

I think it is very important that you don't see it as a 'silver bullet' that is suitable for any kind of UI. Also, I think most people find it complex at first, don't think you're alone :)

---

### Post by J V on 2009-10-13
I certainly don't think of it as a silver bullet, but I've been trying to work with it for the past year (about 40 hours of failures) and I am still right where I started (I have this thing with maths and programming ideas I don't already understand, either it comes as a revelation or I won't understand it at all...)

Is there an other way to use OOP in a GUI application other than MVC? Is it worth it? (Considering functional programming means its impossible to actually destroy a window, only hide it, or else you have to bundle the whole damn thing into one huge file)

Thanks for the links vekaz, will post back about my most recent mind-twists...

---

### Post by doas777 on 2009-10-13
oop is a far simpler (and thus far wider reaching and fundamental) concept than I think you are realizing. I think you are making mountains out of molehills.

---

### Post by mmix on 2009-10-13
[http://live.gnome.org/Vala](http://live.gnome.org/Vala)

[http://live.gnome.org/Vala/GTKSample](http://live.gnome.org/Vala/GTKSample)

---

### Post by mehaga on 2009-10-13
> **doas777 said:**
> oop is a far simpler (and thus far wider reaching and fundamental) concept than I think you are realizing. I think you are making mountains out of molehills.
Sorry, but I disagree. *Good* OO isn't simple at all.

---

### Post by doas777 on 2009-10-13
> **vekaz said:**
> Sorry, but I disagree. *Good* OO isn't simple at all.
it is, but because of it's size and fundemental nature, there is a lot there to know and understand. I think we prolly agree, but on different levels.

---

### Post by Reiger on 2009-10-13
OOP is simple in its basic form: you have an object which holds data and functions that do useful stuff with that data. This is mostly about does-the-same-kind-of-things-differently.

OOP is fairly complex in its intermediate form: you have an API of some form or another which must be implemented on one side and talked to on another side. This is where things like &#8216;interface&#8217;, &#8216;abstract&#8217; and &#8216;virtual&#8217; starts popping up.

OOP is a fairly non-issue in its more advances forms like MVC. The real problems arise when you want to side-step OOP for things like global variables (those are inherently non-OO by nature of their global-ness) and OOP turns out to require some pretty complex hoop-jumping to model something as simple as a global variable i.e. singletons.

If you want to learn MVC a good starting point would programming Swing apps with Java. It sort of follows out of its own accord that you learn to understand MVC as you grasp Java/Swing and as you learn how to code Swing apps such that adding, say, a menu bar which holds duplicate entries for your tool bar buttons no longer means doing lots of duplicate work.

---

### Post by benj1 on 2009-10-13
it sounds like you may be having more problems with pygtk
its not the easiest, best documented or best written lib to get to grips with
i used [http://zetcode.com/tutorials/pygtktutorial/]("http://zetcode.com/tutorials/pygtktutorial/")
which has fairly clear examples

---

### Post by kavon89 on 2009-10-13
I learned programming with Java so OO is my default way to solve a problem. IMO you can't apply it well to a GUI other than getter/setter methods and some interfaces on the graphical components so I wouldn't worry about it. Your back-end or logic code (the controller in mvc) often can be simplified if using OO.

I read a good introduction to what OO is and how it's useful in one of my Java books, before that I was in the same boat as you.

---

### Post by nmccrina on 2009-10-13
If you are trying to learn OOP, I recommend doing it in Java. I was taught ("taught") OOP in college using C++, but it wasn't until I went through Head First Java on my own that the whole object-oriented thing "clicked". After that, I realized how powerful OOP is, and C++ made a lot more sense too; I actually prefer C++. 
Also, for GUI I found Swing the easiest to build stuff with, and also QT (which kind of feels similar to Swing except for event handling). GTK, in my experience, was a mess. Of course, I only got half way through the tutorial before giving up in disgust, so I could be wrong ;) Keep in mind, that GTK is not object-oriented, even though you're using an object-oriented language to interact with it; so don't blame (all) of your frustrations on OOP! 
Ever since trying out GTK I haven't been able to figure out why GNOME seems more stable than KDE, when *clearly* QT is so much easier to develop with. :P

On the other hand, every time I run into these "OOP is absolutely the most awesomest way to program, in every situation!" people (one of my professors is like this, or at least it seems that way) I want to start programming exclusively in C or Assembly or something just to show 'em.

---

### Post by doas777 on 2009-10-13
the head first series is great for the broad conceptual stuff that requires some paradigm shift.

---

### Post by nmccrina on 2009-10-13
> **doas777 said:**
> the head first series is great for the broad conceptual stuff that requires some paradigm shift.

I was going to warn people that it's a little corny (at least, the Java one was), but it did explain stuff very well, while providing examples that will stay in your head forever (for better or worse :P ). In other words, it's not a textbook. Which I guess is a good thing.

---

### Post by CptPicard on 2009-10-14
> **nmccrina said:**
> On the other hand, every time I run into these "OOP is absolutely the most awesomest way to program, in every situation!" people (one of my professors is like this, or at least it seems that way) I want to start programming exclusively in C or Assembly or something just to show 'em.

Well, asm and C are not the only options to Simula-style OOP that C++ and Java follow, although it is true that in most minds "OOP" means exactly the object-oriented extensions to Algol-family languages, in particular the descendants of C...

I can feel OP's pain as I felt that during my learning the "pattern-based" bureaucratic programming model of static-typed OOP was what held me back most. The issue with object-obsessed languages like Java is that before you're able to really meaningfully design any kind of program, you need to be quite well versed in all kinds of design patterns, which always gave me the feel that "ok, we've designed that we've got to have these kinds of objects, so this is what you must do with them to force them to be what you're thinking about". That is, the patterns often feel like they are cures to a symptom...

This is btw why I like the way Python approaches object-orientedness... it is not dictated on you, but an "object" is still a very natural entity in language, and duck-typing allows for your class interfaces to naturally evolve and come into being as you write code, and not the other way around -- that you need to set your structure in stone before you write one line!

In Java, Netbeans' refactorings are also awesome in discovering the object structure as you go. As I am very used to writing in terms of closures in languages that have them, there is nothing handier than to just drop in an ad hoc implementation of some interface when I need it, and then split it out into a class of its own as I need it. Often that further evolves either into a class hierarchy by pushing functionality "up" into a base class, or more commonly these days as I internalize the idea of "coding to interfaces", an interface hierarchy...

---

### Post by J V on 2009-10-14
Ive been refreshing this thread for hours, but I never noticed the second, and third pages...

I am very linear, I prefer functional programming, and when it comes to game programming I'm completely confused because the loop is so non-linear...

The only thing keeping me from completely switching to a functions only application is that something like signal_autoconnect(self) won't work...

If I could understand how I can start an application with one window (set of subobjects) and then create the main window on the same hierarchical level as the start window...

Along with some way to create new "View" objects without them having to be hierarchied so I can have individual windows, I could work with that... 

If someone would just show me some empty classes in the correct order, I could fill them in myself... I semi-understand objects, but I am completley incapable of creating a working GUI architecture (Even off a predefined template such as gtkmvc)

---

### Post by nvteighen on 2009-10-14
> **J V said:**
> 
I am very linear, I prefer functional programming, and when it comes to game programming I'm completely confused because the loop is so non-linear...


I think when you refer to "functional programming" you are referring to "procedural programming". Functional programming is something **completely** different (and really worth to learn!)

[http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming)
[http://en.wikipedia.org/wiki/Procedural_programming](http://en.wikipedia.org/wiki/Procedural_programming)

---

### Post by doas777 on 2009-10-14
> **J V said:**
> Ive been refreshing this thread for hours, but I never noticed the second, and third pages...

I am very linear, I prefer functional programming, and when it comes to game programming I'm completely confused because the loop is so non-linear...

The only thing keeping me from completely switching to a functions only application is that something like signal_autoconnect(self) won't work...

If I could understand how I can start an application with one window (set of subobjects) and then create the main window on the same hierarchical level as the start window...

Along with some way to create new "View" objects without them having to be hierarchied so I can have individual windows, I could work with that... 

If someone would just show me some empty classes in the correct order, I could fill them in myself... I semi-understand objects, but I am completley incapable of creating a working GUI architecture (Even off a predefined template such as gtkmvc)


I think you may be confusing the "objects" (windows, frames, buttons, dropdowns) used in GUI programming, with the more abstract objects used in OOP. I recall that I had a similar mental block when I first started working with objects. when we talk about OOP, most of the objects we are talking about do not have a visible component (though gui components are usually a conglomerate of coded objects). 

just remember, a window may be an object, but an object is not necessarily a window. 
you may want to start a thread more specific to your issue with the gui tools you are working with.

---

### Post by J V on 2009-10-14
"I think you may be confusing the "objects" (windows, frames, buttons, dropdowns) used in GUI programming, with the more abstract objects used in OOP." 

No I amn't... In the case of the GUI I can clearly see the use of OOP, it's very good for GUI creation, but the backend just doesn't seem to work...

I not only can't see a hierarchy between non-existing objects, or a reason for splitting them up (And subsequently making it impossible to create a new one without screwing up the architecture or using globals), I just don't see anything at all that would make objects helpful for a backend...

I would just use callbacks for the entire application if the file wasn't so huge and the creation of classes such a pain in the *** (Predeclaring everything or it becomes a sub-object of the current hierarchy)

I'm sorry, I'm asking hackers questions about OOP while I should be asking a hacker/psychiater why the hell my brain has stopped working ](*,)

---

### Post by J V on 2009-10-15
Well if no-one has a good idea about an architecture, can someone at least tell me why this isn't working so that I can mark this solved?

```
import pygtk
pygtk.require("2.0")
import gtk
from gtkmvc import View
from model import AppModel
from controller import AppCtrl

if __name__ == "__main__":
    m = AppModel()
    v = View(None, "profile_select.glade", "window") # This needs to be linked to a controller after it's been created, getting libglade errors all the time no matter how I try to call the class
    c = AppCtrl(m) # This is the head controller, all windows have their own subcontrollers, hence it isn't linked to a view
    gtk.main()
```I think hte applicable error message here is: "Expected <glade-interface>.  Got <interface>."

View() is trying to load gtkbuilder with libglade?

---

