---
title: "C# / GTK Question"
date: 2009-05-07
forum: Programming Talk
---

### Post by PaulM1985 on 2009-05-07
Hi

I have started to mess around with C# and GTK in Monodevelop.  I come from a Java background and I am used to adding action listeners to buttons and then implementing inner classes to deal with button clicks.

How do I add a similar thing to a button using C# and GTK?  I have found gtk_button_clicked(GTKButton *button) in the GTK documentation, but I am not sure if I am supposed to implement this method or if it already exists, and if I do have to implement it, where do I do it?

I am very new to C# so sorry if I have missed something really obvious.

Paul

---

### Post by cabalas on 2009-05-07
To handle an event in C# you need to add a new event handler to the event.  An event handler takes a function as a parameter which is what is called when the even is triggered.  The code for it looks like this.

[PHP]
button1.Clicked += new EventHandler(onButtonClicked);
[/PHP]

Generally you will of declared the function onButtonClicked somewhere else in your class.

---

### Post by PaulM1985 on 2009-05-08
Hi

I tried:

```

using System;
using Gtk;

public partial class MainWindow: Gtk.Window
{	
	public MainWindow (): base (Gtk.WindowType.Toplevel)
	{
		Build ();
		button1.Clicked += new EventHandler(ButtonClick());
	}
	
	protected void OnDeleteEvent (object sender, DeleteEventArgs a)
	{
		Application.Quit ();
		a.RetVal = true;
	}
	
	public void ButtonClick()
	{
		Console.Write("Button Clicked \n");	
	}
}

```

But I get the error: Method name expected, on the button1.Clicked line.

The actual adding of the button has been done by the GUI Builder.

Paul

---

### Post by sakabato on 2009-05-08
There should be no paranthesis there.  


button1.Clicked += new EventHandler(ButtonClick);


Notice there is no paranthesis after ButtonClick


Also the following is correct as well:

button1.Clicked += new ButtonClick;




Finally your event handler should be as below :

public void ButtonClick(object sender, EventArgs e)
	{
		Console.Write("Button Clicked \n");	
	}



I also strongly recommend you should read about the basics of events and delegates.




button1.Clicked += ButtonClick;

Also your ButtonClick methods' signature isnot EventHandler

It should be

---

### Post by jespdj on 2009-05-08
Is that the complete application? button1 in the example is the name of a variable, but you did you declare a variable named 'button1' anywhere in your source code - so the compiler will complain that it doesn't know what you mean with 'button1'.

---

### Post by PaulM1985 on 2009-05-08
Thanks sakabato.  That got it working.  I will look into the things you have mentioned.  I have found a tutorial on GTK that I am going to go through to help.

Thanks again.

Paul

---

### Post by SKLP on 2009-05-08
Also you can use anonymous delegate (i.e. closures) to handle the events, like so:
```

[...]
int a = 0;
button1.Clicked += delegate {
	a++;
	button1.Label = "Clicked " + a.ToString() + "times";
};
[...]

```
(havent checked if the property is really called "Label" but you get the picture...)

also if you need to handle the parameters a good way may be to use lambdas as then the parameter types can be inferred, such as:
```

[...]
button1.Clicked += (sender, eventargs) => {
    [...]
};
[...]

```

Also, you can use the GTK#-specific docs rather than the ones meant for plain GTK.
[http://www.go-mono.com/docs/](http://www.go-mono.com/docs/)

---

### Post by directhex on 2009-05-08
> **jespdj said:**
> Is that the complete application? button1 in the example is the name of a variable, but you did you declare a variable named 'button1' anywhere in your source code - so the compiler will complain that it doesn't know what you mean with 'button1'.

MonoDevelop stores declarations of variables designed using the GUI designer in a partial class, i.e. they're all automatically linked & available inside your code

---

