---
title: "Mono/C# programming: is it really this hard?"
date: 2009-07-30
forum: Programming Talk
---

### Post by tornadof3 on 2009-07-30
So I'm quite used to Perl and PHP programming, thought I'd give Mono/C# a go because I want to make some GUIs. So I created a new project ("solution) in Mono that is a GTK C# type project. Managed to design the GUI with the help of a little guide.

I've googled away for hours and can't find any up to date Mono/C#/Gtk# howtos or guides... All I am writing for my first project is a nice little recursive Pi calculator. I am stuck in 2 ways.

1. I cannot get something as simple as a pop-up message box to work
2. I cannot figure out how to "call" another function/subroutine from within the programme.

The GUI has a menu bar with the signals connected to OnClickGo and OnClickSetPiValue and a couple of buttons named btnSetPi and ActionGoBtnClicked, just want to link the buttons in so they invoke the code under the relevant menu item (to save duplication).

The MessageDialog causes an error when I try to run the program:

"Line=30, Column=55, Type=Error, Priority=Normal, Description=Expression denotes a `type', where a `variable', `value' or `method group' was expected(CS0119)]"

Mainwindow.cs:

```
using System;
using Gtk;


public partial class MainWindow: Gtk.Window
{	
	public MainWindow (): base (Gtk.WindowType.Toplevel)
	{
		Build ();
	}
	
	protected void OnDeleteEvent (object sender, DeleteEventArgs a)
	{
		Application.Quit ();
		a.RetVal = true;
	}

	protected virtual void OnClickExit (object sender, System.EventArgs e)
	{
		Application.Quit();
		
	}

	protected virtual void OnClickSetPiValue (object sender, System.EventArgs e)
	{
	}

	protected virtual void OnClickGo (object sender, System.EventArgs e)
	{
		MessageDialog md = new MessageDialog (MainWindow,
		                                      MessageType.Info,
		                                     ButtonsType.Ok,
		                                    "You clicked Go!");
	
		md.Run ();
		md.Destroy();

			
		

		
	}

	protected virtual void OnClickAbout (object sender, System.EventArgs e)
	{
		// Create a new About dialog
     AboutDialog about = new AboutDialog();
     
     // Change the Dialog's properties to the appropriate values.
     about.ProgramName = "Pi Calculator";
     about.Version = "1.0.0";
     
     // Show the Dialog and pass it control
     about.Run();
     
     // Destroy the dialog
     about.Destroy();

	}



	protected virtual void btnSetPi (object sender, System.EventArgs e)
	{
		// need some code here that 'calls' the OnClickSetPiValue function/class/etc
	}

	protected virtual void ActionGoBtnClicked (object sender, System.EventArgs e)
	{
		// need some code here that 'calls' the OnClickGo function/class/etc

		
	}
}
```

---

### Post by James- on 2009-07-30
> **tornadof3 said:**
> Mainwindow.cs:

```
using System;
using Gtk;


public partial class MainWindow: Gtk.Window
{	
	public MainWindow (): base (Gtk.WindowType.Toplevel)
	{
		Build ();
	}
	
	protected void OnDeleteEvent (object sender, DeleteEventArgs a)
	{
		Application.Quit ();
		a.RetVal = true;
	}

	protected virtual void OnClickExit (object sender, System.EventArgs e)
	{
		Application.Quit();
		
	}

	protected virtual void OnClickSetPiValue (object sender, System.EventArgs e)
	{
	}

	protected virtual void OnClickGo (object sender, System.EventArgs e)
	{
		MessageDialog md = new MessageDialog (MainWindow,
		                                      MessageType.Info,
		                                     ButtonsType.Ok,
		                                    "You clicked Go!");
	
		md.Run ();
		md.Destroy();

			
		

		
	}

	protected virtual void OnClickAbout (object sender, System.EventArgs e)
	{
		// Create a new About dialog
     AboutDialog about = new AboutDialog();
     
     // Change the Dialog's properties to the appropriate values.
     about.ProgramName = "Pi Calculator";
     about.Version = "1.0.0";
     
     // Show the Dialog and pass it control
     about.Run();
     
     // Destroy the dialog
     about.Destroy();

	}



	protected virtual void btnSetPi (object sender, System.EventArgs e)
	{
		// need some code here that 'calls' the OnClickSetPiValue function/class/etc
	}

	protected virtual void ActionGoBtnClicked (object sender, System.EventArgs e)
	{
		// need some code here that 'calls' the OnClickGo function/class/etc

		
	}
}
```


