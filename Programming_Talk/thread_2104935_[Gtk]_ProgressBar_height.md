---
title: "[Gtk] ProgressBar height"
date: 2013-01-14
forum: Programming Talk
---

### Post by bird1500 on 2013-01-14
Hi,
How can I control the height of the BrogressBar, by default it's as high as other widgets, which is too high, ugly, see screenshot.

set_size_request and other approaches seem to fail, meanwhile the nautilus file I/O dialog box has a progress bar with a small height, which is what I need too.

set_margin_top/bottom is a hack around it that sort of works with unclear consequences.

```

#include <gtkmm.h>

int main(int argc, char *argv[]) {
    Gtk::Main th(argc, argv);
    Gtk::Window win;
    
    Gtk::Box mainBox(Gtk::ORIENTATION_VERTICAL);
    win.add(mainBox);
    Gtk::Box box(Gtk::ORIENTATION_HORIZONTAL);
    mainBox.pack_start(box, false, true);
    
    Gtk::ProgressBar p;
    p.set_fraction(0.5);
    p.set_size_request(-1, 5);
    box.pack_start(p, false, true);
    
    Gtk::Button btn("OK");
    btn.set_size_request(100, 100);
    box.pack_start(btn, false, true);
    
    
    win.set_size_request(600, 200);
    win.show_all();
    th.run(win);
}

```

---

### Post by r-senior on 2013-01-15
You are setting your button to a height of 100. Did you mean to do that? Image button perhaps?

Try adding another vertical box to contain the progress bar. Set the expand and fill to true when you add that box, but set the expand on the progress bar to false.

It's worth having a copy of Glade to play around with these things visually, even if you decide to build the UI in code.

---

### Post by bird1500 on 2013-01-15
I'm setting the button so tall to show that the progress bar will also become as tall.
What you suggested doesn't seem to work, I wish the gtk progress bar height could be configured or was properly implemented.

---

### Post by SledgeHammer_999 on 2013-01-15
You need to use another Gtk::Box(let's name it x ) inside your Gtk::Box named box. You put your progress bar inside x and then x inside box.

I can't remember if x should have Gtk::ORIENTATION_HORIZONTAL or Gtk::ORIENTATION_VERTICAL. Try it out and see.

You should use Glade as a guide to how to do your GUI. Glade is a visual editor for Gtk.

---

### Post by r-senior on 2013-01-15
> **bird1500 said:**
> What you suggested doesn't seem to work ...
Maybe I didn't explain it fully enough. Here's a Python version that follows your code as closely as I can. (I'm not set up for gtkmm so this was quicker for me).

```
#!/usr/bin/env python

from gi.repository import Gtk

class Progress(Gtk.Window):

    def __init__(self):
        Gtk.Window.__init__(self, title='Progress')

        main_box = Gtk.VBox(False, 0)
        self.add(main_box)
        box = Gtk.HBox(False, 0)
        main_box.pack_start(box, False, True, 0)
        
        [COLOR="Red"]''' This is the new box for the progress bar '''
        vbox = Gtk.VBox(False, 0)
        box.pack_start(vbox, False, True, 0)[/COLOR]
        
        progress_bar = Gtk.ProgressBar()
        progress_bar.set_fraction(0.5)
        [COLOR="Red"]vbox.pack_start(progress_bar, False, True, 0)[/COLOR]

        button = Gtk.Button('OK')
        button.set_size_request(100, 100)
        box.pack_start(button, False, True, 0)

        self.set_size_request(600, 200)
        self.connect("destroy", self.on_quit)

    def on_quit(self, widget):
        Gtk.main_quit()

if __name__ == '__main__':
    Progress().show_all()
    Gtk.main()

```

I'd probably set expand on the new box so that it fills the width, and the controls need padding but I wanted to follow your code.

---

### Post by bird1500 on 2013-01-15
Thanks, your solution works, though it shows up the progress bar at the top, while I need it in the center (middle).

So while trying to center it vertically:
progressBar.set_valign(Gtk::ALIGN_CENTER);

I noticed that now I don't need any helper boxes any longer, that line makes the progress bar both thin vertically and vertically aligned at the center (middle), so I shot 2 issues down with one bullet, boy is Gtk weird.

With this line of code adding the progress bar to the mainBox doesn't matter if filled/expanded are true or false - the progress bar stays always thin regardless, go figure.

---

