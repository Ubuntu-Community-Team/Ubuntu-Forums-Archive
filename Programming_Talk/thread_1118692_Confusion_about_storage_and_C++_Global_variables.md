---
title: "Confusion about storage and C++ Global variables"
date: 2009-04-07
forum: Programming Talk
---

### Post by MaxVK on 2009-04-07
Note: Please be gentle - very new C++ developer!

I am just starting out with C++, having been through a variety of languages both on Windows and now on Linux. I am using Code::Blocks and wxWidgets.

I have searched for information about Global variables and found that they are frowned upon. Fair enough, Ill learn that lesson, but I am still left with a consideration:

When using other languages for a basic learning project such as a small scale text editor, when I wanted to keep a track of the current filename etc, I would place it in a global variable. This has always worked for me.

In C++ this is not correct, so my question is really - Where/How do I store this filename so that it can be pulled from the ether when it is required?

regards

Max

---

### Post by dwhitney67 on 2009-04-07
Within a class object.

This class object could be called "File".  It could have attributes like filename, file attributes, file size, current edit position, etc.

In turn, another class object, say Editor, would contain one or more File objects.  It is possible to edit more than one file at a time, right?

Anyhow, global variables suck.

---

### Post by Arndt on 2009-04-07
> **dwhitney67 said:**
> Within a class object.

This class object could be called "File".  It could have attributes like filename, file attributes, file size, current edit position, etc.

In turn, another class object, say Editor, would contain one or more File objects.  It is possible to edit more than one file at a time, right?

Anyhow, global variables suck.

I'd like to add that global variables become a problem in any language, if allowed to proliferate and misused for communicating between functions/modules. Interfaces become unclean, which makes understanding and developing them harder. So the reasons for avoiding them are pretty much the same in C++ as elsewhere.

There are probably good exposés on this issue on the web. Wikipedia has this to say: [http://en.wikipedia.org/wiki/Global_variable](http://en.wikipedia.org/wiki/Global_variable).

---

### Post by gtr32 on 2009-04-07
> **MaxVK said:**
> Where/How do I store this filename so that it can be pulled from the ether when it is required?

Others have already answered that question, I just wanted to also add you want to protect that filename from direct writing. Instead of exposing it as public variable on the class, make it private (or protected in some cases). You should have the basic file functions of Open, Save, SaveAs and Close which would then handle changing that variable. 

_file->Open("\foo\foo.c"); // <- if successful, filename is set to \foo\foo.c

You would also need to write a function inside the class to fetch the filename:

string GetFileName() const ; // <- gets the filename

Look up data encapsulation for more info.

---

### Post by MaxVK on 2009-04-07
Thanks everyone, I'm familiar with such classes from using things like Python etc, but Iv always also used globals for things like this.

As dwhitney67 mentioned, yes I will of course be likely to open more than one file at a time (eventually), and in light of this a further question comes to mind:

Assuming that each time a file is opened the class is initialized to store the filename and perhaps other details about this particular file, what would be the best way to keep track of the individual instances of the class?

Again in other languages Id be inclined to use a global such as "CurrentFileID = x" but would this also be a candidate for a class?

regards

Max

---

### Post by gtr32 on 2009-04-07
Depends on your application but something like std::list perhaps. No globals, use it within the scope you need.

---

### Post by eye208 on 2009-04-07
> **MaxVK said:**
> Assuming that each time a file is opened the class is initialized to store the filename and perhaps other details about this particular file, what would be the best way to keep track of the individual instances of the class?
Attach them to the instances of the GUI element that is related to the file. For example, if your editor opens each file in a separate window, the file data should be attached to the window object. If your editor uses multiple tabs in a single window, attach the file data to the tab instead.

In wxWidgets, each GUI element is a subclass of wxEvtHandler. You can attach user-defined data to a wxEvtHandler object using the SetClientData or SetClientObject methods.

Since wxApp is a subclass of wxEvtHandler too, you can attach global application data (such as user preferences) to your application object instead of holding them in a global variable.

The concept of attaching user-defined data to GUI elements is not unique to wxWidgets. GTK+ and other libraries offer similar services. As a result, you can get along without any global variables in your code.

---

### Post by MaxVK on 2009-04-08
Thanks for the help everyone - no doubt Ill be back with more trifling problems!

regards

Max

---

