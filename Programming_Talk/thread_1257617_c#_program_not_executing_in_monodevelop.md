---
title: "c# program not executing in monodevelop?"
date: 2009-09-04
forum: Programming Talk
---

### Post by abhilashm86 on 2009-09-04
this is actually a valid program in c#, but when i refer external assembly System.Windows.Forms, i'm getting error?

```
using System;
using System.Windows.Forms;
namespace pgm2.cs
{
	class MainClass
	{
		public static void Main(string[] args)
		{
	
			MessageBox.Show("this is referrning external assembly!!");			
		}
	}
}
```
how to include the assembly Windows.Forms?

---

### Post by phrostbyte on 2009-09-04
Go to References -> Edit References in your project and ensure System.Windows.Forms is present. Also make sure you have [this]("apt://libmono-winforms2.0-cil") package installed.

If you are writing a Gnome application look into using GTK# however, since it will integrate better in the environment and offer more flexibility (ZOMG vector graphics). MonoDevelop also has a GTK# visual designer.

---

### Post by abhilashm86 on 2009-09-05
> **phrostbyte said:**
> Go to References -> Edit References in your project and ensure System.Windows.Forms is present. Also make sure you have [this]("apt://libmono-winforms2.0-cil") package installed.

If you are writing a Gnome application look into using GTK# however, since it will integrate better in the environment and offer more flexibility (ZOMG vector graphics). MonoDevelop also has a GTK# visual designer.

i din't find any preferneces in my menus, also i found some addin manager.......

---

### Post by phrostbyte on 2009-09-05
It's on the left side of the screen, in the project hierarchy. There is a folder "References"

---

### Post by abhilashm86 on 2009-09-06
> **phrostbyte said:**
> It's on the left side of the screen, in the project hierarchy. There is a folder "References"

oh now i got it!! thanks a ton phrotbyte:) one more thing, everytime i open a c# solution, i need to checkmark and use the external assembly, how can i make my solution defaultly take and use all external assemblies??

---

