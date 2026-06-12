---
title: "Gtk::Image resizing"
date: 2013-01-20
forum: Programming Talk
---

### Post by walkingbeard on 2013-01-20
Hi folks,

I am writing my first programme with gtk and as part of it, I have a Gtk::Image which is loaded as the user clicks on a TreeView item.

Loading the image is fine, but instead of fitting the bitmap to the size of the Gtk::Image, the Gtk::Image is expanded to fit the bitmap. I've been trying for about four hours to get the bitmap to automatically resize to the Gtk::Image. I can hardly believe that something so simple is so difficult.

I have given up on the automatic resizing, and tried to load the bitmap to a Gdk::Pixbuf, resize it manually and then load the Gtk::Image with the Gdk::Pixbuf, but the resizing just doesn't work. Here's my code:

```

Glib::RefPtr<Gdk::Pixbuf> temp = Gdk::Pixbuf::create_from_file(row[in_files.fullname]);
temp->scale_simple(750, 600, Gdk::INTERP_BILINEAR);
img_scrshot.set(temp);
```Do any of you understand why the Pixbuf isn't resizing? Can anyone help with the automatic resizing?

Thanks!

---

### Post by spjackson on 2013-01-20
See for example [http://developer.gnome.org/gtkmm/unstable/classGdk_1_1Pixbuf.html]("http://developer.gnome.org/gtkmm/unstable/classGdk_1_1Pixbuf.html")
> 
```

Glib::RefPtr< Gdk::Pixbuf > 	scale_simple (int dest_width, int dest_height, InterpType interp_type) const

```

This function does not modify its object, but returns a new scaled object.

---

### Post by limapapy on 2013-05-18
This is a snip of code that i use to re-size my image.
the simple re-size return the image re-sized without touching the original one.
```

bool GuiTag::on_draw_original(const ::Cairo::RefPtr< ::Cairo::Context>& cr){
  Glib::RefPtr<Gdk::Pixbuf> image_buf,image_scaled;
.
.
.
   image_scaled = image_buf->scale_simple(new_width,new_height, Gdk::INTERP_BILINEAR);    
   Gdk::Cairo::set_source_pixbuf(cr,image_scaled, (IMAGES_FRAME_WIDTH-new_width)/2, (IMAGES_FRAME_HEIGHT-new_height)/2);
   cr->paint();

```

---

