---
title: "problem with Gtk+ GUI"
date: 2010-06-24
forum: Programming Talk
---

### Post by miak on 2010-06-24
Hi,

I'm writing a GUI with Gtk+ in C, and I want to update plots on the GUI every 30 seconds without any user input.
If I was using python I could've just used multi threading and have one thread call a function in the other. This seems kind of impossible to me since C is not object oriented at all. 
Any ideas how to update a GUI every 30 seconds??

Also is it possible to trigger the update from some other program? say one written in python.

Thanks,
miak

---

### Post by SledgeHammer_999 on 2010-06-25
Use a "timeout" callback that gets fired every 30 seconds. See the tutorial link here-->[http://library.gnome.org/devel/gtk-tutorial/stable/c1759.html#SEC-TIMEOUTS](http://library.gnome.org/devel/gtk-tutorial/stable/c1759.html#SEC-TIMEOUTS)

---

### Post by NonMSman on 2010-06-25
In C you can execute tasks at the same time using :  fork();


main()  {
***string sIdentifier;
***int*** iStackVariable = 20;
***pid_t pID = fork();
***if (pID == 0)****{*********** // child
*****                                *// Code only executed by child process
******sIdentifier = "Child Process: ";
******globalVariable++;
******iStackVariable++;
****} else if (pID < 0)***{*******      * // failed to fork
********cerr << "Failed to fork" << endl;
********exit(1);
*******                                         *// Throw exception
****}*else**{******************************** // parent
******// Code only executed by parent process
******sIdentifier = "Parent Process:";
   }

):P

---

### Post by NonMSman on 2010-06-25
Sorry about * in code.  I did not place any there.  I copied the code from a google search on an example and this forum placed them in there.

anyway...  That's how you can do two things at once in C....

Hope it helps...:guitar:

---

### Post by chay on 2010-06-25
In C you also have threads since 1995: check pthread_create, pthread_join, pthread_exit & friends in the man pages.

In python, the threads are "crippled" (check Python GIL in google, the global interpreter lock, python doesn't have real threads).

HTH

---

### Post by tbastian on 2010-06-25
In my experience gtk doesn't like threads by default. Your best bet is to either use the timeout function, or I think there is some sort of lock you can acquire similar to mutexts.

There is a tutorial [here]("http://www.yolinux.com/TUTORIALS/GTK+ProgrammingTips.html"). This is the gist of it:

```

if( !g_thread_supported() )
{
    g_thread_init(NULL);
    gdk_threads_init();                   // Called to initialize internal mutex "gdk_threads_mutex".
    printf("g_thread supported\n");
}

```

then:

```

    gdk_threads_enter();
    // make gtk call
    gdk_flush();
    gdk_threads_leave();

```

they leave you with this warning:

[Potential Pitfall]: You will create a deadlock condition if you try to update a widget before it has been realized.

---

### Post by miak on 2010-06-25
thanks SledgeHammer_999 I think timeouts is exactly what I wanted.
for NonMSman, thanks for suggestion but I don't want to use forks, since they are slow and i don't really know how they will work with gtk.

One more small question, does anyone know how to empty a widget in gtk, i.e. remove all its children. 
There is a function that returns a list(get_children()), but i don't know how to iterate over a list in c.

---

### Post by miak on 2010-06-25
Actually if you answer this one it will be even better 
How can I pass two arguments to a function using one pointer?
So I want to pass two widgets to the timeout function and timeout function should be defined in this way :
```
gint function(gpointer data)
```

---

### Post by Milliways on 2010-06-25
> **miak said:**
> Actually if you answer this one it will be even better 
How can I pass two arguments to a function using one pointer?
So I want to pass two widgets to the timeout function and timeout function should be defined in this way :
```
gint function(gpointer data)
```

Create a structure with 2 pointers, and pass a pointer to an instance of the structure.

---

