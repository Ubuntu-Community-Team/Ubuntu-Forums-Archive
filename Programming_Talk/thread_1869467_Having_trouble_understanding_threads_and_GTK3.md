---
title: "Having trouble understanding threads and GTK3"
date: 2011-10-25
forum: Programming Talk
---

### Post by Liiiim on 2011-10-25
I'm trying to write a simple application - all it will consist of is a GUI with one button and some labels.  You press the button, some code starts running in the background and the labels are updated every once in a while.

How I thought this should work is like this:  Pressing the button calls a handler function, which creates a new thread with 'g_thread_create'.  But then I'm not sure how that new thread should update the labels.  I read that there should only be one thread which does anything with the GUI, so I thought somehow I should have the original thread watch a mutex and update the labels once it saw the mutex change value.  Does that makes sense?  Or am I mistaken in thinking that only one thread interact with the GUI?  If I am, I think it would make the most sense to just have the new thread emit a signal when the labels should be updated.

Any advice would be much appreciated :)

---

### Post by cgroza on 2011-10-25
I don't know about GTK, but in wxWidgets the worker thread posts events to the widget that manages the GUI. The event system automatically calls the handlers in the next loop iteration.

---

### Post by gsmanners on 2011-10-25
I don't know, but I'd read the [Threads chapter]("http://developer.gnome.org/gdk/2.24/gdk-Threads.html#gdk-Threads.description") in the GDK manual before doing that kind of thing in gtk.

---

### Post by t1497f35 on 2011-10-25
> **Liiiim said:**
>  I should have the original thread watch a mutex and update the labels once it saw the mutex change value.
Yes, only one thread should access gtk (and probably some/all glib functions).
You don't need a mutex, because gdk_threads_enter()/gdk_threads_leave() is the mutex which blocks the main Gtk/glib thread from updating the GUI, hence you can just do this from your thread:

[PHP]
void myThread() {
gdk_threads_enter();
//Update labels, entries, etc from this thread.
//The main Gtk thread won't update any GUI
gdk_threads_leave();
//now the main thread can update the GUI
}
[/PHP]I use this approach, but there's another one - using dispatchers which I don't like cause the source code starts looking like spaghetti - though some people like it and say it makes the source code more readable or so.

Here's a tiny Gtkmm3 app demonstrating what I said. You have to have Oneiric to compile & run it.
To compile install this: sudo apt-get install libgtkmm-3.0-dev

---

### Post by t1497f35 on 2011-10-25
Also remember that the code from signal handlers always executes in the main thread, more info here:
[http://tadeboro.blogspot.com/2009/06/multi-threaded-gtk-applications.html](http://tadeboro.blogspot.com/2009/06/multi-threaded-gtk-applications.html)

---

### Post by Liiiim on 2011-10-25
Oops, I thought that page was just a reference page.  Reading now...  

And thanks very much for that t1497f35, I'll take a look at that code.

Since the signal handlers all execute in the main GTK thread, would something like this make sense -

```
void myThread (){
    gtk_threads_enter ();
    g_emit_signal (...);
    gdk_threads_leave ();
}
```

And the signal emitted would just be handled by a function that could update the labels from the main GTK thread.  Would that work?

Also, in the Threads chapter of the GDK manual gsmanners posted there's an example which uses pthreads to create a thread.  Why wouldn't the author have just used Glib's 'g_thread_create' to do that?

---

### Post by t1497f35 on 2011-10-25
Emitting a signal would work, but why emit a signal which updates the GUI when you can update the GUI right there, without having to emit a signal. Cut the middle-man!
Like this:

//inside my thread
gdk_threads_enter();
myLabel.set_label("new label");
gdk_threads_leave();
...

In my example source code I'm also using pthreads for 2 reasons: 1) I read a book on pthreads 2) The app isn't meant to run on window$.

---

### Post by Liiiim on 2011-10-25
It works now :D  Thank you so much!

I just have one more question - how would you suggest printing debug messages with 'g_print' from non-GTK threads?  Do you just have to have dozens of gdk_thread_enter/leave's, or is there a more elegant solution?

---

### Post by t1497f35 on 2011-10-25
I don't use g_print, I just use std::cout or printf, **without** enclosing them with gdk_threads_enter/leave, I don't know if I'm doing right but I never had any issues with that.

---

### Post by Liiiim on 2011-10-25
Oh!  I should have realized that would work - I was thinking printf doesn't work in GTK apps but of course it just won't work inside the GTK thread.

You've been a fantastic help, thanks so much :)

---

### Post by t1497f35 on 2011-10-25
I just googled around and it looks like printf is actually thread safe, thus it should work fine from any thread any time (without the need to enclose it into gdk_threads_enter/leave), including inside the main GTK thread.

[http://stackoverflow.com/questions/467938/stdout-thread-safe-in-c-on-linux](http://stackoverflow.com/questions/467938/stdout-thread-safe-in-c-on-linux)

---

### Post by Liiiim on 2011-10-26
Oops, you're right.  Calling fflush (stdout) after a printf gets it to show up.

Sorry for bumping a 'Solved' thread, but I've got a new question that I thought should just go here...

In the GDK [Threads](http://developer.gnome.org/gdk/2.24/gdk-Threads.html#gdk-Threads.description) chapter, it says that with the Win32 backend, "GDK calls should not be attempted from multiple threads at all."  I'm a little confused about what constitutes a GDK call.  Is that any function that starts with a 'g' and requires glib.h or gtk.h?  Or is it just the functions starting with 'gdk'?

---

### Post by gsmanners on 2011-10-27
I think any function defined in the GDK reference is a GDK call.

---

### Post by crdlb on 2011-10-27
> **Liiiim said:**
> 
In the GDK [Threads](http://developer.gnome.org/gdk/2.24/gdk-Threads.html#gdk-Threads.description) chapter, it says that with the Win32 backend, "GDK calls should not be attempted from multiple threads at all."  I'm a little confused about what constitutes a GDK call.  Is that any function that starts with a 'g' and requires glib.h or gtk.h?  Or is it just the functions starting with 'gdk'?

It includes anything at or above the GDK layer, basically anything involving the UI. Your other threads can use GLib (assuming you have called g_thread_init), but they must not interact with any GDK data structures.

You should use g_idle_add to perform all changes to the UI in the main thread. There is also gdk_threads_add_idle, a wrapper that acquires the GDK lock, but my understanding is that it is unnecessary if you never touch GDK outside of the main thread (including any libraries or plugins).

---

### Post by Liiiim on 2011-10-27
Ok thanks, that's how I thought it would work.

As I understand it though, g_idle_add will hook a function to be called whenever the main thread is idle, meaning that function will be called repeatedly.  I just want to update the UI (by calling that function) a few specific times, so could I just use g_main_context_invoke to do that?

---

### Post by crdlb on 2011-10-27
> **Liiiim said:**
> 
As I understand it though, g_idle_add will hook a function to be called whenever the main thread is idle, meaning that function will be called repeatedly.  I just want to update the UI (by calling that function) a few specific times, so could I just use g_main_context_invoke to do that?

Return FALSE from the g_idle_add callback and it will not be called again.

---

### Post by Liiiim on 2011-10-27
What's the difference between calling g_idle_add and returning FALSE from its call back and just using g_main_context_invoke?

---

### Post by crdlb on 2011-10-27
> **Liiiim said:**
> What's the difference between calling g_idle_add and returning FALSE from its call back and just using g_main_context_invoke?

g_main_context_invoke is a recent addition (GLib 2.28) that appears to be meant for use with multiple mainloops on different threads. There is no reason not to use g_idle_add when dealing with the default MainContext.

---

