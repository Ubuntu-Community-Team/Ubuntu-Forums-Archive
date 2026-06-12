---
title: "Drawable in pygtk ! cant get it work"
date: 2009-12-20
forum: Programming Talk
---

### Post by e=mc^3 on 2009-12-20
Hello,

After a night searching and trying, finally i think i need your help. Here is the code first:

```

import gtk

win=gtk.Window()

drawing_area = gtk.DrawingArea()
drawing_area.set_size_request(600, 400)

win.set_default_size(600,400)

win.add(drawing_area)

#retrieve the wrapped gtk.gdk.window... as the tutorial ...
drawable=drawing_area.window

#and draw... just a point
drawable.draw_point(xgc,100,100)

draw_area.show()
win.show()
gtk.main()


```Look ugly right ?  I just to make it as simple as possible. What i want to know is how the drawable and drawing thing in Pygtk work. So i do all the step as the tutorial. First to make a drawing area, then retrieve the wrapped gtk.gdk.window and then draw onto it.

But it doesnt work. It said:

[COLOR=Blue]  drawable.draw_point(xgc,100,100)
AttributeError: 'NoneType' object has no attribute 'draw_point'[/COLOR] 

[COLOR=Black]So, basically what is the simplest way to make it works ? I can do as the sample code in the tutorial and it works perfectly but i dont understand (drawing happen in the expose_event....as the tutorial)[/COLOR].

The tutorial dont say anything about the expose event. But i read somewhere it say that [COLOR=Teal]"[/COLOR][COLOR=Teal]When things need drawing in GTK+ an “expose-event” will be emitted"[/COLOR] and [COLOR=Teal]"[/COLOR][COLOR=Teal]When an expose event occurs, GTK+ will also give us other information, including the area of the widget that we need to redraw. All of this information is contained within the GdkEventExpose object."[/COLOR]

[COLOR=Black]I dont get it :([/COLOR] If i just move all the drawing code into the expose_event handler then connect the expose_event handler to the drawing_area then it works ! So all drawing stuff MUST be INSIDE the call back function for expose event ?


If we draw with cairo, is it the same way ?

Thanks

Chuong

---

### Post by nvteighen on 2009-12-20
The tutorial tells you you have to use the realize() method before grabbing the gtk.gdk.Window...

[QUOTE=PyGtk tutorial]
The DrawingArea must be realized (i.e. the Widget methods realize() or show() have been called) to have an associated gtk.gdk.Window that can be used for drawing.
[/QUOTE]

---

### Post by e=mc^3 on 2009-12-20
Thank you.

After i realize it, i can retrieve the gtk.gdk.window. It runs, but it dont display what i paint :D. Hmm, i guess i have to stick to the expose event.

---

