---
title: "Gtk, Where to put exit code / freeing memory"
date: 2011-02-11
forum: Programming Talk
---

### Post by captnemo on 2011-02-11
I have two questions really:

The environment is Linux, standard Gnu C, Gtk.

1) Where is the best place to put cleanup exit code in a Gtk app?  In main() after Gtk returns from its main loop?  Or is there a callback I can register where I put cleanup code?  Or...?

2) Memory management: I have an app that allocates and frees bits of memory during operation.  There's no question there.  But this app also has about 50 chunks of memory totalling about 500k that are allocated at startup and used for the duration of the program.  Do I need to free those before exiting or does the OS take care of that for me?

Long ago it was necessary to be diligent about freeing all memory, otherwise unfreed memory became "zombied" when an app exited.  But modern OS's keep track of which process owns which memory and freeing is automatic so is freeing memory on exit really necessary anymore?

---

### Post by worksofcraft on 2011-02-11
> **captnemo said:**
> I have two questions really:

The environment is Linux, standard Gnu C, Gtk.

1) Where is the best place to put cleanup exit code in a Gtk app?  In main() after Gtk returns from its main loop?  Or is there a callback I can register where I put cleanup code?  Or...?

2) Memory management: I have an app that allocates and frees bits of memory during operation.  There's no question there.  But this app also has about 50 chunks of memory totalling about 500k that are allocated at startup and used for the duration of the program.  Do I need to free those before exiting or does the OS take care of that for me?

Long ago it was necessary to be diligent about freeing all memory, otherwise unfreed memory became "zombied" when an app exited.  But modern OS's keep track of which process owns which memory and freeing is automatic so is freeing memory on exit really necessary anymore?

I don't think it is necessary but if you did start using object oriented techniques then freeing the memory would often be associated with a "destructor" activity.

That might be important like to flush out any buffers before closing associated files. Also I get the impression that things relating to X11 as well as GTK can still be left "zombied" if not tidied up properly :shock: (no concrete evidence atm).

It is probably just good practice to try make sure you do actually define "constructor" and "destructor" kind of functions that will be called even when not strictly necessary.

---

### Post by captnemo on 2011-02-11
> **worksofcraft said:**
> I don't think it is necessary but if you did start using object oriented techniques then freeing the memory would often be associated with a "destructor" activity.

That might be important like to flush out any buffers before closing associated files. Also I get the impression that things relating to X11 as well as GTK can still be left "zombied" if not tidied up properly :shock: (no concrete evidence atm).

It is probably just good practice to try make sure you do actually define "constructor" and "destructor" kind of functions that will be called even when not strictly necessary.

Object oriented does not necessarily mean clean disciplined code.  After over 40 years of practice I have methods for writing very modular code.  Each module has externally visible startup/initialization and shutdown/cleanup function calls.  Now it's time to figure out the best place to call all the shutdown functions and I'm not exactly sure where it's best to do that in a Gtk app.

I want a spot where I'm sure there will be no more events.  It would seem that in main() right after the gtk main loop returns would be the spot, but maybe there's a better one, or one specifically provided by Gtk.

---

### Post by TpwUK on 2011-02-11
The GTK+ programmers guide says that gtk_exit is now deprecated and a simple exit() is all that is required and that GTK+ will clean up after itself.

If i am understanding you correctly - I would implement a clean-up phase of the GTK parts that you use, then call the exit() then do any other housework in your main and exit. You could i suppose set it all to a function that handles any exceptions or errors before terminating

TpwUK

---

### Post by worksofcraft on 2011-02-11
> **captnemo said:**
> Object oriented does not necessarily mean clean disciplined code.  After over 40 years of practice I have methods for writing very modular code.  Each module has externally visible startup/initialization and shutdown/cleanup function calls.  Now it's time to figure out the best place to call all the shutdown functions and I'm not exactly sure where it's best to do that in a Gtk app.

I want a spot where I'm sure there will be no more events.  It would seem that in main() right after the gtk main loop returns would be the spot, but maybe there's a better one, or one specifically provided by Gtk.

IMO the term "Object Oriented" was coined precisely to describe the practices that you refer to. Recently I saw some code written in Fortran IV back in the early 70's and it was beyond a doubt OO even if nobody had thought of that name yet... i.e. modular with initialization and cleanup and the data and implementation details all encapsulated...

Whatever... as I program in C++ I leave the cleanup to where destructors get called implicitly. Thus in a way the need for memory management actually promotes modular design: e.g. the gtk_builder is no longer needed even before I enter the gtk_main loop so I localize it within a function that as sole outputthe widget tree I want while the other bits are disposed of.

Although I've never had cause to write a program with multiple gtk main loops yet I gather it IS possible and you might want to pass constructs from one loop to the next, disposing of things that are encapsulated within such a module. IOW IMO there isn't really any hard and fast rule of where to do the house keeping as it depends on what follows and what is needed there... hum perhaps I misunderstood your question :confused:

---

### Post by captnemo on 2011-02-12
> **worksofcraft said:**
> IMO the term "Object Oriented" was coined precisely to describe the practices that you refer to. Recently I saw some code written in Fortran IV back in the early 70's and it was beyond a doubt OO even if nobody had thought of that name yet... i.e. modular with initialization and cleanup and the data and implementation details all encapsulated...

Whatever... as I program in C++ I leave the cleanup to where destructors get called implicitly. Thus in a way the need for memory management actually promotes modular design: e.g. the gtk_builder is no longer needed even before I enter the gtk_main loop so I localize it within a function that as sole outputthe widget tree I want while the other bits are disposed of.

