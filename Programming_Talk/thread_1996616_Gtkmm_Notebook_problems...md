---
title: "Gtkmm: Notebook problems.."
date: 2012-06-04
forum: Programming Talk
---

### Post by fallenshadow on 2012-06-04
Hi guys/gals,

I have been trying to do something simple with Gtk:Notebook. All I want to do for starters is get the number ID of the current tab.

I have the following code:

```
Gtk::Notebook *notebook;
		  refBuilder->get_widget("notebook", notebook);
			
		  int count = notebook.get_current_page();
		  
		  std::cerr << "TAB COUNT" + count << std::endl;

```

However I get the following error, which to me doesn't mean much:

> error: request for member ‘get_current_page’ in ‘notebook’, which is of non-class type ‘Gtk::Notebook*’


Does anyone understand this?

---

### Post by r-senior on 2012-06-04
I don't think you want the '*' before notebook. You are declaring a pointer to a Gtk::Notebook.

[http://developer.gnome.org/gtkmm-tutorial/stable/sec-basics-simple-example.html.en](http://developer.gnome.org/gtkmm-tutorial/stable/sec-basics-simple-example.html.en)

So the error message says you are trying to invoke a method on something which is not a class. Which is true -- it's a pointer to a class.

---

### Post by fallenshadow on 2012-06-04
Well this is the way it is done working with Glade. I have similar code for everything else and it does work.

Thanks for trying to help though!

---

### Post by r-senior on 2012-06-04
OK, I've not used gtkmm wth Glade but how about:

```
notebook->get_current_page()
```

---

### Post by pbrane on 2012-06-04
As r-senior points out you should use the **->** operator to access members of pointer objects.
```

Gtk::Notebook *notebook;
refBuilder->get_widget("notebook", notebook);
			
int idx = notebook->get_current_page();
		  
std::cerr << "Page Index: " << idx << std::endl;

```

Have a look at this gtkmm tutorial:
[http://developer.gnome.org/gtkmm-tutorial/stable/sec-multi-item-containers.html.en#sec-notebook]("http://developer.gnome.org/gtkmm-tutorial/stable/sec-multi-item-containers.html.en#sec-notebook")

---

### Post by fallenshadow on 2012-06-06
Yes it works now! Funnily enough I thought of the solution when I was in bed sleeping a few days ago, so I reckon I would of got it after a bit longer.

I just saw that in my first post I put a + sign! Looks like somebody has been doing too much Java lately! :D

Last question I swear! :) ...

You know the way many applications have an "X" to close each tab (built into the tab), is this possible with standard Gtkmm or do I need to do some kind of custom coding for it?

---

### Post by r-senior on 2012-06-06
You have to add the close button yourself. :(

[https://www.google.com/search?client=ubuntu&channel=fs&q=add+close+button+to+tab+gtk&ie=utf-8&oe=utf-8&gl=uk](https://www.google.com/search?client=ubuntu&channel=fs&q=add+close+button+to+tab+gtk&ie=utf-8&oe=utf-8&gl=uk)

---

### Post by fallenshadow on 2012-06-06
No problem, I have a great idea on how to do this! I will report back with a story of success or failure when I try this at home after work! :)

---

### Post by r-senior on 2012-06-06
I'd be interested. I have a little project (in Python but the GTK stuff is similar) where I'm at exactly the same point of wanting to make tabs with close buttons.

---

### Post by fallenshadow on 2012-06-06
Check it out! :)

[IMG]http://ubuntuone.com/0zixMq93m2yNkikAYFqFXr[/IMG]

I did this today on the way home. I spent a few minutes in Glade and a few in Inkscape. Didn't even touch a line of code! 8-)

Only problem is that this is fine for the first tab, next I need to figure out how to create a new tab with the same layout. I hope I can retrieve the same tab from the .glade file and create a new one... otherwise I will have to assemble code to create this and just call that method for creating a new tab. :)

---

### Post by fallenshadow on 2012-06-11
**@r-senior:**

So I created my close button in glade by doing the following:

Put a grid of 1 row and 2 columns. Put a label in the left and a small button on the right.

In order to create new tabs I will need to achieve the same in code.

Although I have no experience of Python I will try to describe what you need to do.

1. Create a Notebook to hold our tabs.
2. Create a method to do the following:

Create a label.
Create a button - use the stock close icon or do a custom icon if you wish.
Pack them into a Grid or h:box with the label first, then the button you defined earlier.

3. Connect signals to your button to close the current selected tab when clicked.

I found some code which seems to do the trick for Python! :) Check it out!

[http://www.eurion.net/python-snippets/snippet/Notebook%20close%20button.html](http://www.eurion.net/python-snippets/snippet/Notebook%20close%20button.html)

---

### Post by fallenshadow on 2012-07-07
Can anyone see anything wrong with this?

```

        Gtk::Viewport *view
	refBuilder->get_widget("viewport1", view);
	
	Gtk::Notebook *replace;
	refBuilder->get_widget("notebook", replace);
  
	view->remove(*replace);
  
	view->attach(m_Notebook);
```

I am attempting to replace the existing notebook in glade with a code built one. 

Here are the error messages:

> 
main.cc: In member function ‘Gtk::Window* mainWindow::init()’:
main.cc:103:2: error: expected initializer before ‘refBuilder’
main.cc:108:23: error: no matching function for call to ‘Gtk::Viewport::remove(Gtk::Notebook&)’
main.cc:108:23: note: candidate is:
/usr/include/gtkmm-3.0/gtkmm/bin.h:140:8: note: void Gtk::Bin::remove()
/usr/include/gtkmm-3.0/gtkmm/bin.h:140:8: note:   candidate expects 0 arguments, 1 provided
main.cc:110:8: error: ‘class Gtk::Viewport’ has no member named ‘attach’


So from what I understand Viewports don't have a call for attach or remove.. so how can I achieve what I want to do? :?

---

### Post by GeneralZod on 2012-07-07
> **fallenshadow said:**
> Can anyone see anything wrong with 

There's no semicolon after

```

        Gtk::Viewport *view

```

for a start ;)

---

### Post by fallenshadow on 2012-07-08
Wow thats yet another clumsy mistake! :oops:

Reduced the errors by 1 because of that! :D

> 
main.cc: In member function ‘Gtk::Window* mainWindow::init()’:
main.cc:108:23: error: no matching function for call to ‘Gtk::Viewport::remove(Gtk::Notebook&)’
main.cc:108:23: note: candidate is:
/usr/include/gtkmm-3.0/gtkmm/bin.h:140:8: note: void Gtk::Bin::remove()
/usr/include/gtkmm-3.0/gtkmm/bin.h:140:8: note:   candidate expects 0 arguments, 1 provided
main.cc:110:8: error: ‘class Gtk::Viewport’ has no member named ‘attach’


---

### Post by pbrane on 2012-07-09
I assume you want to add a notebook object with code. In your glade file remove the parent of the notebook which is a GtkViewport. (right click on the notebook object then select remove parent) Then you can use hbox1 as your container for the notebook. Add scrollable viewports to the individual notebook pages if you need them. Making the notebook itself scrollable is not necessary.

---

### Post by fallenshadow on 2012-07-10
Thanks! I surprisingly got it done myself! :)

Yeah I don't know why I had the notebook inside a viewport, I think I meant to have a viewport inside a notebook page, not the other way around! :D

---

