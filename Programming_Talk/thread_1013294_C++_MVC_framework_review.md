---
title: "C++ MVC framework review"
date: 2008-12-16
forum: Programming Talk
---

### Post by Sydius on 2008-12-16
I just released the first version of a model-view-controller framework I've been writing for C++.  I have games in mind for it, though it is abstract enough that it could be used for something else.

Models subclass the Model class and are the most loosely-coupled elements in the design.  They don't depend on anything.

Controllers subclass Controller and attach themselves as observers to a System object to listen for input or other kinds of notifications from the underlying system.  The controller updates Model(s) and selects a View (or, more likely, a ViewComposite) to display.

Views subclass View and can be contained within ViewComposites.  They attach themselves to Model(s) to listen for changes to Model updates (optional) and are called to display by a Controller.

The Controllers and Views (but not Models!) depend on a SystemInterface, which is just an interface for an underlying system.  A System object implements the SystemInterface.  An example of a SystemInterface would be ConsoleInterface and an example of a System would be a ncursesSystem.  The goal is that there could be multiple implementations of a single SystemInterface, possibly for different platforms.

Finally, there is a Facade object that the application might subclass itself from.  The Facade is an interface to everything else and is responsible for registering Models, Views, and Controllers, as well as initializing a System.  The rest of the system interacts via the Facade. I intentionally avoided the use of singletons.

I would like a review of the code quality.  I don't expect anybody else to use it yet (though, if you want to, go ahead!), but I would like to know if there are any obvious problems with the quality of the code.

You can browse the code at [http://code.google.com/p/sydmvc/source/browse/#svn/trunk](http://code.google.com/p/sydmvc/source/browse/#svn/trunk) without needing to download it.

I will attach an example (albeit very sloppy) implementation of it.  I know it's sloppy; it was written haphazardly while writing the actual framework.

I'm only interested in comments about the framework, not the attached example usage of it.

[http://code.google.com/p/sydmvc/source/browse/#svn/trunk](http://code.google.com/p/sydmvc/source/browse/#svn/trunk)
[http://code.google.com/p/sydmvc/](http://code.google.com/p/sydmvc/)

---

### Post by dwhitney67 on 2008-12-16
Your design looks great!  I state this because I know that there is no way I could have conjured up such a design.  I'm sure you have put diligent effort into testing it, thus I'm sure it is a solid design.

I've worked on GUIs in the past that employed MVC paradigm.  The operator (user) interacts with the Viewer; in turn the Controller is notified of the action, and then updates the Model.  Sometimes an external input is received, by the Controller, which in turn updates both the Model and the Viewer.

I only saw a couple of petty things with your code; one is the inclusion of system header files *before* including local header files, and the other is for not returning a value from the macro that defines the main() function.

Another thing that would be nice to see with the presentation of your design is a UML diagram.  That way one could understand the relationship between the class objects without having to open multiple tabs in their web browser, and also not have to be fluent in C++.

---

### Post by Sydius on 2008-12-17
> **dwhitney67 said:**
> not returning a value from the macro that defines the main() function

See [ ISO/IEC 14882:1998](http://www.kuzbass.ru:8086/docs/isocpp/basic.html), Section 3.6.1, item 5.  Not returning anything from the main function is equivalent to returning 0 (and perfectly valid).  Perhaps, however, I should allow for the return of arbitrary values.  It could be handy.

As for the header files, I have been trying to follow the [Google C++ Style Guide](http://google-styleguide.googlecode.com/svn/trunk/cppguide.xml#Header_Files) for MOST things, but I didn't notice the header issue.  I'll fix it, thanks.

---

### Post by Kazade on 2008-12-17
From the sample code there are just two little (very minor and pedantic) niggles that I thought I'd mention. To quote the great Herb Sutter:

> 
TO_PUT_IT_BLUNTLY: Macros are the bluntest instrument of C and C++'s abstraction facilities, ravenous wolves in functions' clothing, hard to tame, marching to their own beat all over your scopes. Avoid them.


With that in mind. I would suggest that instead of the #defines at the top you use "const" variables (I know it's a sample this one so minor).

More importantly, instead of your "DISALLOW_COPY_AND_ASSIGN" macro take a look at boost::noncopyable, (which is also very easy to implement yourself if you don't want to depend on boost - Scott Meyers Effective C++ has an item on this IIRC).

I like your idea of the design, I'll take a look at the source of it in a bit. It looks really interesting! :)

---

### Post by Kazade on 2008-12-17
I've had a quick look. The code looks very clean, very nice!

Just a few suggestions:

1. Use tr1::shared_ptr or boost::shared_ptr instead of raw pointers in the containers (ModelList etc.) and for the member pointers. This will shrink down your code a bit and help to prevent any leaks.

2. There is no need to check if a pointer is NULL before calling delete. If the pointer is NULL delete will do nothing.

3. Consider using the NVI (non-virtual interface) idiom, your design is a good candidate for it.

---

### Post by Sydius on 2008-12-17
I was attempting to avoid bringing boost in as a dependency, at least in the core of the framework, but I will take it into consideration.

---

### Post by eeyore on 2009-06-25
Your library looks really nice. I've picked it up for a little pet project I have, and have noticed one deficiency that I have to work around. I don't like the fact that the events have to be integers. Templating that type would be a wonderful addition to the library.

---

### Post by kennbox on 2009-11-03
Your Design is straight enough. I found it quite useful and educative.   Thanks a Lot   A uml layout of the classes is attached. Hopes it helps.

---

### Post by dribeas on 2009-11-04
I have given it just a quick glipse, and besides the issues already brought up (you should use smart pointers, boost::noncopyable or other inheritance based solution is better than a macro, no need to check for null prior to deletion, no need to set attribute pointers to 0 in destruction [they will not exist as soon as the destructor completes]), I think that you should really document your template arguments. 

I gave it just a minute worth of browsing, and while browsing the code the three files I opened defined a templated class on an argument 'I', but that is not documented. I may find some time later in the week to take a deeper look into the design/code, just not now.

---

### Post by A_Fiachra on 2009-11-04
> **kennbox said:**
> Your Design is straight enough. I found it quite useful and educative.   Thanks a Lot   A uml layout of the classes is attached. Hopes it helps.



How did you generate that diagram?

Or did you do it by hand?


Thanks ..

---

