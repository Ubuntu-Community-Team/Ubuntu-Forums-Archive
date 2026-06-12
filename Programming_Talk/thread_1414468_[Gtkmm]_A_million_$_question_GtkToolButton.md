---
title: "[Gtkmm] A million $ question: Gtk::ToolButton"
date: 2010-02-23
forum: Programming Talk
---

### Post by kahumba on 2010-02-23
Hi,
I need to catch mouse **pressed** events of Gtk::ToolButton.
Can't do it. Tried different ways, even putting it inside an EventBox doesn't help.
Anyone knows if this is achievable at all?

---

### Post by SledgeHammer_999 on 2010-02-23
Gtk::ToolButton is derived from [Gtk::Widget](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Widget.html). That means that you can use all the signals Gtk::Widget emmits. So you can use [Gtk::Widget:::signal_button_press_event()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Widget.html#aa1a2371482cc55309d13c6f828e190f2)

Where's my 1 million $?

---

### Post by kahumba on 2010-02-24
Wait, wait :)
That doesn't work, I don't know why, have you tried it yourself?

---

### Post by SledgeHammer_999 on 2010-02-24
Uhm no I didn't try it :(

Because I am incredibly lazy could you provide an example code that uses a Gtk::ToolButton so I can then experiment on getting the "pressed" signal?

---

### Post by kahumba on 2010-02-24
There we go. When clicking the ToolButton nothing gets printed - proof that the Gtk::ToolButton doesn't respond to mouse press events.

Makefile must be in current folder and all .cpp files in a subfolder "src".

main.cpp
```

#include <gtkmm.h>

#include "Win.h"

int main(int argc, char **argv) {
    Gtk::Main kit(argc, argv);
    Win win;
    Gtk::Main::run(win);
    return 0;
}

```Win.h
```

#ifndef WIN_H
#define WIN_H

#include <iostream>
#include <gtkmm.h>

class Win : public Gtk::Window {
public:
    Win();
    virtual ~Win();
    
    virtual bool onButtonPress(GdkEventButton*);
};
#endif

```Win.cpp
```

#include "Win.h"

Win::Win() {
    Gtk::ToolButton *btn = Gtk::manage(new Gtk::ToolButton(Gtk::Stock::GO_BACK));
    btn->set_events(Gdk::BUTTON_PRESS_MASK);//just making sure
    btn->signal_button_press_event().connect(sigc::mem_fun(*this, &Win::onButtonPress));
    Gtk::HBox *hbox = Gtk::manage(new Gtk::HBox());
    hbox->pack_start(*btn);
    add(*hbox);
    set_default_size(300,300);
    show_all_children();
}

Win::~Win() {
}

bool Win::onButtonPress(GdkEventButton* event) {
    std::cout << "Button has been pressed!!" << std::endl;
}

```Makefile
```

APP = app
CC = g++
CFLAGS = -O1 `pkg-config --cflags gtkmm-2.4`
LDFLAGS = `pkg-config --libs gtkmm-2.4`
OBJ_FILES = main.o Win.o
LOG = @echo Compiling $@

$(APP): $(OBJ_FILES)
    @echo Creating executable $@
    $(CC) $(LDFLAGS) -o $@ $(OBJ_FILES)

main.o: src/main.cpp
    $(LOG)
    $(CC) $(CFLAGS) -c -o $@ $<

Win.o: src/Win.cpp src/Win.h
    $(LOG)
    $(CC) $(CFLAGS) -c -o $@ $<

clean:
    rm -rf $(APP) *.o

```Since the tabs are transformed into spaces (and Makefile becomes broken) I attached them too.

---

### Post by SledgeHammer_999 on 2010-02-25
You are out of luck.

The code works if you use eg a Gtk::HScale, but it fails if you use a Gtk::Button or a Gtk::ToolButton. It turns out that there is a specific (and old) bug of Gtk::ToolButton [here](https://bugzilla.gnome.org/show_bug.cgi?id=160056). You could work around it the way it is suggested there(connect to the "contained" gtk::button), or you could use Gtk::MenuToolButton(as it is said there, because I saw your other thread about popping a menu next to the button).

---

### Post by SledgeHammer_999 on 2010-02-25
Also never do a set_events() unless you specifically need only the event_mask you pass on that call and discard the previous event_mask. If you want to add an event then use add_events().

---

### Post by kahumba on 2010-02-25
Thanks,
The workaround doesn't work for me.
I'm not sure I (ever) posted a thread about popping a menu next to a button, but it doesn't matter.
I need the "press" event not to bring up a menu, but for another reason (which if I explain won't matter to readers anyway).
And yes, I find it sad, when the developers instead of fixing the bug change the subject to like "it's actually a nice side effect to prevent you from shooting yourself in the foot and we know better than you what you need" and the casuistry goes on and on.

---