Although I've never had cause to write a program with multiple gtk main loops yet I gather it IS possible and you might want to pass constructs from one loop to the next, disposing of things that are encapsulated within such a module. IOW IMO there isn't really any hard and fast rule of where to do the house keeping as it depends on what follows and what is needed there... hum perhaps I misunderstood your question :confused:

No, I think you understood correctly.  This is a multi-threaded real-time application with its own main-loop handler, its own jiffy timer handler, task scheduler, linked lists of tasks to be executed, semaphores and buffers to communicate between threads, and between threads and main, etc.  It basically implements its own real-time operating system and it works beautifully under Gtk, which is a tribute to Gtk.  It all works exactly as expected.

When it comes time to exit, a global exit semaphore is raised which signals all the threads to shut down.  Once that has happened, the threads have all freed the memory they were using and all I'm left with is about 50 chunks of globally visible memory that I would like to free before exiting completely and I'm wondering where to put that bit of code.

My guess is in main() after gtk_main_loop() exits but I'd like to know if there's a better way or a way that the Gtk designers would prefer.

---

### Post by TpwUK on 2011-02-12
> No, I think you understood correctly.  This is a multi-threaded  real-time application with its own main-loop handler, its own jiffy  timer handler, task scheduler, linked lists of tasks to be executed,  semaphores and buffers to communicate between threads, and between  threads and main, etc.  It basically implements its own real-time  operating system and it works beautifully under Gtk, which is a tribute  to Gtk.  It all works exactly as expected.Thank god for that, i wouldn't like trying to sort any problems with that :P

> When it comes time to exit, a global exit semaphore is raised which  signals all the threads to shut down.  Once that has happened, the  threads have all freed the memory they were using and all I'm left with  is about 50 chunks of globally visible memory that I would like to free  before exiting completely and I'm wondering where to put that bit of  code.Ok that's the interesting bit to me - If you have 50 chunks of memory still allocated, then logic dictates that either you used them in your main or that your threads have not been cleaning up behind themselves before the exit was issued. If you used them before calling gtk, then they are your mess, if they are left over from gtk then i guess the exit() call don't do as said,  i.e it don't clean up after itself, in which case that's something you would need to take up with the gtk developers :(

>  My guess is in main() after gtk_main_loop() exits but I'd like to know  if there's a better way or a way that the Gtk designers would prefer.     If cleaning up within your main() does not make your code unreadable and difficult to understand or follow, then do it there. If it will look odd or out of place, then do it as a function call and handle any errors or exceptions that get raised if any. Once gtk has been and gone, gtk aint gonna care as long as those "chunks" were not left over from gtk, or that your chunks don't interfere with any future calls to gtk

To me it sounds as if you have a wonderful piece of work and that you are worrying a little too much about how clean it should be. That is down to how efficient you want to be, and no-body can fix that bit. If you have potential security issues with them "chunks" - then clean them up as soon as possible.

My next question is, if you have 50 chunks left over, is this 100 next time it's run, 150 there-after etc etc, if that's the case then you have a memory leak problem

TpwUK

---

### Post by captnemo on 2011-02-12
> **TpwUK said:**
> Thank god for that, i wouldn't like trying to sort any problems with that :P

Ok that's the interesting bit to me - If you have 50 chunks of memory still allocated, then logic dictates that either you used them in your main or that your threads have not been cleaning up behind themselves before the exit was issued. If you used them before calling gtk, then they are your mess, if they are left over from gtk then i guess the exit() call don't do as said,  i.e it don't clean up after itself, in which case that's something you would need to take up with the gtk developers :(

If cleaning up within your main() does not make your code unreadable and difficult to understand or follow, then do it there. If it will look odd or out of place, then do it as a function call and handle any errors or exceptions that get raised if any. Once gtk has been and gone, gtk aint gonna care as long as those "chunks" were not left over from gtk, or that your chunks don't interfere with any future calls to gtk

To me it sounds as if you have a wonderful piece of work and that you are worrying a little too much about how clean it should be. That is down to how efficient you want to be, and no-body can fix that bit. If you have potential security issues with them "chunks" - then clean them up as soon as possible.

My next question is, if you have 50 chunks left over, is this 100 next time it's run, 150 there-after etc etc, if that's the case then you have a memory leak problem

TpwUK

Those 50 or so blocks of memory basically contain lookup tables of pre-calculated data.  They were allocated by main() at startup and so should be freed by main.

I guess what I'm asking can be phrased differently as follows:

Does the function gtk_main() always return?  In other words, is code that is located after the function call to gtk_main() guaranteed to execute before the program shuts down, no matter what?

Obviously, if there's a seg-fault crash or something where the OS kills the task then all bets are off but in an orderly shutdown does gtk_main() always return or does gtk sometimes do some kind of internal exit without ever returning to main()?

---

### Post by TpwUK on 2011-02-12
Does this help any ?

[http://developer.gnome.org/doc/GGAD/sec-mainloop.html](http://developer.gnome.org/doc/GGAD/sec-mainloop.html)

You are way beyond my level of programming on linux .. I was just applying logic without truly understanding the issue you have. If you ever do get to the bottom of it i would love know myself now, curiosity peaked and all that :)

TpwUK

---

### Post by captnemo on 2011-02-12
> **TpwUK said:**
> Does this help any ?

[http://developer.gnome.org/doc/GGAD/sec-mainloop.html](http://developer.gnome.org/doc/GGAD/sec-mainloop.html)

You are way beyond my level of programming on linux .. I was just applying logic without truly understanding the issue you have. If you ever do get to the bottom of it i would love know myself now, curiosity peaked and all that :)

TpwUK

Thank you.  That page precisely answers my questions.  Somehow I never came across that page before.

---

### Post by TpwUK on 2011-02-12
Cool .... Glad to have been of some help, good luck with the rest of your project :popcorn:

---

