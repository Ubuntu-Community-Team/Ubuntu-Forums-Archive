---
title: "How to catch Gdk::BUTTON1_MOTION_MASK"
date: 2017-06-21
forum: Programming Talk
---

### Post by rockandsalt on 2017-06-21
How do you catch the BUTTON1_MOTION_MASK? I'd like to get the location of my cursor on the widget when I press the middle mouse button.  The goal is to implement a rotation feature in a opengl widget. The following code snippet are inside an Gtk::ApplicationWindow called mainWindow.

I tried :
```

glWidget.add_events(Gdk::BUTTON2_MOTION_MASK);
glWidget.signal_motion_notify_event().connect(sigc::mem_fun(*this,&mainWindow::rotate));
```

with:
```
bool mainWindow::rotate(GdkEventMotion* motion_event)
{
    cout<<"test"<<endl;
}
```

But the code doesn't react when I click the middle button. 

The following snippet works when I replace the mask(BUTTON2_MOTION_MASK) with 
```
Gdk:POINTER_MOTION_MASK
```

 But it catches the signal and print test each time the pointer is on the widget which is not quite what I want.

---

### Post by norobro on 2017-06-22
I don't know enough about gtkmm to understand why one works but not the other. 

Try putting your glWidget inside an EventBox and see if it works. [https://developer.gnome.org/gtkmm-tutorial/3.0/sec-eventbox.html.en](https://developer.gnome.org/gtkmm-tutorial/3.0/sec-eventbox.html.en)

---

### Post by rockandsalt on 2017-06-22
Hi thanks for the answer. In the end, I figured it out. I needed to add the [COLOR=#2B91AF][FONT=inherit]Gdk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#303336][FONT=inherit]BUTTON1_MOTION_MASK and the [/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Gdk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#303336][FONT=inherit]BUTTON_PRESS_MASK mask. 

```
[COLOR=#303336][FONT=inherit]glWidget[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]add_events[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Gdk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Button1_MOTION_MASK[/FONT][/COLOR][COLOR=#303336][FONT=inherit]|[/FONT][/COLOR][COLOR=#2B91AF][FONT=inherit]Gdk[/FONT][/COLOR][COLOR=#303336][FONT=inherit]::[/FONT][/COLOR][COLOR=#303336][FONT=inherit]BUTTON_PRESS_MASK[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR]
```

But for some reason, this only react when I click the left mouse button. Still searching on how to get it to react to the middle mouse button. [/FONT][/COLOR]

---

### Post by norobro on 2017-06-22
If I understand what you are trying to do, the following seems to work:```
mainWindow::mainWindow() {
     set_default_size(600, 400);
     m_eventBox.add(m_glArea);
     m_eventBox.add_events(Gdk::BUTTON2_MOTION_MASK);
     m_eventBox.signal_motion_notify_event().connect(sigc::mem_fun(*this, &mainWindow::rotate));
     add(m_eventBox);
     show_all_children();
}

bool mainWindow::rotate(GdkEventMotion* motion_event) {
     std::cout<< motion_event->x << ", " << motion_event->y <<"\n";
     return true;
}
```
Clicking the middle button on the mouse and dragging produces output like this:```
[COLOR=#000000]173.118, 156.992[/COLOR]
[COLOR=#000000]173.851, 158.459[/COLOR]
[COLOR=#000000]173.851, 159.459[/COLOR]
[COLOR=#000000]174.851, 160.459[/COLOR]
[COLOR=#000000]175.851, 160.459[/COLOR]
[COLOR=#000000]176.851, 161.459
[/COLOR]...
```

---

### Post by rockandsalt on 2017-06-23
Hi thanks this works. I noticed that this will react to all the mouse button. This is not a problem since I can check which button was pressed using motion_event->state.
Since state is a bit mask, I went to the gdkModifier [page]("https://developer.gnome.org/gdk3/stable/gdk3-Windows.html#GdkModifierType") to find the correct constant to use if I want to check which key is pressed. But I noticed the value specified by GDK_BUTTON2_MOTION_MASK is different from what motion_event->state output. 

For the middle button the state value is 529 while GDK_BUTTON2_MOTION_MASK is 512. I can probably check for the value 529 but this seems ghetto and will probably create problem  if I port the program another platform. I checked with other button mask and they are all off aswell. Is that a bug or am I not using the correct constant? 

I am currently running ubuntu.

---

### Post by norobro on 2017-06-23
You're welcome!
> **rockandsalt said:**
>  Is that a bug ...Dunno. For a 529 GDK_BUTTON2_MASK, GDK_MOD2_MASK and GDK_LOCK_MASK would be set. [https://github.com/GNOME/gtk/blob/master/gdk/gdktypes.h#L234](https://github.com/GNOME/gtk/blob/master/gdk/gdktypes.h#L234)

Running the simple example above on my Debian box outputs 272, 528 and 1040 for mouse buttons 1-3.


One possible solution is, in your slot check to see if the bit for a button is set by doing a bitwise &. [https://developer.gnome.org/gtkmm/stable/group__gdkmmEnums.html#ga0288c23e93ded8c0326235f1f1120c61](https://developer.gnome.org/gtkmm/stable/group__gdkmmEnums.html#ga0288c23e93ded8c0326235f1f1120c61)
Like so:```
bool mainWindow::rotate(GdkEventMotion* motion_event) {
    if(motion_event->state & GDK_BUTTON2_MASK) {
        std::cout<< motion_event->x << ", " << motion_event->y <<"\n";
        return true;
    }
    return false;
}
```

---

