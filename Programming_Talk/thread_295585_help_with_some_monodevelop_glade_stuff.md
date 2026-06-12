---
title: "help with some monodevelop glade stuff"
date: 2006-11-08
forum: Programming Talk
---

### Post by Choad on 2006-11-08
```

// project created on 11/8/2006 at 3:16 PM
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
		Application.Init ();

		Glade.XML gxml = new Glade.XML (null, "notes.glade", "window1", null);
		gxml.Autoconnect (this);
		Application.Run ();
	}

	// Connect the Signals defined in Glade
	
	// add button
	private void on_button1_clicked (object sender, EventArgs a) 
	{
		// add entry
		Glade.XML gxml = new Glade.XML (null, "notes.glade", "window2", null);
		gxml.Autoconnect (this);
	}
}


```

im just learning c# and glade and all that, and i am making a little app that will function as a "to do list" type thing. just a list with an add and remove button and whatnot. i have removed most of the callback functions from the code because they're irrelevant, i am just wondering 
a) if im going about calling up the new window in the correct way (check the button1_clicked event) 
and b) how can i disable the the original window when the new window is invoked (so that you have to deal with window2 before being able to bring window1 back in to focus) 
and c) how do i add things to a GtkList
and d) how do i transfer data from one window to another.... window2 is a text entry window, and i need to send the data back to be added as an entry to list1 (a gtkLIst)


ummm.... i hope i have been clear enough and i hope someone can help :)

---

### Post by Choad on 2006-11-09
bump!

cmon someone has got to know :)

---

