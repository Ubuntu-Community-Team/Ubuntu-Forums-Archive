---
title: "getting an exception while using glade in mono?"
date: 2009-11-26
forum: Programming Talk
---

### Post by shafi on 2009-11-26
Hi,
I am using the glade interface designers **( [http://glade.gnome.org/](http://glade.gnome.org/) )** for designing GUI.
I have created a very simple glade file which contains only a simple label.
When I use this glade file in C# via mono develop I am getting an exception.
This is the simple glade file:
```

<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="frmMain">
    <child>
      <object class="GtkLabel" id="label1">
        <property name="visible">True</property>
        <property name="label" translatable="yes">Sample label here ..</property>
      </object>
    </child>
  </object>
</interface>


```
Mono Main App:
```


using System;

namespace MonoGlade
{
	
	
	public class MainApp
	{
		
		public static void Main(string[] args)
		{
			Gtk.Application.Init();
			MainWindow wndMain = new MainWindow();
			wndMain.win.ShowAll();
			Gtk.Application.Run();

		}
	}
}


```
Mono Main Window:
```


using System;
using Gtk;
using Glade;


namespace MonoGlade
{
	
	
	public class MainWindow
	{
		public Gtk.Window win;
		Glade.XML xml;

		public MainWindow()
		{
			xml = new Glade.XML("/home/shafi/Projects/MonoGlade/MonoGlade/test4.glade","frmMain", "");
			win = (xml.GetWidget("frmMain") as Gtk.Window);
		}
	}
}


```

*************
this is the exception which I have got:

```


(MonoGlade:10346): libglade-WARNING **: Expected <glade-interface>.  Got <interface>.

(MonoGlade:10346): libglade-WARNING **: did not finish in PARSER_FINISH state

(MonoGlade:10346): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at MonoGlade.MainApp.Main (System.String[] args) [0x0000b] in /home/shafi/Projects/MonoGlade/MonoGlade/MainApp.cs:15 

The application was terminated by a signal: SIGHUP


```

**Note:** I have download another .glade file from internet and I replaced the path in Mono Window to this new file , working with out any problem, I have attached the mentioned file (please save as the file to .glade extension).
I think this new glade version need some extra configuration.

---

### Post by shafi on 2009-11-28
I have found the problem,
I must change the content of .glade file abit
the <interface> tag should be change to <glade-interface> , the  <requires lib="gtk+" version="2.16"/> should be omited, and the <object ...> tag should be replace with the <widget....> tag.
but this looks quite strange , why the glade do not provide the .glade files to be consistent with the mono?

---

### Post by shafi on 2009-11-28
> **shafi said:**
> 
but this looks quite strange , why the glade do not provide the .glade files to be consistent with the mono?

The problem solved, I have changed the project file format from GtkBuilder to Libglade.

---

