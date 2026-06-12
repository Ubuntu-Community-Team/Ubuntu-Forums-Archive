---
title: "Algorithm problem: making a GUi frontend and backend interact"
date: 2010-12-12
forum: Programming Talk
---

### Post by jfreak_ on 2010-12-12
I am writing a GUI in Gtk+ for a CLI program I had made in C. What I am doing now is having a separate list of code for the GUI and another for the backend. At a certain point in the backend, I want a dialog box to appear and when the user has accepted it, I want the program to continue from the same point it had left.
Is my way of thinking correct? If it is right, how do I call the function which makes the dialog box, from the backend? Till now, I have been calling such functions from within the frontend listing like this:
```

g_signal_connect(button , "clicked",   G_CALLBACK(display_card_blank), label);

``` 

But obviously I cannot pass control to display_card_blank in this fashion from the backend, since the widgets and windows are local to the GUI code. Any suggestions?

Feel free to criticize me, this is my first time doing somewhat complex code and I would gladly accept suggestions now before it becomes too late to re-write the entire thing.

---

### Post by dwhitney67 on 2010-12-12
Have the back-end app send a message to the front-end app.  You could use a signal, a message queue, shared memory, a pipe, or even a socket as the "glue" that binds the two applications together.

Btw, what are you currently using for the front-end app to communicate with the back-end app?

---

### Post by jfreak_ on 2010-12-13
OK so I have a piece of code that does what I needed, but there is a hitch. Consider this

```

.
.
.
a=1;
open_dialog(); // this goes to open_dialog and opens a dialog, and when user presses ok, increments 'a' by 1
a++;
printf("%d",a);
.
.
.

```

this gives output as 2, and not 3 as I expected, since by the time user presses ok, the control has already run along having printed 'a' as 2
What to do?

---

### Post by dwhitney67 on 2010-12-13
What is open_dialog()?  Have you set it up to open the dialog as modal?  You indicate that it is incrementing 'a'; how?  Is 'a' a global variable?

From looking at the code snip you provided, I would have expected 'a' to be 2.

---

### Post by Simian Man on 2010-12-13
The idea of having a GUI and textual program interact this way is horrible from a design perspective.  Just because some Linux programs do it, eg. gdb and ddd, should be no reason to write new programs that work this way.

What you should really do is put all of the code you have minus the interface into a library and then write two interfaces: a GUI one and a CLI one.  Then the interfaces just call the functions from your library and present the information in an appropriate way.

---

### Post by dwhitney67 on 2010-12-13
> **Simian Man said:**
> 
What you should really do is put all of the code you have minus the interface into a library and then write two interfaces: a GUI one and a CLI one.  Then the interfaces just call the functions from your library and present the information in an appropriate way.

Having a library is not necessary, nor would it add any benefit for a single application.  However you are correct that putting together a better design would be appropriate.

As for the printf() in the OP's code, I'm sure that is merely there for diagnostic purposes.

The OP should attach a callback routine to his OK button that performs the desired task (incrementing a value?), and if necessary return a status.  Whether the dialog should be invoked as modal or not depends on the application being developed.

---

### Post by Simian Man on 2010-12-13
> **dwhitney67 said:**
> Having a library is not necessary, nor would it add any benefit for a single application.  However you are correct that putting together a better design would be appropriate.

Sorry, I didn't mean actually implement it as a library - and certainly not as a shared object.  I just mean that the code should be logically separated into a "backend" that does the work and then the two interfaces.  Not as two processes that communicate somehow.

---

### Post by dwhitney67 on 2010-12-13
> **Simian Man said:**
> Sorry, I didn't mean actually implement it as a library - and certainly not as a shared object.  I just mean that the code should be logically separated into a "backend" that does the work and then the two interfaces.  Not as two processes that communicate somehow.

The industry-used term is MVC (Model-Viewer-Controller).  There are many ways to design to this paradigm, and each probably is dictated by what the application needs to perform.

For example, a GUI that I developed (at work) presents a main application shell to the user, which primary purpose is to display event messages from other applications which are running across the network.  The GUI contains several buttons, and pull-down menu selection choices.  Some of these open other dialog windows.

My main shell (dialog) contains the other dialogs.  When a button (or appropriate menu item) is selected, a callback routine merely pop ups the appropriate dialog.  Other callbacks are used to adjust the state of the overall GUI.

For more complex GUIs, say one that is used to control a remote system, separation of the GUI and the back-end that actually manipulates the remote system is a design must.  How the GUI and the back-end communicate with each other can vary from one project to the next.  It would not be wise to assume that the GUI and the back-end app run on the same machine, although there's nothing wrong with this.  But one should consider whether multiple GUIs will be used to manage a single controller.

Btw, for the benefit of the OP, in as far as MVC is concerned, the Model is where the data (state) is stored; the Controller manages the Model, and handles requests from the Viewer, and more importantly manages the external devices.  The Viewer sends requests to the Controller, that either asks for the current state of the system (e.g. current temperature of a melting pot), or to request that the system state be changed (e.g. shut off heating system).

A novice in the art of putting together a GUI sometimes makes the mistake of merging all of the MVC features into a big whopping mess of code.  Try to avoid that!

---

### Post by jfreak_ on 2010-12-13
@Simian Man and dwhitney67 
What i have done is i wrote a pure CLI program first. I am now writing a separate GUI listing with the CLI program in #include"abc.h"  . From the GUI listing, I am calling the appropriate function which is in the CLI program. However, I now need the user to enter a value and then manipulate it (to replace the scanf() in the CLI code). What I thought is that instead of calling a function from the GUI to CLI, I call a function from the CLI side which creates a dialog box in the GUI code . So now as i described, I expected the program to wait till the user entered a value. But it is not doing so, the dialog_box function runs in a loop waiting for the user to respond while the CLI side goes on manipulating the non-entered value.
The code that I gave was merely a example.

What exactly does a modal dialog box do?

I would be grateful if you could point to a tutorial telling how to integrate a GUI and CLI. And yes, the code is already getting dirty and unreadable, and I have hardly set out.

---

### Post by dwhitney67 on 2010-12-13
> **jfreak_ said:**
> 
I would be grateful if you could point to a tutorial telling how to integrate a GUI and CLI. And yes, the code is already getting dirty and unreadable, and I have hardly set out.

With a good design, you would not have to merge a CLI app and a GUI app.  You back-end app should support one, or more, interfaces.  The interface should not be embedded in app itself; in fact, the interface should be separated from the app.

For example, say in your code, you have a function that requires an acknowledgment from the user:
```

extern int displayDialog(enum DialogType type, const char* prompt);

void someFunction()
{
   int response = displayDialog(ACK, "Do you want to continue?");

   if (response == 1)
   {
      // do something.
   }
}

```

Now, as for what is implemented in displayDialog(), that is up to you.  You could potentially have two different versions: one that uses CLI that uses printf() and scanf(), or another that pops up a GUI dialog.  In either case, the application should not care; all it wants is a response so that it knows what to do next.

Does this make sense now?

> **jfreak_ said:**
> 
What exactly does a modal dialog box do?

A modal dialog prevents the user from interacting with the rest of the GUI until they have dismissed the dialog.


P.S.  Developing GUIs in C can be a mess; may I suggest you consider C++.

---

