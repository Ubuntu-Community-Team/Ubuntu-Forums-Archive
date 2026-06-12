---
title: "Writing GTk/Gnome Applications"
date: 2009-02-10
forum: Programming Talk
---

### Post by XanTrax on 2009-02-10
Hi everyone,

I have been itching to get into writing Linux applications that have a user interface.  I have found some information but sadly, it only seems to be a tutorial in using Java to write a GTK/Gnome app.

I am wondering, does anyone have any information on writing a simple Gtk or Gnome application user interface that can be used in KDE, Gnome, Fluxbox, etc?

I have a few ideas for programs, mostly based around shell scripts, but I would like to provide users an easier way of utilizing the applications.  I would like to do this through writing an interface using the gnome desktop environment.

EDIT: I have also found this: [http://www.codeproject.com/KB/cross-platform/gtksharpguide.aspx](http://www.codeproject.com/KB/cross-platform/gtksharpguide.aspx)  - it looks as if what I need, but, I would like to hear back from other programmers about what they use to write their UI's

---

### Post by nvteighen on 2009-02-10
GTK+'s native language is C.

There's the GTK+ official tutorial: [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

But, it's also really recommended to get the documentation. You can download it from the repos (or look it at [http://library.gnome.org/devel/gtk/stable/](http://library.gnome.org/devel/gtk/stable/)), together with the nice documentation called DevHelper

```

sudo apt-get install libgtk2.0-doc devhelper

```

Start Devhelper from Applications->Programming.

---

### Post by kknd on 2009-02-10
I develop UIs to use in both GNU / Linux and Windows. I'm using GTK+ (2.14.x) with Lua. Besides some quirks in Windows that needed some workarounds (most of then caused by the differences of the window manager of Windows and any that runs on Linux), it's very easy to keep the application multi-platform.

Here's the best tutorial (in my opinion) of GTK+ on the web: [http://zetcode.com/tutorials/gtktutorial/](http://zetcode.com/tutorials/gtktutorial/)

---

### Post by rich1939 on 2009-02-10
> **kknd said:**
> I develop UIs to use in both GNU / Linux and Windows. I'm using GTK+ (2.14.x) with Lua. Besides some quirks in Windows that needed some workarounds (most of then caused by the differences of the window manager of Windows and any that runs on Linux), it's very easy to keep the application multi-platform.

Here's the best tutorial (in my opinion) of GTK+ on the web: [http://zetcode.com/tutorials/gtktutorial/](http://zetcode.com/tutorials/gtktutorial/)

I have had good luck using CODE::BLOCKS for its editor, compiler-interface, linker-interface, and debugger-interface. As for graphic design of user interfaces, I use GLADE, in concert with CODE::BLOCKS, which runs a pre-compilation routine to convert the Glade XML file to GBuilder format, for use with GTK+.

If you need help in setting up CODE::BLOCKS or Glade, let me know and I'll try to help. Both of these are in the repository.

I had initially tried Anjuta, and it didn't agree with me. CODE::BLOCKS is much nicer, IMO.

---

### Post by XanTrax on 2009-02-10
> **nvteighen said:**
> GTK+'s native language is C.

There's the GTK+ official tutorial: [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

But, it's also really recommended to get the documentation. You can download it from the repos (or look it at [http://library.gnome.org/devel/gtk/stable/](http://library.gnome.org/devel/gtk/stable/)), together with the nice documentation called DevHelper

```

sudo apt-get install libgtk2.0-doc devhelper

```

Start Devhelper from Applications->Programming.


I have found that GTK+'s native language is C.  I am pretty familiar with C but recently had some classes at my Uni over the summer for C#.  With that, I have begun looking into GTK# since it can use C# and seems as easily portable to Vista machines as it does look very portable amongst Ubuntu distributions, which is my primary OS at this time.
 


> **kknd said:**
> I develop UIs to use in both GNU / Linux and Windows. I'm using GTK+ (2.14.x) with Lua. Besides some quirks in Windows that needed some workarounds (most of then caused by the differences of the window manager of Windows and any that runs on Linux), it's very easy to keep the application multi-platform.

Here's the best tutorial (in my opinion) of GTK+ on the web: [http://zetcode.com/tutorials/gtktutorial/](http://zetcode.com/tutorials/gtktutorial/)

I kind of want to stay away from Lua as well as stuff like Mono Basic to write these applications.  I don't know why, but those types of languages I never really got along with.  GTK# is as easily portable with using C# as it was for you with GTK+ and Lua?



> **rich1939 said:**
> I have had good luck using CODE::BLOCKS for its editor, compiler-interface, linker-interface, and debugger-interface. As for graphic design of user interfaces, I use GLADE, in concert with CODE::BLOCKS, which runs a pre-compilation routine to convert the Glade XML file to GBuilder format, for use with GTK+.

If you need help in setting up CODE::BLOCKS or Glade, let me know and I'll try to help. Both of these are in the repository.

I had initially tried Anjuta, and it didn't agree with me. CODE::BLOCKS is much nicer, IMO.

I use CODE::BLOCKS for some C/C++ apps primarily.  I decided to not use CODE::BLOCKS because it just seemed like it already did too much and not in the way I wanted it.  I think I remember selecting a new clean project and to just include libs and such and it still wound up setting up an entire 'skeleton' for me rather than just simple things I needed.  I dont use Anjuta cuz well...it just didnt feel comfortable to me.  I decided to compile these applications with mcs at the command line.  I am assuming doing it this way will keep the portability amongst Linux distros?

My primary goal in this is to give some of my shell scripts a UI to interface with so that they dont have to be run from shell.  So a user can use some of my shell scripts without having to do it via command line.  For example, I have a script for killing compiz before game launch, replacing it with metacity, and then enabling compiz again afterwards.  This, of course, takes arguments.  I want to write a UI for this so that the user can browse to the executable and the application decides whether or not it is an application that requires wine, then stores it for the user in another column (flat file database anyone?) for the user to select it for future use.

---

### Post by cb951303 on 2009-02-10
You can also use Glade which is a GUI designer for GTK. As of version 3 glade generates programming language agnostic xml files (it was generating C code in previous versions)
You can then use those XML files with the help of libglade. The downside is your program will depend on libglade, the upside is, your job will be a lot easier/faster.

Here is a tutorial for you
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by XanTrax on 2009-02-10
> **cb951303 said:**
> You can also use Glade which is a GUI designer for GTK. As of version 3 glade generates programming language agnostic xml files (it was generating C code in previous versions)
You can then use those XML files with the help of libglade. The downside is your program will depend on libglade, the upside is, your job will be a lot easier/faster.

Here is a tutorial for you
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

Thanks.  I'll have a look into it.

Glade and GTK together remind me of XAML and the new .NET framework :p.

---

### Post by directhex on 2009-02-10
Actually, glade-2 could also write XML files (and GTK# can use them). Though for C# apps, the preferred method is the integrated GUI designer in Monodevelop

---

### Post by XanTrax on 2009-02-10
> **directhex said:**
> Actually, glade-2 could also write XML files (and GTK# can use them). Though for C# apps, the preferred method is the integrated GUI designer in Monodevelop

Interesting.  I don't know anything about the integrated GUI designed in monodevelop.  Is it along the same lines as the GUI developer for Visual Basic on Windows?

---

### Post by directhex on 2009-02-11
> **XanTrax said:**
> Interesting.  I don't know anything about the integrated GUI designed in monodevelop.  Is it along the same lines as the GUI developer for Visual Basic on Windows?

Yes

Though GTK+ is a container-based layout toolkit (rather than pixel-based for WinForms), so there's a lot of placing HBox, VBox and Tables to control look & feel. Kinda like HTML <TABLE> abuse.

---

### Post by cb951303 on 2009-02-11
> **directhex said:**
> Yes

Though GTK+ is a container-based layout toolkit (rather than pixel-based for WinForms), so there's a lot of placing HBox, VBox and Tables to control look & feel. Kinda like HTML <TABLE> abuse.

I think thats the advantage of GTK. pixel-based toolkits are PITA to work with. Also you can always make pixel-based GTK applications with a container (I really don't remember the name now :))

@XanTrax [http://monodevelop.com/Image:Stetic-in-monodevelop.png](http://monodevelop.com/Image:Stetic-in-monodevelop.png)

---

### Post by directhex on 2009-02-11
> **cb951303 said:**
> I think thats the advantage of GTK. pixel-based toolkits are PITA to work with. Also you can always make pixel-based GTK applications with a container (I really don't remember the name now :))

@XanTrax [http://monodevelop.com/Image:Stetic-in-monodevelop.png](http://monodevelop.com/Image:Stetic-in-monodevelop.png)

Spot on, of course. Pixel based is essentially impossible to internationalize or use with high-visibility layouts (i.e. big fonts)

---

### Post by XanTrax on 2009-02-11
> **cb951303 said:**
> I think thats the advantage of GTK. pixel-based toolkits are PITA to work with. Also you can always make pixel-based GTK applications with a container (I really don't remember the name now :))

@XanTrax [http://monodevelop.com/Image:Stetic-in-monodevelop.png](http://monodevelop.com/Image:Stetic-in-monodevelop.png)

The monodevelop looks to be exactly what I want.  Though I like to do most of the programming, there is no need to reinvent the wheel and make my life harder with something like this.


Thanks for the resources guys.  Expect to see some cool things coming ;) :p.

---

### Post by cl333r on 2009-02-11
Gtk has some nice features, built-in support for color and font choosing, but it needs a serious review, I hope version 3 comes out sooner. There are funny random names like calling a component with tabs a notebook whereas other frameworks ourdays have much more intuitive names like the JTabbedPane, I also found it funny that there's no Table like component ("table" in gtk is rather a layout manager), unless you use the thirdparty library. So it's good but misses some obvious things.

---

### Post by cb951303 on 2009-02-11
> **XanTrax said:**
> The monodevelop looks to be exactly what I want.  Though I like to do most of the programming, there is no need to reinvent the wheel and make my life harder with something like this.


Thanks for the resources guys.  Expect to see some cool things coming ;) :p.

latest stable version doesn't have a debugger. That pretty much makes it useless IMHO.

---

### Post by XanTrax on 2009-02-11
> **cb951303 said:**
> latest stable version doesn't have a debugger. That pretty much makes it useless IMHO.

Im not too concerned with a debugger though because my stuff is pretty straight forward.  Does Monodevelop come with auto-fill of code and a compiler at least?

When I say auto-fill I mean like Visual Studio has Intellisense that can see what you're typing and drop down a box of suggestions.  Then, when you are using one, it shows you what arguments it takes.

---

### Post by cb951303 on 2009-02-11
> **XanTrax said:**
> Im not too concerned with a debugger though because my stuff is pretty straight forward.  Does Monodevelop come with auto-fill of code and a compiler at least?

When I say auto-fill I mean like Visual Studio has Intellisense that can see what you're typing and drop down a box of suggestions.  Then, when you are using one, it shows you what arguments it takes.

I believe it does

---

### Post by rich1939 on 2009-02-11
> **cb951303 said:**
> You can also use Glade which is a GUI designer for GTK. As of version 3 glade generates programming language agnostic xml files (it was generating C code in previous versions)
You can then use those XML files with the help of libglade. The downside is your program will depend on libglade, the upside is, your job will be a lot easier/faster.

Here is a tutorial for you
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

I understand that the use of **libglade** is deprecated, in favor of converting the glade xml file to GBuilder format. If using CODE::BLOCKS, the conversion can be accomplished automatically by placing the conversion call as a pre-compile step in the building process.

Then, instantiation of GUI elements can be as easy as the following:

```

GtkBuilder *builder;
GtkWidget *window;

builder = gtk_builder_new();
gtk_builder_add_from_file(builder, "*your_project.xml*", NULL);

window = GTK_WIDGET(gtk_builder_get_object (builder, "window"));

```

Any of the other interface elements in the window (or any window or dialog that was defined within Glade can be similarly accessed using the ```
gtk_builder_get_object
``` function, for example, to access their values or contents.

My current application is built in C, using Glade as the interface designer, and has multiple top-level windows instantiated in just this way.

---

### Post by directhex on 2009-02-11
> **rich1939 said:**
> I understand that the use of **libglade** is deprecated, in favor of converting the glade xml file to GBuilder format. If using CODE::BLOCKS, the conversion can be accomplished automatically by placing the conversion call as a pre-compile step in the building process.

Then, instantiation of GUI elements can be as easy as the following:

```

GtkBuilder *builder;
GtkWidget *window;

builder = gtk_builder_new();
gtk_builder_add_from_file(builder, "*your_project.xml*", NULL);

window = GTK_WIDGET(gtk_builder_get_object (builder, "window"));

```

Any of the other interface elements in the window (or any window or dialog that was defined within Glade can be similarly accessed using the ```
gtk_builder_get_object
``` function, for example, to access their values or contents.

My current application is built in C, using Glade as the interface designer, and has multiple top-level windows instantiated in just this way.

Looks a lot like how I was using Glade# a couple of years ago (before Monodevelop had a GUI designer).

```
using System;
using Gtk;
using Glade;
public class GladeApp
{
        public static void Main (string[] args)
        {
                new GladeApp (args);
        }
 
        public GladeApp (string[] args) 
        {
                Application.Init();
 
                Glade.XML gxml = new Glade.XML (null, "gui.glade", "window1", null);
                gxml.Autoconnect (this);
                Application.Run();
        }

       // Using [Widget] gives access to the named GTK object from Glade.
       // That's all that's needed.
       [Widget]
       Button button1;
}
```

---

