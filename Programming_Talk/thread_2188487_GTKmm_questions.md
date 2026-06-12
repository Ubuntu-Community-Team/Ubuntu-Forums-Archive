---
title: "GTKmm questions"
date: 2013-11-17
forum: Programming Talk
---

### Post by Stauricus on 2013-11-17
hello everybody
i'm posting here because i couldn't find a GTK forum.
learning gtkmm is being a real pain. simply put, there is no GTK forum. most doc pages doesn't exist anymore (error 404). i have found some error i believe are bugs, but i couldn't find where to report them. taking into consideration that they seem to be too obvious bugs, i'm wondering: is gtkmm abandoned?

here is what i have done:
1-downloaded and instaled gtkmm 3
sudo apt-get install gtkmm-3.0-dev
2-updated Code::Blocks 12.11 with the compiler settings and linker settings:
`pkg-config --cflags  gtkmm-3.0`
`pkg-config --libs gtkmm-3.0`
3-made this little "program":
```
#include <gtkmm/main.h>
#include <gtkmm/window.h>
int main(int argc, char* argv[]){
    const int window_size_x = 800;
    const int window_size_y = 600;
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    window.set_default_size(window_size_x, window_size_y);
    window.set_resizable(false);
    window.set_name("GTK Test");

    kit.run(window);
    return 0;
}
```

which returns me a little-almost-invisible window (bug 1). if i set the resizable parameter to "true", the window appears correctly. but i do not want it to be resizable.
also, the window title is not correctly set to "GTK Test" (bug 2). it's set to "Project 2", which is the name set at Code::Blocks project creation. but this does not happen in SFML, for example, which works as expected.

i'm using Lubuntu 13.04, Code::Blocks 12.11, g++ 4.7.3, and the gtkmm-3.0-dev lib downloaded from the repositories (i don't know it's exact version).
i'd apreciate any sugestion on how to make the code work, or any news regarding gtkmm, or any suggestions on GUI libraries that are good and easy to use.
thanks in advance.


EDIT: I just realized that the correct function to set the window's title is "set_title", and not "set_name". i have no idea what "set_name" is for, tough.

---

### Post by r-senior on 2013-11-17
Have you looked at the gtkmm book?

