---
title: "Cairo text rendering"
date: 2008-05-22
forum: Programming Talk
---

### Post by xlinuks on 2008-05-22
Hi,
I'm using NetBeans 6.1 on Hardy learning Cairo through Gtkmm (C++).
I'm trying to display several lines of text through a loop using
the cairo "show_text" method, but for some reason every new line
of text gets shorter than the prev one by one letter, can anyone please
suggest what's the matter?

Here's the method (screenshot also attached):
```

bool FilesPane::on_expose_event(GdkEventExpose* event) {

        Glib::RefPtr<Gdk::Window> window = get_window();

        if (window) {
                cr = window->create_cairo_context();
                cr->select_font_face("Purisa", Cairo::FONT_SLANT_NORMAL,
                        Cairo::FONT_WEIGHT_BOLD);
                cr->set_font_size(13);
                int iLineHeight = 30;
                int ixOffset = 50;

		string str;
		
                for (int i = 1; i < 15; i++) {
                        str = "String Number #" + i;
			cr->move_to(ixOffset, iLineHeight * i);
                        cr->show_text(str);
                }
		
		
        }

        return true;
}

```

---

### Post by xlinuks on 2008-05-22
the cairo lib is fine.. looks like I wasn't using correctly the string class:
```

bool FilesPane::on_expose_event(GdkEventExpose* event) {

        Glib::RefPtr<Gdk::Window> window = get_window();

        if (window) {
                cr = window->create_cairo_context();
                cr->select_font_face("Purisa", Cairo::FONT_SLANT_NORMAL,
                        Cairo::FONT_WEIGHT_BOLD);
                cr->set_font_size(13);
                int iLineHeight = 30;
                int ixOffset = 50;

		string str;
		stringstream ss;
		
                for (int i = 1; i < 15; i++) {
			ss << i;
			string sNumber = ss.str();
			ss.str( "" );
                        str = "String Number #" + sNumber;
			log( str );
			cr->move_to(ixOffset, iLineHeight * i);
                        cr->show_text(str);
                }
		
		
        }

        return true;
}

```

---

