---
title: "Where are standard gtkmm images stored?"
date: 2010-04-13
forum: Programming Talk
---

### Post by f1r3flie on 2010-04-13
I have been learning to program in gtkmm, and the documentation has made references to the little default images often shown on buttons etc. One such file is "info.xpm". The problem is, the images just show up as error images (Might upload a screenshot later; don't have time to register an account for photobucket right now).

Where could I download these and where on my computer would I find them?

---

### Post by nvteighen on 2010-04-13
> **f1r3flie said:**
> I have been learning to program in gtkmm, and the documentation has made references to the little default images often shown on buttons etc. One such file is "info.xpm". The problem is, the images just show up as error images (Might upload a screenshot later; don't have time to register an account for photobucket right now).

Where could I download these and where on my computer would I find them?

Those are accessed from the GTK+ "Stock". You use macros like GTK_STOCK_OPEN or GTK_STOCK_INFO in functions that are designed to use them; usually widgets that are able to contain images have a special method for using a stock image. Look at GTK+'s API.

---

### Post by fallenshadow on 2010-04-13
Post a small bit of code and we can help you.

I used to be in your position (just starting with GTKmm) but now im quite used to the way stuff works.

---

### Post by f1r3flie on 2010-04-14
Here's a code snippet from one of my programs:
```
m_button.add_pixlabel("info.xpm", "cool button");
```
I want to find the directory these images are stored and also why it isn't displaying properly. The button and text label works fine.

---

### Post by nvteighen on 2010-04-14
> **f1r3flie said:**
> Here's a code snippet from one of my programs:
```
m_button.add_pixlabel("info.xpm", "cool button");
```
I want to find the directory these images are stored and also why it isn't displaying properly. The button and text label works fine.

The thing is you don't need to know where it is. Those "default" icons are abstracted through the stock system.

I'm not familiar with the gtkmm binding, but it seems that the Gtk::Button constructor allows you to pass a stock constant. Look at [http://old.nabble.com/Using-Stock-icons...-td23544663.html](http://old.nabble.com/Using-Stock-icons...-td23544663.html) The "info" icon would presumably be Gtk::Stock::Info.

This is coherent with the underlying C GTK+, where I'd use gtk_button_new_from_stock(GTK_STOCK_INFO) to get a button with that icon. PyGTK also uses the gtk.Button(stock_id) constructructor to do this.

---

