---
title: "Choosing a language to create an interface"
date: 2007-03-09
forum: Programming Talk
---

### Post by lucks on 2007-03-09
hi!

am a student and am working on my project...am having a lot of problems to create an interface which i will integrate with ARtoolkit (Augmented Reality is a system that joins real and virtual objects into a real environment setting, happening in real-time, while registering
(aligning) the real and virtual objects relative to each other).

ARtoolkit is in C and as per some recommendations, i am using Gtk+( in C also) to build an interface but am new to it and its very complicated and takes a lot of time with the coding and i dont know how to integrate it...i want to run my interface through ARtoolkit...

I fact i want to know if i can choose other language (such as Visual basic) to do the interface and which can interact with ARtoolkit...Is there any environment where i can easily create an interface??:( 

I am behind schedule for my project and have to complete it in 1 week...I would be much grateful if anyone can help me in this problem..please

thanks

---

### Post by rjfioravanti on 2007-03-09
I dont know anything about this ARtoolkit you need to work with, (sounds weird) but I recommend java swing for interface

Eclipse and Netbeans are both nice IDE's, Netbeans is good for building interfaces with drag and drop of buttons, and it generates pretty nice java code

Visual basic isnt platform independent, I don't even think you can use it on anything except windows, unless you have mono

---

### Post by pmasiar on 2007-03-09
> **lucks said:**
> am a student and am working on my project...am having a lot of problems to create an interface which i will integrate with ARtoolkit (Augmented Reality is a system that joins real and virtual objects into a real environment setting, happening in real-time, while registering
(aligning) the real and virtual objects relative to each other).

ARtoolkit is in C and as per some recommendations, i am using Gtk+( in C also) to build an interface but am new to it and its very complicated and takes a lot of time with the coding and i dont know how to integrate it...i want to run my interface through ARtoolkit...

I fact i want to know if i can choose other language (such as Visual basic) to do the interface and which can interact with ARtoolkit...Is there any environment where i can easily create an interface??:( 

ARtoolkit is on windows, right? I am not sure How easy would be to integrate it with a VB or Java program. Anyone knows a simple GUI builders for C?

Do you have to have GUI? can you keep it simple using command line input?

---

### Post by lnostdal on 2007-03-09
ah, if you're using GTK+ you should check out Glade (version 3.x is recommended; 2.x isn't that nice) .. just do:

```

sudo aptitude install glade-3

```

do you have some more concrete questions regarding this (gtk+, glade, libglade)? .. i can probably help you with some of this ... :)

edit:
i link to a short guide about how to integrate gtk+ and glade in my signature btw.

---

### Post by lucks on 2007-03-09
thanks to you all for your reply...

hi lnostdal,

in fact i`ve already started to use gtk+ (version 2.0) and i`ve managed to create just a simple  interface just for testing its integration with ARtoolkit...

well i am using C for Gtk+ on windows platform since i dont know too much on linux...i am very late with my project and nobody is able to help me...its nice that i got contact with you....:) 

