---
title: "GTK# Monodevelop question"
date: 2010-07-10
forum: Programming Talk
---

### Post by texaswriter on 2010-07-10
In the programming example below, a window class is created. It then seems [in the main()] that "def variable name = windowclass()" is used to instantiate it. When I use "def" in C#, it throws an error. I want to use this implementation, especially if I decided to have more than one window of a similar configuration. Hope this is clear enough. 

[http://nemerle.org/Gtk_text_editor](http://nemerle.org/Gtk_text_editor)

[PHP]using System;
using Gtk;
 
class MainWindow : Window
{
	public this()
	{
                // set caption of window
		base ("Very Simple Editor");
                // resize windows to some reasonable shape
		SetSizeRequest (300,200);
	}
}
 
module SimpleEditor
{ 
	Main() : void
	{
		Application.Init();
		def win = MainWindow();
 
                // exit application when editor window is deleted
                win.DeleteEvent += fun (_) { Application.Quit () };
 
                win.ShowAll ();
		Application.Run();
	}
}[/PHP]

---

### Post by cszikszoy on 2010-07-11
That's not C# code.  You need to compile that with ncc, the nemerle compiler.

[http://nemerle.org/Main_Page](http://nemerle.org/Main_Page)

---

### Post by texaswriter on 2010-07-11
> **cszikszoy said:**
> That's not C# code.  You need to compile that with ncc, the nemerle compiler.

[http://nemerle.org/Main_Page](http://nemerle.org/Main_Page)

Thanks for noticing that. It looked alot like C# code to me :o

---

### Post by cszikszoy on 2010-07-11
There are some good GTK# guides for C# here:

[http://www.mono-project.com/GtkSharpBeginnersGuide](http://www.mono-project.com/GtkSharpBeginnersGuide)
[http://www.mono-project.com/GtkSharp](http://www.mono-project.com/GtkSharp)

---

