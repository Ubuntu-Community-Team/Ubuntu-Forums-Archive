---
title: "C++/Gtkmm: Run code from separate file?"
date: 2011-01-10
forum: Programming Talk
---

### Post by fallenshadow on 2011-01-10
I really hate needing to ask about this but its causing me alot of problems at the moment. What I want to do is split up my code into separate files in order to make working with my project not such a nightmare.

In my mainwindow.cc here is what I want to do:

void MWindow::show_about_dialog()
{
   //Execute function in separate file (about.cc) containing my code I want to run.
} 

Note that I have done this with code already but that was with code that had a header file to accompany it. This code does not have a header file.

Any help or ideas on what to do would be great!

---

### Post by dwhitney67 on 2011-01-10
And functions that you implement should have a function prototype declared somewhere (and typically this is within a .h file).  The reason for this is to ensure that you call the function using the appropriate parameters, if any.

Of course, you could circumvent this widely used practice by simply declaring the function prototype in the module where it is called using the "extern" keyword, but this IMO, is lame.  Here's an example:

Module1.cpp:
```

#include <string>  // since you haven't a header file for the function prototype below, you must do this yourself.
extern void externalFunction(const int val, const std::string& str);


MyClass::localFunction()
{
   std::string hello("hello");

   externalFunction(4, hello);
}

```

Module2.cpp:
```

#include <string>

void externalFunction(const int val, const std::string& str)
{
   ...
}

```

To build program:
```

g++ Module1.cpp Module2.cpp -o myprog

```
To reiterate, the code shown above is lame and should be avoided unless you like to experience the wrath of your peers (and possibly the compiler if you screw something up).  The better practice is to define all of your functions within header file(s) that can be included within the module(s) where they will be called.

---

### Post by fallenshadow on 2011-01-10
Interesting... but I can't use this? or I guess you are just saying I shouldn't really use this. :D

The problem I have is that the code doesn't need anything as far as I can see. However I will have a go at doing some kind of header for it and see how far I get.

I will report back soon. :)

---

### Post by fallenshadow on 2011-01-10
Ok I made a header file for my about.cc file.

Here is my current error message:

> cannot call member function ‘virtual void aboutDialog::show_about_dialog()’ without object

Any ideas as to where the problem might be?

---

### Post by dwhitney67 on 2011-01-10
Learn, learn, learn... to develop small apps to practise new concepts before integrating them into a massive application.

As for your error, you need to instantiate a class object before you can call that particular class function.  The alternative is to declare the function as static, but this may not meet your needs either.

Earlier you did not provide sufficient reasons for creating a separate module.  Why do you feel you need this?  If anything, perhaps you can declare/define a helper function within your existing class.

---

### Post by fallenshadow on 2011-01-10
I want to do this because working with large files is a pain (1000k+ lines).

The problem is that as time goes on this file will get much too big for me or anyone else to handle.

I think this is reason enough to do it.

---

### Post by dwhitney67 on 2011-01-10
I work with files that often exceed 1500 lines, so I guess I'm used to it.

But you do what you want.  Why don't you consider splitting the implementation of a class into multiple modules.  It's not standard practice, but it can be done.  For example:

Foo.h
```

class Foo
{
public:
   ...

   void function1();
   void function2();

private:
   void helper1();
   void helper2();
};

```

Foo1.cpp:
```

#include "Foo.h"

void
Foo::function1()
{
   helper1();
}

void
Foo::function2()
{
   helper2();
}

```
Foo2.cpp:
```

#include "Foo.h"

void
Foo:helper1()
{
   ...
}

void
Foo::helper2()
{
   ...
}

```
Then you build your project the same as you would with any other multi-module project.

---

### Post by nvteighen on 2011-01-10
I think you need to know a couple of things about the compilation process first. Otherwise, you may not understand this fully.

What we usually call the "C++ compiler" is actually the combination of the preprocessor, the actual compiler, the assembler and the linker. First of all, each file is processed separately upto the assembler; the linker is the stage where everything is tied up into one single binary file.

**0. Preprocessor**
Roughly speaking, what this does is to execute the #whatever directives for each C++ source file. These prepare the source code for compilation in several ways, e.g. substituting stuff using macros, conditional compiling, and mostly *including header files*. This outputs a new preprocessed C++ source file.

(Note that when I state that files are created, depending on how you're executing g++, the "file" isn't created on the filesystem, but on memory. You can tell g++ to stop at each stage and output the result to an actual file, but this is usually done to avoid linking in some situations)

**1. Compiling**
After the code's been preprocessed, the compiler takes each C++ source file and transforms it into some platform-specific Assembly. 

