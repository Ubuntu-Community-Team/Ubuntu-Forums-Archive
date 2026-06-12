---
title: "Monodevelop + Glade 2 little problems"
date: 2009-06-18
forum: Programming Talk
---

### Post by bennyboy2791 on 2009-06-18
I am using a libglade project in monodevelop.
It builds okay however I cannot for the life of me figure out how to use the press_icon function in C# for a text entry widget. I have the signals all there and the icon has the sensitive property to true. All I want is for it to be able to clear the text entry.
Glade Code:
```
   <widget class="GtkEntry" id="Search">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
                <property name="activates_default">True</property>
                <property name="truncate_multiline">True</property>
                <property name="caps_lock_warning">False</property>
                <property name="secondary_icon_stock">gtk-clear</property>
                <property name="secondary_icon_sensitive">True</property>
                <property name="secondary_icon_tooltip_text">Clear</property>
                <signal name="changed" handler="OnSearchChanged"/>
                <signal name="icon_press" handler="OnSearchClearClick"/>
              </widget>
```C# Code:
```
public void OnSearchClearClick (object sender, EventArgs e) {
        Search.Text = "";
    }
```I'm guessing it's extremely simple.

My second problem is that, in Glade, I've added a volume button.  It shows up fine in Glade, but whenever I run the program, I get this "libglade-WARNING **: unknown widget class 'GtkVolumeButton'" which I find silly.

Thanks in advanced!
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by monraaf on 2009-06-18
Ok, I just tried it with Python and PyGTK, works fine here. Are you running an older version of Ubuntu? The Icon in the gtk.Entry was  introduced in GTK+ 2.16. which was released on March 13 2009.

---

### Post by bennyboy2791 on 2009-06-18
Nope, I'm running Ubuntu Juanty 9.04
When I run the program, the entry widget shows up just fine, even with the icons.  It just doesn't seem to want to signal the icon_press (or I wrote the function completely wrong, which I don't doubt).
libgtk2.0 is 2.16.1

And I don't even know why the volumebutton is being recognized in monodevelop, though one thing at a time.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by monraaf on 2009-06-18
Well, I don't know C#, so I don't know if I can help you. Maybe you forgot to connect to the signal handler in your code? In Python I usually do something like this to connect the signals from a glade XML file:

```

self.widgets = gtk.glade.XML(gladefile)
self.widgets.signal_autoconnect(self)

```

---

### Post by bennyboy2791 on 2009-06-18
Dang, nope, it automatically connects signals
```
    public GladeApp (string[] args) {
        Application.Init ();

        Glade.XML gxml = new Glade.XML (null, "gui.glade", "MainWindow", null);
        gxml.Autoconnect (this);
        Application.Run ();
    }
``` (I didn't even have to write that code, it gave it to me) oh well, thank you for your help though, perhaps someone else may know.

[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by days_of_ruin on 2009-06-19
Are you really using Glade 2 ? That is outdated use Glade 3.

---

### Post by bennyboy2791 on 2009-06-19
Oh no, but I can see how you would think that, I probably shouldn't have use the number 2

I am using Glade 3, it's just that I have 2 problems.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by bennyboy2791 on 2009-06-19
bump
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by bennyboy2791 on 2009-06-19
Well, I've dropped the search box for now, I found an alternative.
But I'm still stuck on the volume button, and now, a new problem (horay!)

In a tree view, you can have a pixbuf to show an icon, however I cannot seem to find a way to just display a stock icon (generic-x-audio to be precise).  If anyone could help with that too, it would be greatly appreciated.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by days_of_ruin on 2009-06-19
[http://tadeboro.blogspot.com/2009/04/creatin-gtktreeview-with-glade-3.html]("http://tadeboro.blogspot.com/2009/04/creatin-gtktreeview-with-glade-3.html")

---

### Post by bennyboy2791 on 2009-06-20
days_of_ruin,  I owe you a beer, thank you for the link, it was a great tutorial and just what I needed :).
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