i am using C since ARtoolkit is also in C and according to some info that i`ve got from some friends, they said that it should work...but i have tried a lot and am having a lot of problems..

am very down and need a lot of help in gtk+...will you help me please??:( 

thanks

---

### Post by lnostdal on 2007-03-09
well, what is the actual question(s)?

---

### Post by j_g on 2007-03-09
> started to use gtk+ on windows platform

Here's the deal.

You're probably following some GTK+ example whereby you manually create a window by calling the API gtk_window_new, and then creating each control (ie, widget in Linuxland) by calling various other APIs such as gtk_button_new_with_label to create a button. Then you're calling g_signal_connect to assign various callbacks to handle various "events" that happen with those controls.

Right?

Well, you don't have to do it that way. That's akin to calling the Windows API CreateWindow to create a window of your own class, and then calling CreateWindow to create each individual control in that window.

Have you ever used Microsoft Visual C++, or one of the .NET IDEs? They have a built-in GUI builder tool. It features a "panel" that contains all the different controls, and you just drag and drop controls on your own "template window" where you want the controls to appear. And then when you're done with your "window layout", you save it to a .RC file that gets linked to your executable. (ie, Your "window/dialog layouts" are saved in your EXE's resources). Then when you want to load/display one of the windows/dialogs, you just call DialogBox or LoadDialog, and the operating system takes care of creating the window and all its controls. (ie, The operating system does all those calls to CreateWindow for you).

Well, there is sort of the equivalent for GTK+, but with Linux, things aren't as simple or well-integrated as they are with Windows. First of all, that GUI builder tool for GTK+ isn't bundled with your C compiler. It isn't even bundled with the GTK+ libraries. So you have to go and install it separately. That GUI builder tool for GTK+ is called Glade. (There are a couple versions. Version 3 is the latest, and the one you should use). I don't use GTK+ on Windows, so I can't tell you if Glade3 is available on Windows, and if so, how complete/usable it is. So, the first thing you need to do is go to [http://gladewin32.sourceforge.net/modules/wfdownloads/](http://gladewin32.sourceforge.net/modules/wfdownloads/) and download/install the Glade GUI builder tool for Windows.

Now, unlike Microsoft's GUI builders, Glade does not produce a .RC file that you link with your executable (ie your Glade GUI layouts aren't ultimately embedded in your EXE's resources). Instead, Glade produces an XML data file containing your GUI layouts. This never gets embedded into your EXE. Instead, you must ship this XML data file along with your EXE. To load/display any of the windows/dialogs in this data file, you do not use the standard Windows APIs LoadDialog, DialogBox, et al. Instead, you need to download and install another support library (DLL) called libglade. It's available for Windows at the above web site. You will call a function in this DLL named glade_xml_new. (Think of this as GTK's version of LoadDialog).

If, when creating your GUI layout with Glade, you flipped to the "Signals" page of the Properties notebook for each control, and entered the name of your callback function to handle any events you desire, then you can avoid having to do a g_signal_connect for each event. You can call one libglade function that will do all the g_signal_connect calls for you. If you don't put the signal information in your glade XML file, then you'll have to connect up your signals the "old" way by calling g_signal_connect for each event on each control. Note that you'll need to call the libglade function glade_xml_get_widget to get a "handle" to each control. (ie, Think of glade_xml_get_widget as GTK's version of the standard Windows API GetDlgItem).

One more thing. Standard Win32 controls have numeric IDs. For example, maybe you have a button control with an ID of 1000. And then you have an EDIT control with an ID of 1001. GTK widgets don't use numbers for their IDs. They use string names. (Most all data in Linux is text-based. I swear, Linux programmers are scared to death of binary data). So unlike GetDlgItem to which you pass a control ID number, glade_xml_get_widget is passed the string name of the widget you want.

In conclusion, using the Glade GUI builder, and the libglade DLL, will pretty much give you what you get with MS dev tools, albeit not as simple and well-integrated as MS offerings. This should decrease the time it takes you to create your GUI with GTK+.

---

### Post by lnostdal on 2007-03-09
just gonna add to this that you can embed the xml-data in your .exe if you want to .. just use glade_xml_new_from_memory  instead of glade_xml_new

edit: you can even "download the gui" from a server over the internet this way .. just fill a char* buffer with the contents of what you download

---

### Post by j_g on 2007-03-09
Let me add to this add. That isn't the same as embedding the GUI layout in an EXE's resources. What he's talking about is using Glade to produce that XML data file. Then you load it up in your text editor (since it's essentially a text file). You copy the contents of it into your C source code, assigning as a string (ie, don't forget to add quotes to it, and modify it so that any embedded quotes inside the XML data don't mess it up) to some global/static variable in your C source. Then you pass the contents of this variable to glade_xml_new_from_memory.

Not really the same both from a technical standpoint, and a usability standpoint (because Glade doesn't spit out a version of the XML data all ready to be embedded in the C source). It is the same from a theoretical standpoint though.

---

### Post by lnostdal on 2007-03-09
yup, that's right .. but something like a one-liner via scons (or whatever) can do that automatically and transparently

---