But, for technical reasons I won't go further into, to do that the compiler has to know the signatures of the functions that are used in the specific source file you're compiling. It doesn't need to know where the function is declared nor what it does: just know the data types of the arguments it takes and the data type it returns. This is why you use header files as interfaces: these define the signatures of the functions used.

**2. Assembling**
Each source code file is translated now from Assembly to object code. Nothing interesting here, actually, save the several optimizations that compilers usually do at this stage.

**3. Linking**
Here is where the magic occurs. Each assembled object file at this stage is just a translation of your C++ code, but the references haven't been resolved yet. In other words, no check has been done in order to establish whether a function was actually defined or not, apart from declared. The linker is in charge of this because it's the only stage of all four that "sees" all files that are needed to create the executable. If a function is not found at the object files given to the linker, the linking stage will fail.

(I won't go into how shared libraries are compiled, but basically, the linking stage is "postponed").

**4. Very nice, but what does this have to do with multi-files projects?**
Well, it explains what dwhitney67 is telling you. The key points are two:

1) You need to get the (actual) compiler know about the functions' signature. The usual way is to use a header because you can use it in different files without repeating the signatures everywhere where needed.

2) You need to get the linker know about all the needed object files so it can resolve the names and know where to find everything. gcc/g++ does this by having you listing all files as arguments:

```

g++ -o mybin file1.c file2.c file3.c (etc.)

```

I hope this helps to clarify the overall picture.

---

### Post by nvteighen on 2011-01-10
I think you need to know a couple of things about the compilation process first. Otherwise, you may not understand this fully.

What we usually call the "C++ compiler" is actually the combination of the preprocessor, the actual compiler, the assembler and the linker. First of all, each file is processed separately upto the assembler; the linker is the stage where everything is tied up into one single binary file.

**0. Preprocessor**
Roughly speaking, what this does is to execute the #whatever directives for each C++ source file. These prepare the source code for compilation in several ways, e.g. substituting stuff using macros, conditional compiling, and mostly *including header files*. This outputs a new preprocessed C++ source file.

(Note that when I state that files are created, depending on how you're executing g++, the "file" isn't created on the filesystem, but on memory. You can tell g++ to stop at each stage and output the result to an actual file, but this is usually done to avoid linking in some situations)

**1. Compiling**
After the code's been preprocessed, the compiler takes each C++ source file and transforms it into some platform-specific Assembly. 

But, for technical reasons I won't go further into, to do that the compiler has to know the signatures of the functions that are used in the specific source file you're compiling. It doesn't need to know where the function is declared nor what it does: just know the data types of the arguments it takes and the data type it returns. This is why you use header files as interfaces: these define the signatures of the functions used.

**2. Assembling**
Each source code file is translated now from Assembly to object code. Nothing interesting here, actually, save the several optimizations that compilers usually do at this stage.

**3. Linking**
Here is where the magic occurs. Each assembled object file at this stage is just a translation of your C++ code, but the references haven't been resolved yet. In other words, no check has been done in order to establish whether a function was actually defined or not, apart from declared. The linker is in charge of this because it's the only stage of all four that "sees" all files that are needed to create the executable. If a function is not found at the object files given to the linker, the linking stage will fail.

(I won't go into how shared libraries are compiled, but basically, the linking stage is "postponed").

**4. Very nice, but what does this have to do with multi-files projects?**
Well, it explains what dwhitney67 is telling you. The key points are two:

1) You need to get the (actual) compiler know about the functions' signature. The usual way is to use a header because you can use it in different files without repeating the signatures everywhere where needed.

2) You need to get the linker know about all the needed object files so it can resolve the names and know where to find everything. gcc/g++ does this by having you listing all files as arguments:

```

g++ -o mybin file1.c file2.c file3.c (etc.)

```

I hope this helps to clarify the overall picture.

---

### Post by nvteighen on 2011-01-10
.

---

### Post by nvteighen on 2011-01-10
.

---

### Post by nvteighen on 2011-01-10
.

---

### Post by nvteighen on 2011-01-10
.

---

### Post by fallenshadow on 2011-01-10
Im not sure was it me just being crazy... now im not sure should I split up my code or is it less work to just leave it the way it is? :confused:

---

### Post by dwhitney67 on 2011-01-10
It is not unusual for GUI code to become a huge monstrosity.  There's all the code to create each individual widget, then the setup of the callback routines, and then the implementation of the callback routines.

If you have additional dialog boxes with your GUI, then each of these should be implemented in a separate module.  The top-level GUI should contain these; in other words, the top-level GUI instantiates them, and then pops them up via the appropriate callback routine.  The callback routine should never create a dialog box; they should already be created.

If you feel that your code has become unmanageable, then perhaps you should take a step back and perform a self peer review of the code to see if you made any bad assumptions.  You could also post here on the forum for others to peer review it too.

---

