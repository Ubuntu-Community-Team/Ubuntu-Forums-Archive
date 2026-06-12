---
title: "Problems with inheritance a ListStore, Gtk#"
date: 2005-06-19
forum: Programming Talk
---

### Post by Get on 2005-06-19
Hi!


I try to inheritance a ListStore inte my own class. I found out that I need to set the Columntypes with the SetColumnTypes function, but when I do that, I get error about "No overload for method `SetColumnTypes' takes `2' arguments(CS1501)". What have I made wrong?

```

using Gtk;
using System;
using GLib;

public class WordList : Gtk.ListStore {

/* Some code */

     public WordList (string language1, string language2) 
    {
		SetColumnTypes(typeof(string), typeof(string));
			
		
     }

/*Some more code */

}



```

---

### Post by born_confused on 2005-06-21
meaning there isnt an overload method that takes those parameters

EDIT: arent you supposed to use some keyword, such as super? rather than call the method, having a look at mono doc shows 

the constructors take in either Glib.Gtype[] System.types where as set columntypes only takes in  Glib.Gtypes

---

### Post by Get on 2005-06-22
[QUOTE=born_confused]meaning there isnt an overload method that takes those parameters

EDIT: arent you supposed to use some keyword, such as super? rather than call the method, having a look at mono doc shows 

the constructors take in either Glib.Gtype[] System.types where as set columntypes only takes in  Glib.Gtypes[/QUOTE]
 Thx

Sloved it with this.ColumnTypes = new GType[]{GType.String, GType.String};

---

