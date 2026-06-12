---
title: "Glade to C++?"
date: 2007-11-13
forum: Programming Talk
---

### Post by Blice on 2007-11-13
Sorry if this has been asked before, but how do I make my GUIs in C++ form instead of XML? I googled around, and saw somewhere that you can export it as C in the project options- But my Glade (3) doesn't have project options.


Thanks,

---

### Post by slavik on 2007-11-13
There is no code generation in Glade3, only XML.

---

### Post by Blice on 2007-11-13
...Oh. 

Should I get an earlier version, then?

---

### Post by slavik on 2007-11-13
Why?

The whole point is to separate the GUI logic from the backend logic.

---

### Post by Blice on 2007-11-13
I just wanted a program to make the GUI with a nice drag and drop interface for c++ applications. Is there better programs for that?

---

### Post by slavik on 2007-11-13
you can still change the GUI using code after it has been loaded from XML ...

---

### Post by j_g on 2007-11-13
Glade's ability to output C source code (to create the UI) was removed from version 3 of Glade. You're obviously reading an old tutorial about an earlier Glade version.

The output of Glade 2 was not an XML file. Rather, it was C source code that called a bunch of glib functions to create each widget/window/menu (ie, the UI). But this presented a problem using glade with other programming languages. For example, if one wanted to use Python, then Glade would need to be modified to output Python code that used glib functions to create the UI.

Rather than have Glade 3 output source code (in various languages) that actually builds up the UI, the Glade programmers instead decided to have Glade output a data file in some neutral format (ie, XML). This data file contains organized (ie, tagged) definitions of each window and its widgets/menu. Then, they created another add-on library called libglade. This library has a function called glade_xml_new. You pass glade_xml_new the name of your XML file, and also the "ID" of some window in that XML file. glade_xml_new reads your XML file, and builds up that window and its controls/menus, and presents it on screen. It also returns a handle (to a GladeXML struct) you use to call other libglade functions that can do things such as return a handle to some widget in that window (glade_xml_get_widget), etc.

For example, if my XML file is named "Myfile.glade" and the window that I want to create has an id of "MyWindow", I'd do:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <gtk/gtk.h>
#include <gdk/gdkx.h>
#include <glade/glade.h> // NOTE: Include this for libglade

GladeXML *xml;

// Create MyWindow
if (!(xml = glade_xml_new("Myfile.glade", "MyWindow", 0)))
   printf("MyWindow failed to load\n");
