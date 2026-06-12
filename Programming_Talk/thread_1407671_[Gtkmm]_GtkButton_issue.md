---
title: "[Gtkmm] Gtk::Button issue"
date: 2010-02-15
forum: Programming Talk
---

### Post by kahumba on 2010-02-15
Hi,
How do I make a Gtk::Button display only its icon? (that is the icon without the text label)

---

### Post by SledgeHammer_999 on 2010-02-15
What happens when you do a **button.set_label("")** ?

---

### Post by kahumba on 2010-02-15
Forgot to mention, I'm creating the button from Gtk::Stock::GO_BACK, but I want it to show only the icon without the label.  And happens the opposite: a button with a label without the icon.

[SledgeHammer_999]("http://ubuntuforums.org/member.php?u=76221"): since the icon doesn't show up at all it only shows whatever label I set. Don't know what it has to do with my question though.

---

### Post by SledgeHammer_999 on 2010-02-15
Hmmm, can you give me a simple example code? (I certainly was able to show only an image using set_image(), in the past.)

---

### Post by kahumba on 2010-02-15
It looks like it's one of those Gnome's developers crappy decisions, the difference is that this decision is crappier than usually. I just read this:
[http://www.mail-archive.com/desktop-devel-list@gnome.org/msg17769.html](http://www.mail-archive.com/desktop-devel-list@gnome.org/msg17769.html)

Anyway, here's the example:
```

#include <gtkmm.h>

int main(int argc, char *argv[]) {
    Gtk::Main kit(argc, argv);
    Gio::init();
    Gtk::Window window;
    
    Gtk::Button *btn = Gtk::manage(new Gtk::Button(Gtk::Stock::GO_BACK));
    window.add(*btn);
    
    window.show_all_children();
    window.set_default_size(200, 200);
    Gtk::Main::run(window);
    return 0;
}

```

---

### Post by SledgeHammer_999 on 2010-02-15
Hmm after some digging I think I found an answer for your problem. From [Gtk::Button::set_image():](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Button.html#ac49972018a8ed3392e897cdf9da66391)
> Note that it depends on the **Gtk::Settings:gtk-button-images setting** whether the image will be displayed or not, you don't have to call Gtk::Widget::show() on image yourself.

So your code should look like this:
[php]#include <gtkmm.h>

int main(int argc, char *argv[]) {
    Gtk::Main kit(argc, argv);
    Gio::init();
    Gtk::Window window;

    Gtk::Settings::get_default()->property_gtk_button_images() = true;

    Gtk::Button *btn = Gtk::manage(new Gtk::Button(Gtk::Stock::GO_BACK));
    window.add(*btn);

    window.show_all_children();
    window.set_default_size(200, 200);
    Gtk::Main::run(window);
    return 0;
}[/php]

Unfortunately this shows the label too. Doing a set_label("") vanishes the image+label. After some digging I found what exactly are Stock IDs. They are not images. They are objects that can contain labels and/or images. From the gtk docs-->[link](http://library.gnome.org/devel/gtk/stable/gtk-Stock-Items.html):
> 
Each stock ID can be associated with a GtkStockItem, which contains the user-visible label, keyboard accelerator, and translation domain of the menu or toolbar item; and/or with an icon stored in a GtkIconFactory. See GtkIconFactory for more information on stock icons. The connection between a GtkStockItem and stock icons is purely conventional (by virtue of using the same stock ID); it's possible to register a stock item but no icon, and vice versa. Stock icons may have a RTL variant which gets used for right-to-left locales. 

So for me the simplest method to display a Stock Icon is doing it this way:
[php]
#include <gtkmm.h>

int main(int argc, char *argv[]) {
    Gtk::Main kit(argc, argv);
    Gio::init();
    Gtk::Window window;

    Gtk::Image img(Gtk::Stock::GO_BACK, Gtk::ICON_SIZE_BUTTON);

    Gtk::Button *btn = Gtk::manage(new Gtk::Button());
    btn->set_image(img);
    window.add(*btn);

    window.show_all_children();
    window.set_default_size(200, 200);
    Gtk::Main::run(window);
    return 0;
}[/php]

---

### Post by kahumba on 2010-02-15
Thanks a lot! seems to work!

---