To call OnClickSetPiValue you can just forward the arguments
```

OnClickSetPiValue(sender,e);

```
if OnClickSetPiValue isn't "binded" an action like a button click I'd suggest making a function like

```

private void OnClickSetPiValue([args that are needed]){
}

```

If you aren't using the sender or the e(event args) i'd suggest just making a simple function

```

private void OnClickSetPiValue(){
}

//You can call by: OnClickSetPiValue();

```

---

### Post by jero3n on 2009-07-30
> **tornadof3 said:**
> 

The MessageDialog causes an error when I try to run the program:

"Line=30, Column=55, Type=Error, Priority=Normal, Description=Expression denotes a `type', where a `variable', `value' or `method group' was expected(CS0119)]"


I have no monodevelop here to check it, but i think this is better

```
MessageDialog md = new MessageDialog (this, MessageType.Info, ButtonsType.Ok, "You clicked Go!");
```

---

### Post by jero3n on 2009-07-30
By the way

This [http://oreilly.com/catalog/9780596007928](http://oreilly.com/catalog/9780596007928) is an excellent book to begin with.

---

### Post by Mirge on 2009-07-30
> **jero3n said:**
> By the way

This [http://oreilly.com/catalog/9780596007928](http://oreilly.com/catalog/9780596007928) is an excellent book to begin with.

Do you know if anything newer has been released that's as good? I might be interested in it as well.:KS

---

### Post by jero3n on 2009-07-30
> **Mirge said:**
> Do you know if anything newer has been released that's as good? I might be interested in it as well.:KS

Unfortunately I am not aware of any newer edition.

When I was looking for a good starting point for mono a couple of years ago this was my better finding.

However do not underestimate books/tutorials for older versions. Newer mono versions just add more library functionality, than change libraries or C#, which is something you may learn later, or when it is needed.

---

### Post by Mirge on 2009-07-30
> **jero3n said:**
> Unfortunately I am not aware of any newer edition.

When I was looking for a good starting point for mono a couple of years ago this was my better finding.

However do not underestimate books/tutorials for older versions. Newer mono versions just add more library functionality, than change libraries or C#, which is something you may learn later, or when it is needed.

Yeah, the book certainly looks good. I'm gonna go ahead and grab a copy I think. Thanks for the recommendation, I was having a hard time trying to find a good book on Mono/GTK#.

---

### Post by tornadof3 on 2009-07-30
Thanks for the replies, so now I now how to 'call' functions.

The "object sender, System.EventArgs e" stuff is a bit of a mystery - mono auto created them and removing them causes other errors elsewhere, but I think I can now call using OnClickGo(sender, e).

The message box still doesn't work tho? I get the following errors:

 Line=30, Column=37, Type=Error, Priority=Normal, Description=Argument `#2' cannot convert `Gtk.MessageType' expression to type `Gtk.DialogFlags'(CS1503)]
Line=30, Column=37, Type=Error, Priority=Normal, Description=The best overloaded method match for `Gtk.MessageDialog.MessageDialog(Gtk.Window, Gtk.DialogFlags, Gtk.MessageType, Gtk.ButtonsType, string, params object[])' has some invalid arguments(CS1502)]

Mainwindow.cs:

```
using System;
using Gtk;


public partial class MainWindow: Gtk.Window
{	
	public MainWindow (): base (Gtk.WindowType.Toplevel)
	{
		Build ();
	}
	
	protected void OnDeleteEvent (object sender, DeleteEventArgs a)
	{
		Application.Quit ();
		a.RetVal = true;
	}

	protected virtual void OnClickExit (object sender, System.EventArgs e)
	{
		Application.Quit();
		
	}

	protected virtual void OnClickSetPiValue (object sender, System.EventArgs e)
	{
	}

	protected virtual void OnClickGo (object sender, System.EventArgs e)
	{
		MessageDialog md =  new MessageDialog (this, MessageType.Info, ButtonsType.Ok, "You clicked Go!");
		md.Run ();
		md.Destroy();	

		
	}

	protected virtual void OnClickAbout (object sender, System.EventArgs e)
	{
			// Create a new About dialog
	     	AboutDialog about = new AboutDialog();
     
		     // Change the Dialog's properties to the appropriate values.
		     about.ProgramName = "Pi Calculator";
		     about.Version = "1.0.0";
		     
		     // Show the Dialog and pass it control
		     about.Run();
		     
		     // Destroy the dialog
		     about.Destroy();

	}



	protected virtual void btnSetPi (object sender, System.EventArgs e)
	{
		OnClickSetPiValue(sender, e);
	}

	protected virtual void ActionGoBtnClicked (object sender, System.EventArgs e)
	{
		OnClickGo(sender, e);

		
	}
}
```

I'm sure this can only be a simple error but coming from a Perl/PHP background, this all looks way more complicated than it needs to be. Back in the days of VisualBasic, a messagebox would just be MsgBox("Message!")

---

### Post by jero3n on 2009-07-30
> **tornadof3 said:**
> 
The "object sender, System.EventArgs e" stuff is a bit of a mystery - mono auto created them and removing them causes other errors elsewhere, but I think I can now call using OnClickGo(sender, e).


Well these auto generated functions are actually event handlers. The runtime calls them when an event has occured. Sender is an instance to the caller class, thus the object that caused the event, and the e is an object that contains information for the event. You probably dont have to care for these parameters now.

> **tornadof3 said:**
> 
 Line=30, Column=37, Type=Error, Priority=Normal, Description=Argument `#2' cannot convert `Gtk.MessageType' expression to type `Gtk.DialogFlags'(CS1503)]
Line=30, Column=37, Type=Error, Priority=Normal, Description=The best overloaded method match for `Gtk.MessageDialog.MessageDialog(Gtk.Window, Gtk.DialogFlags, Gtk.MessageType, Gtk.ButtonsType, string, params object[])' has some invalid arguments(CS1502)]

You forgot to put Gtk.DialogFlags before Gtk.MessageType. My error I didnt notice this before.

```
MessageDialog md = new MessageDialog (this, Gtk.DialogFlags.Modal , MessageType.Info, ButtonsType.Ok, "You clicked Go!");
```


Take a look at this
[http://www.mono-project.com/GtkSharpBeginnersGuide](http://www.mono-project.com/GtkSharpBeginnersGuide)
and this
[http://www.mono-project.com/GtkSharp](http://www.mono-project.com/GtkSharp)

---

### Post by tornadof3 on 2009-07-30
Wow thankyou everyone and thankyou jero3o, 

this program now compiles and runs without errors and creates a message box when I go to my menu item. However, interestingly, I note clicking the 'Go' button does not 'link' to the menu item (tho doesn't cause an error) as the message box doesn't pop up. Arghhh.. I think I'll have to find a C# and Mono book.

---

### Post by James- on 2009-07-30
> **tornadof3 said:**
> 
The "object sender, System.EventArgs e" stuff is a bit of a mystery - mono auto created them and removing them causes other errors elsewhere, but I think I can now call using OnClickGo(sender, e).


object sender, System.EventArgs e  are arguments passed to a function when an event like button click, textbox enter,etc(essentially what it is Handling)

object sender: Pretty self-explainatory, a object ref to the control that sent the message(for example button click, sender would be the button)

System.EventArgs e: if you go into e (.) it won't have much but if ButtonEventArgs was sent(in the case of button click) you could get a lot more properties from it as seen here(Under properties:

[http://msdn.microsoft.com/en-us/library/dd187621.aspx](http://msdn.microsoft.com/en-us/library/dd187621.aspx)

---

### Post by directhex on 2009-07-30
[http://www.zetcode.com/tutorials/gtksharptutorial/](http://www.zetcode.com/tutorials/gtksharptutorial/)

---

