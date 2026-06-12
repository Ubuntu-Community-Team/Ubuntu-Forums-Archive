---
title: "Gtkmm: Creation of GC on a drawing area."
date: 2006-06-26
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-06-26
HI all,

I am trying to draw a simple line onto a drawing area and the way i created the GC, i am not sure about it: here is the code

> Glib::RefPtr<GDK::Window> win = get_window();
Glib::RefPtr<Gdk::GC> ggcc = GDK::GC::Create(drawingarea1->get_winow());
win->draw_line(ggcc,x,y,z,a);


Where x,y,z and a are drawingareas positions.(Diagonal Line);

is this wrong ? or is there any other way to draw a picture on a drawing area in gtkmm.

i am not getting the line drawn on the screen with the above method.

also if any one can tell me on how to decrease the size of the picture drawn on a big drawing area to a small drawing area it will be of a great help. is there any library function

I am new to linux , please help me with this.

Thanks a lot in advance

---

