---
title: "Mono Glade# Error"
date: 2009-05-06
forum: Programming Talk
---

### Post by phmkem on 2009-05-06
Hello,

I am doing a little C# Program that makes a simple GUI with a Text Entry, A label and a button (When the button is clicked it brings up an alert box). 
Unfortunately the application can not find the xml file and I have provided the program with the **Full Path** to the file. Can someone show me my problem? the code is Below


```

using System;
using System.Text;
using System.Net;
using System.Net.Sockets;
using Glade;
using Gtk;

namespace GtkApps {
	
	class GladeApp {
		[Widget] Entry entry1;
		[Widget] Window window1;
		
		public static void Main(string[] args) {
			new GladeApp(args);
		}
		
		public GladeApp(string[] args) {
			Application.Init();
			Glade.XML gxml = new Glade.XML(null, "/home/keith/test/test/first.xml", "window1", null);
			gxml.Autoconnect(this);
			window1.ShowAll();
			Application.Run();
		}
		
		public void OnWindowDeleteEvent (object o, DeleteEventArgs args) {
			Application.Quit();
		}
		
		public void button1_click(object sender, EventArgs e) {
			Gtk.MessageDialog mes = new Gtk.MessageDialog(null, DialogFlags.DestroyWithParent, MessageType.Info,ButtonsType.Ok , "Hello " + entry1.Text);
			mes.Run();
			entry1.Text = "";
		}

	}
	
}

```

---

### Post by directhex on 2009-05-06
The problem here is you're not using the Glade.XML() constructor you think you are.

You're using Glade.XML(System.Reflection.Assembly assembly, string resource_name, string root, string domain) like this:

```
			Glade.XML gxml = new Glade.XML(null, "/home/keith/test/test/first.xml", "window1", null);
```

What this 4-method constructor is doing is saying "i want to use the embedded resource in the current (null) assembly, named '/home/keith/test/test/first.xml', build the widget named 'window1', and set no translation domain"

This will only work if you're embedding the resource using the -resource:first.xml flag to the compiler (or adding it as a resource in Monodevelop). And even then, I don't know how the full path stuff interacts with the name of the embedded resource, if at all.

If you want to use an embedded resource (i.e. compile your Glade XML into your app) then use:
```
			Glade.XML gxml = new Glade.XML( "first.xml", "window1", null);
```
And be sure to pass -resource:first.xml to gmcs.

Alternatively, if you want the XML to be loaded at run-time from a specified path (which is how it looks to me), then you want to use the painfully similar constructor Glade.XML(string fname, string root, string domain) like this:

```
			Glade.XML gxml = new Glade.XML("/home/keith/test/test/first.xml", "window1", null);
```

Now, THIS constructor takes a filename as input, not a resource name - it'll load the XML file when the app runs, not when it compiles

---

