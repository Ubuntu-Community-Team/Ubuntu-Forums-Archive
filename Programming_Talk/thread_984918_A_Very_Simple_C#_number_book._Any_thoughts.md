---
title: "A Very Simple C# number book. Any thoughts?"
date: 2008-11-17
forum: Programming Talk
---

### Post by davidcaiazzo on 2008-11-17
```

using System;
using System.IO;
/* Assumes the file you want to use is called "thebook.txt" stored in the
 * directory of the .exe.
 */
public class phonebook
{
	public static void Main ()
	{
		Gtk.Application.Init ();
		new phonebook ();
		Gtk.Application.Run ();
	}
	
	public phonebook ()
	{
		string strbase;
		string [] strload;
		
		StreamReader readbook=new StreamReader("thebook.txt");
	
		Gtk.Window window = new Gtk.Window ("Phone Book");
		window.SetSizeRequest (500,200);
		Gtk.TreeView tree = new Gtk.TreeView ();
		Gtk.ListStore numberlist = new Gtk.ListStore (typeof (string), typeof (string));

		
		tree.AppendColumn("Name",new Gtk.CellRendererText(),"text",0);
		tree.AppendColumn("Number",new Gtk.CellRendererText(),"text",1);
		
		
		strbase=readbook.ReadToEnd();
		strload=strbase.Split('\n','(');
		readbook.Close();



		for(int i=0;(i+2)<strload.Length;i+=2){
			numberlist.AppendValues(strload[i],'('+strload[i+1]);
		}

		tree.Model = numberlist;
		window.Add(tree);
		window.ShowAll ();
	}
}

```

I am hoping to expand this code. Probably replace a text file with a sqlite database, add search, the ability to add new contacts, and to filter alphabetically. Before I venture off into that territory are there any opinions on how this is written so far? This is my first gtk app so I would appreciate feed back on it. I attached the source and the .exe as well.

---

