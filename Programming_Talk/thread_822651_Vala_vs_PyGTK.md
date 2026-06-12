---
title: "Vala vs PyGTK"
date: 2008-06-08
forum: Programming Talk
---

### Post by dmitrijledkov on 2008-06-08
I want to start to contribute to Gnome/Gtk based opensource projects. I am beginner programmer in C (know a bit of ECMAsript and Pascal). I haven't done any GUI nor OOP yet.

I do like Objective-C and before almost falling for it I do think It's a carefully placed trap by apple (I mean cocoa.h). C# is from the same league, including Mono. IMHO.

I'm scared of C++ (don't know why). But I do need/want to start doing GUI/Glibc/GObject/G* stuff.

Objective-C is not officially supported and I narrowed my choices down to learning Python and using PyGTK and everything like that. Or to learn Vala cause it seems to be designed to be perfect match to Gnome (eg similar to Objective-C+Cocoa on Mac and C#+.Net on Windows).

As far as I know C and GObject are a bit rough, cause C isn't really OOP. Therefore as a side question is C not used in Gnome projects? Cause by the look onto SVN Epiphany and Empathy are written in C + GObject and loads of other libs. Or am I wrong?

Is C enough to understand and start writting/reading&understanding/contributing to Gnome Apps? I'm confused.

---

### Post by bruce89 on 2008-06-08
> **dmitrijledkov said:**
> 
As far as I know C and GObject are a bit rough, cause C isn't really OOP. Therefore as a side question is C not used in Gnome projects? Cause by the look onto SVN Epiphany and Empathy are written in C + GObject and loads of other libs. Or am I wrong?

Is C enough to understand and start writting/reading&understanding/contributing to Gnome Apps? I'm confused.

GNOME uses C with GObject. Vala is a meta compiler which generates GObject C code. Vala is much nicer than GObject C.

You get the speed of C/GObject but it isn't so painful to write (~150 lines of C just to define a class).

```

using GLib;
using Gtk;

public class GtkSample : Window
{
	construct
	{
		title = "Sample Window";
		create_widgets ();
	}

	public void create_widgets ()
	{
		destroy += main_quit;

		var button = new Button.with_label ("Hello World");
		button.clicked += (btn) =>
		{
			title = btn.label;
		};

		add (button);
	}

	static void main (string[] args)
	{
		Gtk.init (ref args);

		var sample = new GtkSample ();
		sample.show_all ();

		Gtk.main ();
	}
}

```

I very much like Vala, all my tests these days are written in it.

---

### Post by Can+~ on 2008-06-08
I personally use python and GTK with glade3 to make the interfaces, then parse the xml with the library [FONT="Courier New"]gtk.glade[/FONT].

There's a nice tutorial here:
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

Anyway, I suggest you to learn python fully first (if you're going for the pythonic route) and make text based applications for learning, later you care about building a flashy gui around it.

---

### Post by pmasiar on 2008-06-09
Another vote for becoming competent programmer first, before trying to dive into FOSS project. If you wold ask for too much handholding, you get  plain ignored: time is the rarest commodity for a developer in any popular project. 

OTOH Python allows you to dip slowly and gently to programming, and then to OOP. GUI is too complicated for beginners, start with plain old commandline. PythonChallenge or Project Euler have plenty of training tasks, as has wiki in my sig.

---

### Post by mrsomoasun on 2011-10-12
> **pmasiar said:**
> Another vote for becoming competent programmer first, before trying to dive into FOSS project. If you wold ask for too much handholding, you get  plain ignored: time is the rarest commodity for a developer in any popular project. 

OTOH Python allows you to dip slowly and gently to programming, and then to OOP. GUI is too complicated for beginners, start with plain old commandline. PythonChallenge or Project Euler have plenty of training tasks, as has wiki in my sig.
Pmasiar, thank you. I've been slowly and steadily moving towards learning to code. Doing a lot of googling and such, I came across this thread. I've read many a long blog article along the way, but your short post here are some of the wisest words I've come across yet.

BTW, it looks like I'm heading down the 'quickly' path.

-Joel

---

### Post by sisco311 on 2011-10-13
Gravedigging.

Thread closed.

---