### Post by nvteighen on 2011-01-11
I'm truly sorry for the mess I created with my multiple post (and more with a long post like that). I've deleted all but the first one.

---

### Post by fallenshadow on 2011-01-11
Thanks for the info nvteighen and yeah I was gonna ask why did you post it 6 times! :D

Ok I think ive decided to continue splitting up my code. I have my Open and about dialog code inside the mainwindow.cc and I just didn't feel it was right to be doing that.

I feel its easier to develop that way because dialogs can be developed inside a function in the file with no hassle. However it would mean in the future if I continued this way my mainwindow.cc would become too big and it wouldn't make sense to keep opening a big file when all I want to change is a small part of it.

If I can successfully splitup my mainwindow.cc then it will be reduced to about 800 lines, which is perfectly fine. I reckon this will still increase to about 1000 lines after I do more work on the mainwindow but at least only mainwindow stuff will be inside my mainwindow.cc file. 

If I continued by shoving everything inside my mainwindow.cc I think it would go up to around 3000 lines after a while and for me thats far too much to handle.

---

### Post by dwhitney67 on 2011-01-11
> **fallenshadow said:**
> 
Ok I think ive decided to continue splitting up my code. I have my Open and about dialog code inside the mainwindow.cc and I just didn't feel it was right to be doing that.

I feel its easier to develop that way because dialogs can be developed inside a function in the file with no hassle...

No doubt!

Separate the implementation of the MainWindow from the AboutDialog.

To summarize in code:
```

class MainWindow : public Gtk::Window
{
public:
   MainWindow();

   ...

private:
   void aboutCallback();
   ...
   AboutDialog* myAboutDialog;
};

```
MainWindow.cc:
```

MainWindow::MainWindow()
   myAboutDialog(new AboutDialog(this))
{
   ...

   m_refActionGroup->add(Gtk::Action::create("HelpMenu", "Help"));
   m_refActionGroup->add(Gtk::Action::create("Help", Gtk::Stock::ABOUT), sigc::mem_fun(*this, &MainWindow::aboutCallback));

   ...
}

void
MainWindow::aboutCallback()
{
   myAboutDialog->popup();
}

```

In AboutDialog.h:
```

class AboutDialog : public Gtk::Dialog
{
public:
   AboutDialog(Gtk::Window* parent);

   void popup();

   ...
};

```
AboutDialog.cc:
```

AboutDialog::AboutDialog()
{
   ...
}

void
AboutDialog::popup()
{
   // display the dialog when this function is called.
}

```


P.S.  The AboutDialog may not need a reference to the parent window; sometimes dialogs do, sometimes they don't.

---

### Post by fallenshadow on 2011-01-11
Thanks for your help and advice dwhitney67! I got it mostly right but needed some essential fixes from a friend. Now my about dialog has been split from my mainwindow code and changes committed and uploaded to Launchpad! :) :cool:

Now hopefully I can manage to split my Open dialog code in the same way. Then actual progress can happen on my project.

---

### Post by Ravenshade on 2011-01-12
I know this has been solved but...

you could have just used a 'forward declaration' especially if it's just one or two files. 

[http://www.learncpp.com/cpp-tutorial/18-programs-with-multiple-files/](http://www.learncpp.com/cpp-tutorial/18-programs-with-multiple-files/)

---

### Post by dwhitney67 on 2011-01-12
> **Ravenshade said:**
> I know this has been solved but...

you could have just used a 'forward declaration' especially if it's just one or two files. 

[http://www.learncpp.com/cpp-tutorial/18-programs-with-multiple-files/](http://www.learncpp.com/cpp-tutorial/18-programs-with-multiple-files/)

Forward declarations have nothing to do with files; they are used to tell the compiler about data types, namely class/struct declarations.

If you think about it, there's nothing stopping a developer from declaring multiple classes within the same header file, and then implementing one or more .cpp files.

---

### Post by dwhitney67 on 2011-01-12
> **fallenshadow said:**
> Thanks for your help and advice dwhitney67! I got it mostly right but needed some essential fixes from a friend. Now my about dialog has been split from my mainwindow code and changes committed and uploaded to Launchpad! :) :cool:

Now hopefully I can manage to split my Open dialog code in the same way. Then actual progress can happen on my project.

Btw, it seems that the "preferred" way to create and display a dialog window is to create it and run it within the callback routine that is assigned to display it.  This is not a brilliant approach, but that's what the documentation shows.  Something like:

```

void aboutCallback()
{
   AboutDialog dialog;

   dialog.run();
}

```

And earlier I used Gtk Dialog as the base class in my example; for an AboutDialog, Gtk MessageDialog is probably more appropriate to use.


P.S.  If you, or anyone else knows of a way to "pop down" a Dialog window, please let me know.

---