[https://developer.gnome.org/gtkmm-tutorial/unstable/index.html.en](https://developer.gnome.org/gtkmm-tutorial/unstable/index.html.en)

It's probably also useful to have the GTK reference on hand. It's C, but you'll figure out how it maps to gtkmm:

[https://developer.gnome.org/gtk3/stable/](https://developer.gnome.org/gtk3/stable/)

You've already figured out you needed set_title rather than set_name. The set_name function is not on the window, it's inherited from the widget and is used for styling by name, and I believe by GUI builders like Glade.

The set_default_size doesn't appear to play nice with non-resizable windows. Use set_size_request and it works:

```
#include <gtkmm/main.h>
#include <gtkmm/window.h>

int main(int argc, char *argv[])
{
    const int window_size_x = 800;
    const int window_size_y = 600;
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    window.set_size_request(window_size_x, window_size_y);
    window.set_resizable(false);
    window.set_title("GTK Test");

    kit.run(window);
    return 0;
}

```

GTK is quite hard going at times and gtkmm is probably less well documented. I've not done much with gtkmm but I've grappled with GTK from Python and C quite a bit.

Lots of people swear by Qt and QTCreator, which you should probably have a look at before going much further with GTK.

[https://qt-project.org/wiki/Category:Tools::QtCreator](https://qt-project.org/wiki/Category:Tools::QtCreator)

Also WxWidgets:

[http://wxwidgets.org/](http://wxwidgets.org/)

I haven't used Qt but I have used wxWidgets and it's easier to use than GTK+ but there are some areas (that I don't remember now) where it wasn't quite possible to get a 100% native Gnome look. It is cross-platform though, as is Qt.

---

### Post by Stauricus on 2013-11-18
ok, thanks for the help :)
i'll have a look on those pages you linked. i'm a newbie and hobbist programmer, so it's not easy for me to discover how to use some things just by reading the reference.
in last case, i think i'll just switch to wxWidgets, which seems to be more documented...
thanks!

---

### Post by pbrane on 2013-11-18
you can have a look at this link if you haven't already. [https://developer.gnome.org/gtkmm-tutorial/stable/](https://developer.gnome.org/gtkmm-tutorial/stable/)

Also if you install devhelp and the gtkmm doc packages you can find those functions and figure out what they do.

For example,

```
void Gtk::Widget::set_name    (    const Glib::ustring &     name    )    
Widgets can be named, which allows you to refer to them from a CSS file.

You can apply a style to widgets with a particular name in the CSS file. See the documentation for the CSS syntax
(on the same page as the docs for Gtk::StyleContext).

Note that the CSS syntax has certain special characters to delimit and represent elements in a selector
(period, #, >, *...), so using these will make your widget impossible to match by name. Any combination
of alphanumeric symbols, dashes and underscores will suffice.

Parameters
name    Name for the widget.
```

---

### Post by Stauricus on 2013-11-19
ok! i've downloaded the gtkmm docs and devhelp (thanks for the info).
i started to have a look in wxWidgets, but i'm too stubborn. i really want to learn things in GTKmm (and i'm also trying to do the same thing in Python, just for learning :P )
if i'm not being annoying, i'd like to share my code here. i'm trying to create a simple tilemap editor, like the ones from RPG Maker. i have done almost nothing so far:
```
#include <gtkmm/main.h>#include <gtkmm/window.h>
#include <gtkmm/actiongroup.h>
#include <gtkmm/box.h>
#include <gtkmm/uimanager.h>
#include <gtkmm/action.h>
#include <gtkmm/stock.h>
#include <gtkmm/widget.h>
int main(int argc, char* argv[]){
    const int tile_size = 64;
    const int window_size_x = tile_size*10+tile_size*5;
    const int window_size_y = tile_size*10;
    Gtk::Main kit(argc, argv);
    Gtk::Window window;
    window.set_title("GTK Test");
    window.set_size_request(window_size_x, window_size_y);
    window.set_resizable(false);
    window.set_position(Gtk::WIN_POS_CENTER);


    Gtk::Box menubar_box(Gtk::ORIENTATION_VERTICAL);
    window.add(menubar_box);
    Glib::RefPtr<Gtk::ActionGroup> menubar_actgr = Gtk::ActionGroup::create();
    menubar_actgr->add(Gtk::Action::create("FileMenu", Gtk::Stock::FILE));
    menubar_actgr->add(Gtk::Action::create("NewFile", Gtk::Stock::NEW));
    menubar_actgr->add(Gtk::Action::create("SaveFile", Gtk::Stock::SAVE));
    menubar_actgr->add(Gtk::Action::create("OpenFile", Gtk::Stock::OPEN));
    menubar_actgr->add(Gtk::Action::create("Quit", Gtk::Stock::QUIT));
    menubar_actgr->add(Gtk::Action::create("Help", Gtk::Stock::HELP));
    menubar_actgr->add(Gtk::Action::create("About", Gtk::Stock::ABOUT));
    Glib::RefPtr<Gtk::UIManager> menubar_uimngr = Gtk::UIManager::create();
    menubar_uimngr->insert_action_group(menubar_actgr);
    {
        Glib::ustring menubar_uiinfo =
        "<ui>"
        "  <menubar name='MenuBar'>"
        "    <menu action='FileMenu'>"
        "      <menuitem action='NewFile'/>"
        "      <menuitem action='SaveFile'/>"
        "      <menuitem action='OpenFile'/>"
        "      <separator/>"
        "      <menuitem action='Quit'/>"
        "    </menu>"
        "    <menu action='Help'>"
        "      <menuitem action='About'/>"
        "    </menu>"
        "  </menubar>"
        "</ui>";
        menubar_uimngr->add_ui_from_string(menubar_uiinfo);
    }
    Gtk::Widget* menubar_wdgt = menubar_uimngr->get_widget("/MenuBar");
    menubar_box.pack_start(*menubar_wdgt, Gtk::PACK_SHRINK);


    //Gtk::Box statusbar_box(Gtk::Orientation::ORIENTATION_VERTICAL);
    //window.add(statusbar_box);


    window.show_all_children();
    kit.run(window);
    return 0;
}
```

i tried to put a status bar on the window (the commented lines), but got an error:
> Gtk-WARNING **: Attempting to add a widget with type gtkmm__GtkBox to a gtkmm__GtkWindow, but as a GtkBin subclass a gtkmm__GtkWindow can only contain one widget at a time; it already contains a widget of type gtkmm__GtkBox

so, i can't add more than one widget to the window? how do i create program with more than a single widget then? i tried adding a new container to the window, but no success... if anyone could show me how to do it properly, i'd be glad.
thanks again!

---

### Post by r-senior on 2013-11-19
You put a container into the window that accepts multiple widgets, usually a box or a grid:

[https://developer.gnome.org/gtkmm-tutorial/unstable/sec-multi-item-containers.html.en](https://developer.gnome.org/gtkmm-tutorial/unstable/sec-multi-item-containers.html.en)

A vertical box is perhaps the most common thing to add to the window, then add your menubar, toolbar, content area and status bar to the box. So rather than a menubar box, you want a box where your menubar is added with the first pack_start, then your toolbar with a second pack_start, and so on.

---

### Post by Stauricus on 2013-11-19
oh, ok! so, i did it like this:
```

Gtk::Grid window_grid;    
window.add(window_grid);

Gtk::Box menubar_box(Gtk::ORIENTATION_VERTICAL);
window_grid.add(menubar_box);

Gtk::Box statusbar_box(Gtk::Orientation::ORIENTATION_VERTICAL);
Gtk::Button button("Test Button!");
statusbar_box.pack_start(button);
window_grid.add(statusbar_box);

```

and i got this:
[IMG]http://s6.postimg.org/nw6d7hp9d/2013_11_19_175210_1366x768_scrot.png[/IMG]


it's getting better :P
but i do not understand something: if i change "statusbar_box.pack_start(button);" to "statusbar_box.pack_end(button);", nothing changes. shouldn't the test button go to the end of the window?? also, i intended to put the status bar at the end of the window, in the last row of the grid. is there any way to do that?

i hope i'm not bothering you guys with these questions.


btw, the docs says that vertical box is deprecated, and a simple box shoud be used instead. but i think a grid would make things more organized.
thanks again!

---

### Post by r-senior on 2013-11-19
I think the issue here is that your grid has the two boxes side by side, not that the button isn't at the "end" of the statusbar box when you use pack_end. I think you need to use attach() to add the menubar and statusbar in rows 0 and 1 respectively. 

[https://developer.gnome.org/gtkmm/3.1/classGtk_1_1Grid.html#a9c425e95660daff60a77fc0cafc18115](https://developer.gnome.org/gtkmm/3.1/classGtk_1_1Grid.html#a9c425e95660daff60a77fc0cafc18115)

Or I guess you could use add, but set the orientation of the grid to be vertical?

---

### Post by Stauricus on 2013-11-20
[SIZE=2][COLOR=#222222]you're right![/COLOR]
[COLOR=#222222]i used the attach method:[/COLOR]
```
[COLOR=#222222]window_grid.attach(menubar_box,0, 0, 1, 1);
[/COLOR][COLOR=#222222]window_grid.attach(statusbar_box,0, 2, 1, 1);[/COLOR]
```

[COLOR=#222222]and aditionally, i found this little function to make the bar ocuppy allthe horizontal space:[/COLOR]
[COLOR=#222222]```
menubar_box.set_hexpand(true);
```[/COLOR]
[COLOR=#222222]then i added some frames, each one contains a new grid, and here it is:[/COLOR]
[IMG]http://s6.postimg.org/u7pct4un5/2013_11_20_105012_1366x768_scrot.png[/IMG]


[COLOR=#222222]now the worst part starts. I[/COLOR][COLOR=#222222]'m [/COLOR][COLOR=#222222]t[/COLOR][COLOR=#222222]rying [/COLOR][COLOR=#222222]to achieve something visually like this:[/COLOR]
[IMG]http://2.bp.blogspot.com/_G75KT4bgxdY/TSG8thVOezI/AAAAAAAABkA/iQeEVLbln5s/s400/rpg+maker+xp+na+ratazana+games+01.gif[/IMG]

[COLOR=#222222]so,i made a small class to handle a Gtk::Image and a Gtk::EventBox (as it's said that images can't receive input by themselves). But it seems i can't create and resize() a vector of Gtk::images like this:[/COLOR]
```
[COLOR=#222222]std::vector<Gtk::Image>images;
[/COLOR][COLOR=#222222]images.resize(1);
```[/COLOR]


[COLOR=#222222]i got these error (among many others):[/COLOR]
> /usr/include/c++/4.7/type_traits|762|erro:within this context|[COLOR=#222222]/usr/include/c++/4.7/type_traits||Ininstantiation of &#8216;structstd::__is_nt_constructible_impl<Gtk::Image, Gtk::Image&&>&#8217;:|[/COLOR]
/usr/include/gtkmm-3.0/gtkmm/image.h|123|erro:&#8216;Gtk::Image::Image(const Gtk::Image&)&#8217; is private|

i'm not sure about what that means. Do i have to create the images by some other way?
[COLOR=#222222]btw, this works:[/COLOR]
[COLOR=#222222]```
Gtk::Image images[10];
```[/COLOR]

thanks again![/SIZE]

---

### Post by pbrane on 2013-11-20
it might be easier to use glade to build your GUI. it's in the repos. Use Gtk::Builder to load the resulting XML file(s).

---

### Post by Stauricus on 2013-11-21
oh no, my idea was to learn how to use some GUI library... without formbuilders... :/
i'll keep trying, thanks anyway.

---

### Post by r-senior on 2013-11-22
It's worth playing with Glade, even if you build the UI in code. It lets you play around with the layout and get a good idea in your head about what you need to do.

---

