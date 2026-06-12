---
title: "[SOLVED] C++ Window Icon"
date: 2008-10-25
forum: Programming Talk
---

### Post by BenAshton24 on 2008-10-25
Hey, I've written a small GUI calculator in c++ using the gtkmm libraries and it's all working perfectly however i would like to give the window an icon. I have googled about for a while and have found this:
> void Gdk::Window::set_icon  	(  	const Glib::RefPtr<Window>&   	 icon_window,
		const Glib::RefPtr<Pixmap>&  	pixmap,
		const Glib::RefPtr<Bitmap>&  	mask	 
	) 	
from [this page]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGdk_1_1Window.html#8eba9690001e09932eccc46c08aff05c") however i cannot make sense of it, am i even on the wright track :P? the window name is CalcWindow and my xpm icon is called icon.xpm Any help would be appreciated, thanx :D

---

### Post by BenAshton24 on 2008-10-25
It's okay i solved it now :D Realized i was heading completely the wrong way just added this bit of code after my code that displays the window

>   window.set_icon_from_file("icon.xpm");	

---

