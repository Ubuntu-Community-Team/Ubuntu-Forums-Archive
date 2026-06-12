---
title: "[gtkmm/gtk] Problem with adding widget in custom container"
date: 2009-03-22
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-03-22
Hi guys, this is related to this thread [link](http://ubuntuforums.org/showthread.php?t=1102572)


I was able to build a custom container/widget which has 2 gdk windows. I was also able to show both of them and manipulate them.

But now I have a new problem and I am totally clueless on where to look. If I try to add widget in my custom container the widget isn't shown. It is added, but I cannot see it.

Plz help me this is the last problem before my custom widget is fully functional.

Below is a test program that shows the problem. Just click on the "Test button". It removes itself from the current container and it adds itself on my custom container.

build it with this command
```
g++ main.cpp MainWindow.cpp video_wid.cpp `pkg-config gtkmm-2.4 --libs --cflags` -o test
```

---

### Post by Gordon Bennett on 2009-03-22
[http://chipx86.github.com/gtkparasite/]("http://chipx86.github.com/gtkparasite/") will help you track these kinds of things down.

---

### Post by SledgeHammer_999 on 2009-03-23
Interesting program but it didn't help me.
I managed to solve half of my problem. In the **video_wid::on_expose_event** if I add this:
[php]
bool video_wid::on_expose_event(GdkEventExpose* event)
{
    Gtk::Fixed::on_expose_event(event);
    return true;
}[/php]

The Button is shown on the red gdkwindow(video_widp) but whenever the green gdkwindow(display_areap) covers it(just resize the window) it is shown above the green window.

How do I make it appear above the other gdkwindow too?

---

