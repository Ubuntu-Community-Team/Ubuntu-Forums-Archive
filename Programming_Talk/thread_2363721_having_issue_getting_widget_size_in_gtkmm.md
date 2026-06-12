---
title: "having issue getting widget size in gtkmm"
date: 2017-06-13
forum: Programming Talk
---

### Post by rockandsalt on 2017-06-13
[COLOR=#242729][FONT=Arial]I have gtk::applicationWindow with an openGL widget. I would like to query the size of the openGL widget on creation and on resize. This is done so that I can compensate for the aspect ratio when I render a model. Here's a snippet of my code. The problem is that when I resize or spawn the window. The value of m_glAreaWidth and m_glAreaHeight are always 0. The widget does indeed spawn and reacts to resizing. So I don't understand how [/FONT][/COLOR]get_allocation[COLOR=#242729][FONT=Arial] gives a size 0 rectangle. Am I using this correctly?

[/FONT][/COLOR]```
[COLOR=#303336][FONT=inherit]mainWindow[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#303336][FONT=inherit]mainWindow[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]BaseObjectType[/FONT][/COLOR][COLOR=#303336][FONT=inherit]*[/FONT][/COLOR][COLOR=#303336][FONT=inherit] cobject [/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#101094][FONT=inherit]const[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Glib[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]RefPtr[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Gtk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Builder[/FONT][/COLOR][COLOR=#303336][FONT=inherit]>&[/FONT][/COLOR][COLOR=#303336][FONT=inherit] builder[/FONT][/COLOR][COLOR=#303336][FONT=inherit]):[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Gtk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]ApplicationWindow[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]cobject[/FONT][/COLOR][COLOR=#303336][FONT=inherit]),[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        m_refGlade[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]builder[/FONT][/COLOR][COLOR=#303336][FONT=inherit]),[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        [/FONT][/COLOR][COLOR=#858C93][FONT=inherit]//add GLArea Widget [/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        m_TopLayout[/FONT][/COLOR][COLOR=#303336][FONT=inherit]->[/FONT][/COLOR][COLOR=#303336][FONT=inherit]pack_start[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]m_GLArea[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        m_GLArea[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]set_auto_render[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#101094][FONT=inherit]true[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        signal_size_allocate[/FONT][/COLOR][COLOR=#303336][FONT=inherit]().[/FONT][/COLOR][COLOR=#303336][FONT=inherit]connect[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]sigc[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#303336][FONT=inherit]mem_fun[/FONT][/COLOR][COLOR=#303336][FONT=inherit](*[/FONT][/COLOR][COLOR=#101094][FONT=inherit]this[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]&[/FONT][/COLOR][COLOR=#303336][FONT=inherit]mainWindow[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#303336][FONT=inherit]on_my_size_allocate[/FONT][/COLOR][COLOR=#303336][FONT=inherit]),[/FONT][/COLOR][COLOR=#101094][FONT=inherit]false[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        [/FONT][/COLOR][COLOR=#858C93][FONT=inherit]//Makes window fill the whole screen[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        maximize[/FONT][/COLOR][COLOR=#303336][FONT=inherit]();[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        show_all[/FONT][/COLOR][COLOR=#303336][FONT=inherit]();[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

[/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    [/FONT][/COLOR][COLOR=#101094][FONT=inherit]void[/FONT][/COLOR][COLOR=#303336][FONT=inherit] mainWindow[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#303336][FONT=inherit]on_my_size_allocate[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Gtk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Allocation[/FONT][/COLOR][COLOR=#303336][FONT=inherit]&[/FONT][/COLOR][COLOR=#303336][FONT=inherit] allocation[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        [/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Gtk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Allocation[/FONT][/COLOR][COLOR=#303336][FONT=inherit] glAreaAlloc [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] m_GLArea[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]get_allocation[/FONT][/COLOR][COLOR=#303336][FONT=inherit]();[/FONT][/COLOR][COLOR=#303336][FONT=inherit]

        m_glAreaWidth [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] glAreaAlloc[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]get_x[/FONT][/COLOR][COLOR=#303336][FONT=inherit]();[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
        m_glAreaHeight [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] glAreaAlloc[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]get_y[/FONT][/COLOR][COLOR=#303336][FONT=inherit]();[/FONT][/COLOR][COLOR=#303336][FONT=inherit]


        m_GLArea[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]queue_render[/FONT][/COLOR][COLOR=#303336][FONT=inherit]();[/FONT][/COLOR][COLOR=#303336][FONT=inherit]


[/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR]
```

---

### Post by norobro on 2017-06-13
Just a wag, but if you want width and height shouldn't you be using:```
        [COLOR=#303336][FONT=&amp]m_glAreaWidth [/FONT][/COLOR][COLOR=#303336][FONT=&amp]=[/FONT][/COLOR][COLOR=#303336][FONT=&amp] glAreaAlloc[/FONT][/COLOR][COLOR=#303336][FONT=&amp].[/FONT][/COLOR][COLOR=#303336][FONT=&amp]get_width[/FONT][/COLOR][COLOR=#303336][FONT=&amp]();
[/FONT][/COLOR][COLOR=#303336]        m_glAreaHeight [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#303336] glAreaAlloc[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]get_height([/COLOR][COLOR=#303336]);[/COLOR]
```[https://developer.gnome.org/gtkmm/stable/classGdk_1_1Rectangle.html](https://developer.gnome.org/gtkmm/stable/classGdk_1_1Rectangle.html)

---

### Post by rockandsalt on 2017-06-13
> **norobro said:**
> Just a wag, but if you want width and height shouldn't you be using:```
        [COLOR=#303336][FONT=&amp]m_glAreaWidth [/FONT][/COLOR][COLOR=#303336][FONT=&amp]=[/FONT][/COLOR][COLOR=#303336][FONT=&amp] glAreaAlloc[/FONT][/COLOR][COLOR=#303336][FONT=&amp].[/FONT][/COLOR][COLOR=#303336][FONT=&amp]get_width[/FONT][/COLOR][COLOR=#303336][FONT=&amp]();
[/FONT][/COLOR][COLOR=#303336]        m_glAreaHeight [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#303336] glAreaAlloc[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]get_height([/COLOR][COLOR=#303336]);[/COLOR]
```[https://developer.gnome.org/gtkmm/stable/classGdk_1_1Rectangle.html](https://developer.gnome.org/gtkmm/stable/classGdk_1_1Rectangle.html)

Yep, turns out I was using the wrong method to retrieve the width.

---