else
{
   GtkWidget *newWidget;

   // Get the widget with an id of "MyButton"
   newWidget = glade_xml_get_widget(xml, "MyButton");

   // Attach my on_click() function to its "clicked"" event
   g_signal_connect(G_OBJECT(newWidget), "clicked", G_CALLBACK(on_clicked), xml);
}
```

Note that if you give your executable to someone else, you must also supply your glade XML file. libglade obviously needs that XML file on the system whenever your exe runs.

Now to support new languages, Glade programmers simply make a "binding" that allows a language to use libglade's glade_xml_new and glade_xml_get_widget functions.

So, the solution to your problem is to ignore those old Glade tutorials. Run Synaptic and do a search for libglade. Download/install the development headers for libglade. Then do a google search for glade_xml_new to find some more modern tutorials/examples that show you how to use libglade.

P.S. Guys, I realize no one is getting paid to provide answers here, but if you're going to post a reply, please try to consider the question from the OP's point of view, and give a detailed enough answer that will give him the means/direction to solve his problem. It does no good to answer a question ambiguously, or so sketchy, that the OP ends up knowing no more after he reads your reply. That's just aggravating to the OP.

P.P.S. I really wish that people who provide tutorials on the net would either periodically update their tutorials, when new advancements happen that make the info in the tutorial "obsolete", to either mention that the info is not applicable to newer versions of some tools, or just remove the tutorial completely. It really is counterproductive to have lots and lots of dated info out there, that isn't readily apparent to the reader that the info is dated.

---

### Post by Blice on 2007-11-13
Thanks a lot j_g! 

Another concern of mine was with making a Windows version of said GUI- 

Would I need to completely redo the GUI? Or do I just make sure not to use KDE stuff? 
That was another reason for wanting to output in C, so I could try editing it to compile on Windows aswel.

I just now discovered KDevelop Design- Do you think this would be a better option for me?


Thanks again for the excellent reply.

---

### Post by j_g on 2007-11-13
To be honest, I'm not a fan of cross-platform development. When I write Windows software (and I do a lot of that), I prefer to use the most efficient, feature-rich (ie, supports as many of that operating system's unique features as possible) tools/libraries. I don't like writing, nor using, "lowest common denominator" software.

So when I write Windows software, I use the Win32 API (ie, CreateDialog(), which reads a Win32 "dialog template" embedded right inside of the exe. I create the dialog template with Microsoft's GUI builder in Visual C++. This really is the same technique that Glade/libglade uses, although the specific functions are named differently and take different args).

When I write Linux software, I use Glade/libglade.

Even if I'm porting the same app from Windows to Linux, I just find it better to use a really functional UI builder, such as Glade, to quickly redo the UI. Since libglade creates the UI for you, it's actually fairly trivial to recreate a UI on Linux with Glade/libglade. I mean, using CreateDialog on Win32, and libglade on Linux, is pretty much the same technique. If you separate the non-GUI logic in your app, from the GUI creation/management code, it's pretty trivial porting.

Why accept the compromises of other cross-platform libraries (many of which lack such easy GUI builders as Glade for Linux, or Microsoft's GUI builder with Microsoft Visual C++), when you can quickly recreate the UI optimized for your target platform?

There are other people who are into cross-platform UIs, so you could ask them about it. I do believe that Gtk is somewhat cross-platform. I think that there is even a version of Glade/libglade for Win32. So you can investigate that. I doubt it will produce results as good as creating the UI with Microsoft's GUI builder, and presenting it with CreateDialog.

But some people like to mention wxWidget (I believe it's called), which is a cross-platform UI library for both Windows and Linux. The only thing is that I believe it requires C++ (but maybe there are bindings for other languages), and I don't know as if it has a GUI builder like Glade.

Qt/Kde is just another version of a GUI for Linux. It's an alternative to Gtk/Gnome. Nothing in Gnome/Gtk/Glade has anything to do with Qt/KDE/KDevelop/Design. So whatever info you read about Qt/KDE/KDevelop/Design, has no bearing upon your Gnome/Gtk/Glade/libglade development, or vice versa.

Qt/KDE has its own libraries and GUI builder, and like Gtk, I think there's a Windows version (although I believe you have to pay to use Qt if you are going to sell your software). I don't use Qt because it doesn't support writing your app in C. You have to use C++.

The information I'm supplying you about cross-platform UIs is sketchy (and perhaps not uptodate) because I don't use them. You'll want to investigate those options with more authoritative sources, if cross-platform is the way you prefer to go (versus my preference for using native tools/APIs).

---

### Post by Blice on 2007-11-13
I see. I'm pretty new to Linux, so I'm not familiar with the differences in code, and I'm pretty new in C++ (A few months.), I'm only just now making actual useful programs.

My idea was that I could write the program, and then just change the functions to the correct formats for whichever OS I compile on. Just seems like that would save a lot of time on larger programs.. GUIs are fast to make, I could remake them in a different OS with no problem, it's more so the backend code that I worry about. 

Or do you think completely re-writing the code would be easy? Maybe after writing it all out once, you'll be able to do it again without any hesitation with knowing exactly how everything is done? Could also just refer back to the original code when you come accrosed something that you have problems with...

---

### Post by j_g on 2007-11-13
If you really want to write cross-platform, your non-gui code should leverage the C library as much as possible. For example, on Windows, don't use the Win32 CreateFile() to open a file. That's not available on Linux. Use the C library's fopen(). That's available on Linux. Don't use the Win32 API ShellExecute() to launch another program. Use the C lib's system(). Don't use Win32's GlobalAlloc to allocate memory. Use C lib's malloc(). Etc. In other words, use the C library as much as possible.

For areas where there is no C library support, such as threading, you may have to employ judicious use of processor defines (bracket Win32 code with #ifdef WIN32 and #endif). That's because there's no C lib standard for Win32's CreateThread(). But you may be able to find some cross-platform add-on libs that do offer the needed functionality.

For a GUI, if you want to go cross-platform, investigate cross-platform GUIs. A number of people mention wxWidgets. But to some extent Gtk and Qt are two other alternatives that have some cross-platform support. Otherwise, if it's just easier to redo the GUI layout using native tools such as Glade on Linux, and MS's Visual C++ GUI builder, than you can dispense with cross-platform GUIs.

---

### Post by AlexThomson_NZ on 2007-11-13
If you want to use Glade with C++, you have to use Glademm, rather than vanilla glade.  From my experience Glademm is a bit rough around the edges, so I just stick with C and Glade.

(Sorry if someone's already pointed this out- I only skimmed over the thread)

---

### Post by slavik on 2007-11-13
> **j_g said:**
> To be honest, I'm not a fan of cross-platform development. When I write Windows software (and I do a lot of that), I prefer to use the most efficient, feature-rich (ie, supports as many of that operating system's unique features as possible) tools/libraries. I don't like writing, nor using, "lowest common denominator" software.
...


NOTE: I am cutting your post because pmasiar hates when someone quotes the entire thing ...

In any case ... Win32? Shouldn't you be using .NET? I thought Microsoft dumped Win32 and is on .NET ... :P

As for threading, I think there is a pthreads library for windows, isn't there?

As for lowest common denominator, why do we all use C (and Perl, and Python and C++, etc.) as they were designed to be platform independent ...

---

### Post by j_g on 2007-11-13
> Shouldn't you be using .NET?

I love Microsoft's dev tools. They're great. They easily beat anything I've used on Linux.

But I hate .NET. It's too abstract, and much too dependent upon underlying "components" whose documentation, performance, and reliability is not adequate for me.

I use Microsoft tools to write C apps that use the Win32 API, and those tools are the best I've used so far, and the Win32 API is the most useful, feature-rich API I've used to date. So far, I'm getting done what I need to do on Linux, using Linux tools. It works. But I don't like it as much.

> I thought Microsoft dumped Win32 and is on .NET

Microsoft have abandoned (or at least deprecated) a few things that I found to be quite useful, and felt should have been enhanced rather than deprecated (in favor of things that I find to be too abstract, poorly documented, and unreliable). That is one big reason why I'm persuing Linux development. I decided that I wasn't going with NET. (And I'm definitely not going with Vista and DRM. I'm a musician. I need really good timing, and anything that slows a system down for no reason that benefits me, is a deal-breaker).

Of course, if Linux starts moving in the same direction... I'm noticing more and more that Linux folks are starting to gravitate toward more abstract languages, and things that don't support C (such as Qt's lack of C support. I'd rather see Gnome supported, but Linux people seem to be gravitating toward Qt).

> I think there is a pthreads library for windows, isn't there?

Could be. But writing multi-threaded apps can be involved enough without having to use something that may not be feature-complete, adequately tested, or properly documented. You can definitely find docs and examples for the native Win32 API threading, and it has been well-tested. I use it a lot myself. (I've also used pthreads on Linux. It's one of the better Linux API implementations. Here's one area where I don't really feel like I'm taking a step back when moving from Win32 to Linux. But a lot of the other APIs... well...).

> why do we all use C as they were designed to be platform independent

I tend to use C because it makes it very easy to create DLLs (um, shared libraries to you Linux guys) without any compiler/language issues making me pull my hair out. I think that a DLL is a way of "reusing code" which is superior to C++ code. It typically results in smaller, faster code, uses less ram because code is shared between apps, and the DLL is an entirely separate compile from the apps so you can update a DLL without needing to recompile all apps using it, or vice versa. I write tons of DLLs, and I'm always designing my software with the idea that any useful feature that can be used in another program will go into a DLL.

I also dabble in writing device drivers, and I would never use anything but C (and/or asm) for that.

And frankly, I tend not to trust anything written in higher level languages because they usually all have some sort of "exception mechanism" to handle error situations, and yet I can count on one hand the number of times I've seen programmers correctly account for exception handling. Whenever my app uses some other software written in C++ (or such), I usually wonder "How long before this other software makes my app abruptly terminate because that software doesn't have adequate error handling, and how many resources are going to be leaked up until the point it crashes?".

C's "portability" (and actually, I think several other languages are more portable) is immaterial to me.

---

