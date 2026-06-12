---
title: "[Mono/gtk#/c#-Newbie] Problems with listview"
date: 2005-08-14
forum: Programming Talk
---

### Post by André on 2005-08-14
Hi everybody,

[first of all listview isn't the right topic: Should be TreeView or CellRendererText but you can't edit the title after posting once, can you?]

i am trying to do the following in mono using c# and gtk#. Having a simple two column list with word and numbers. When you edit one field in any column write the new text into the edited field.

This must sound so newbish but i am struggeling with this a few hours now and so i decided to ask some people in the know. Til now i got this:

--> code begins
```

using System;
using Gtk;

class MainClass{
	private ListStore store;
	
	public static void Main(string [] args){
		Application.Init();
		Window w = new Window ("TreeView");
		w.DeleteEvent += Window_Deleted;
		VBox v = new VBox();
		v.BorderWidth = 6;
		w.Add(v);

		TreeView tv = new TreeView();
		tv.HeadersVisible = true;
		v.Add(tv);

		TreeViewColumn col = new TreeViewColumn();
		CellRendererText colr = new CellRendererText();
		colr.Editable = true;
		colr.Edited += Word_Edited;
		col.Title = "Wort";
		col.PackStart (colr, true);
		col.AddAttribute (colr, "text", 0);
		tv.AppendColumn (col);

		col = new TreeViewColumn();
		colr = new CellRendererText();
		colr.Editable = true;
		colr.Edited += Word_Edited;
		col.Title = "Seite";
		col.PackStart (colr, true);
		col.AddAttribute (colr, "text", 1);
		tv.AppendColumn (col);

		ListStore store = new ListStore (typeof (string), typeof (string));
		tv.Model = store;

		TreeIter iter = new TreeIter();
		iter = store.AppendValues("Andre", "12");
		iter = store.AppendValues("", "");

		w.ShowAll();
		Application.Run();
	}

	static void Word_Edited (object o, EditedArgs e){
		TreeIter iter;
		TreePath path = new TreePath(e.Path);
		store.GetIter(out iter, path);
		store.SetValue(iter, 0, e.NewText);
	}

	static void Window_Deleted (object o, DeleteEventArgs e){
		Application.Quit();
	}
}

```
--> code ends

which gives me:

--> compiler cries here
> 
andre@gremLin:~/programming/mono/IndexTool$ mcs -pkg:gtk-sharp TreeViewTryOut.cs
TreeViewTryOut.cs(40) warning CS0219: The variable 'iter' is assigned but its value is never used
TreeViewTryOut.cs(51) error CS0120: An object reference is required for the non-static field `store'
TreeViewTryOut.cs(52) error CS0120: An object reference is required for the non-static field `store'
TreeViewTryOut.cs(5) warning CS0169: The private field 'MainClass.store' is never used
Compilation failed: 2 error(s), 2 warnings

--> compiler stops crying here

I think the problem so far is, that my store variable is used in Main which is static. But when i make store static and edit some entry the program crashes hard like:

--> crash report:
> 
Unhandled Exception: System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
in <0x0004d> MainClass:Word_Edited (System.Object o, Gtk.EditedArgs e)
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[])
in <0x0006f> System.Reflection.MonoMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in <0x00104> System.Reflection.MonoMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00017> System.Reflection.MethodBase:Invoke (System.Object obj, System.Object[] parameters)
in <0x000b3> System.Delegate:DynamicInvokeImpl (System.Object[] args)
in <0x00028> System.MulticastDelegate:DynamicInvokeImpl (System.Object[] args)
in <0x0000e> System.Delegate:DynamicInvoke (System.Object[] args)
in <0x00147> GtkSharp.voidObjectstringstringSignal:voidObjectstringstringCallback (IntPtr arg0, System.String arg1, System.String arg2, Int32 key)
in (wrapper native-to-managed) GtkSharp.voidObjectstringstringSignal:voidObjectstringstringCallback (intptr,intptr,intptr,int)
in <0x00000> <unknown method>
in (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x003d0> MainClass:Main (System.String[] args)

--> crash report end

Any ideas? I am justing starting with mono and gtk# and so far i like it a lot but i have so much to learn before stopping to ask newbie questions :-/

I hope it is somehow easy to read this big thread. Please help and Greetings
André

---

### Post by André on 2005-08-16
Here comes the working one:

```


using System;
using Gtk;

class MainClass{
	private static ListStore store;
	
	public static void Main(string [] args){
		Application.Init();
		Window w = new Window ("TreeView");
		w.DeleteEvent += Window_Deleted;
		VBox v = new VBox();
		v.BorderWidth = 6;
		w.Add(v);

		TreeView tv = new TreeView();
		tv.HeadersVisible = true;
		v.Add(tv);

		TreeViewColumn col = new TreeViewColumn();
		CellRendererText colr = new CellRendererText();
		colr.Editable = true;
		colr.Edited += Word_Edited;
		col.Title = "Wort";
		col.PackStart (colr, true);
		col.AddAttribute (colr, "text", 0);
		tv.AppendColumn (col);

		col = new TreeViewColumn();
		colr = new CellRendererText();
		colr.Editable = true;
		colr.Edited += Word_Edited;
		col.Title = "Seite";
		col.PackStart (colr, true);
		col.AddAttribute (colr, "text", 1);
		tv.AppendColumn (col);

		store = new ListStore (typeof (string), typeof (string));
		tv.Model = store;

		TreeIter iter = new TreeIter();
		iter = store.AppendValues("Andre", "12");
		iter = store.AppendValues("", "");

		w.ShowAll();
		Application.Run();
	}

	static void Word_Edited (object o, EditedArgs e){
		TreeIter iter;
		TreePath path = new TreePath(e.Path);
		store.GetIter(out iter, path);
		store.SetValue(iter, 0, e.NewText);
	}

	static void Window_Deleted (object o, DeleteEventArgs e){
		Application.Quit();
	}
}

```

I really shouldn´t make store local in main ;-)

Greetings
André

---

