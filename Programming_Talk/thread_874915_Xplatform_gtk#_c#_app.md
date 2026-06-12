---
title: "Xplatform gtk# c# app"
date: 2008-07-30
forum: Programming Talk
---

### Post by mess110 on 2008-07-30
first of all hello :)

ok I moved to hardy and I was really interested in mono gtk# c#

I have a little problem here. from now on I want to make all my applications crossplatform but I have a little problem

```
// index.cs created with MonoDevelop
// Created by: kiki at 6:06 PM*7/30/2008

using System;
using Gtk;
using Microsoft;

public class GtkHelloWorld{
	
	public static void Main() {
		Application.Init();
		
		Window myWin = new Window("My first gtk# app crossplatform");
		myWin.Resize(200,200);
		
		Label myLabel = new Label();
		myLabel.Text = "Helloworld";
		
		myWin.Add(myLabel);
		
		myWin.ShowAll();
		
		Application.Run();
	}
}
```

this is a sample application I made and it works on linux. but it does not work on windows. I am using monodevelop. can anyone please tell me how to compile to work on both platforms? (I just press F5 to compile it.)

thx in advance

---

### Post by kknd on 2008-07-30
In Windows you will need Gtk# installed too.

---

### Post by mess110 on 2008-07-30
so there is no way to do that without installing stuff?

---

### Post by true_friend on 2008-07-31
you will have to install gtk+ for windows and gtk# binding as well. The gtk+ version for windows is 2.10 while at linux it is 2.12 now (not updated on windows yet) mean you have to build ur application on 2.10 by monodevelop addon which backports the application for windows. better is to ask this question on gtk# list. 
[http://www.go-mono.com/forums/](http://www.go-mono.com/forums/)
will be better place to ask about mono.
Regards

---

### Post by kknd on 2008-07-31
> **true_friend said:**
> you will have to install gtk+ for windows and gtk# binding as well. The gtk+ version for windows is 2.10 while at linux it is 2.12 now (not updated on windows yet) mean you have to build ur application on 2.10 by monodevelop addon which backports the application for windows. better is to ask this question on gtk# list. 
[http://www.go-mono.com/forums/](http://www.go-mono.com/forums/)
will be better place to ask about mono.
Regards

I use GTK 2.12.11 on Windows (there are pre-compiled binaries in [www.gtk.org](www.gtk.org)).

---

