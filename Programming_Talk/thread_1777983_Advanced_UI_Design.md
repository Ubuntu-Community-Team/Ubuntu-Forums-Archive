---
title: "Advanced UI Design"
date: 2011-06-08
forum: Programming Talk
---

### Post by klay on 2011-06-08
Hi, i'm a new member here, I'm using Ubuntu as my primary Linux distribution.
I wanted to ask you something. I'm not a programmer, but i'm a freelance UI designer. **So what are the components or the programs that i should have to start to implement for example my photoshop design. I know about programs like MonoDevelop, but this program is suitable only for basic UI developing (GTK stuff) i want to make a fullscreen application with customizable, skinnable buttons and controls like XBMC (not a program like XBMC, a UI like).** 

;) thanks

---

### Post by simeon87 on 2011-06-08
GTK3 has support for theming, animations, and relating things. It's quite new but you could give that a go.

---

### Post by Petrolea on 2011-06-08
Most programming languages that support GUI will allow you to color buttons, but images in them and so on. Maybe not as much by just clicking around, but with writing some code.

---

### Post by doas777 on 2011-06-08
I think your goal may be too aggressive for GTK. were I to attempt that kind of interface (XBMC's) I would probably start with flash and silverlight.

other than that, you can make an image of your desired UI, and then cut it up into buttons, spacers, etc. then design your gui in gtk or whatever and set the images to the buttons and other objects.

---

### Post by Petrolea on 2011-06-08
> **doas777 said:**
> I think your goal may be too aggressive for GTK. were I to attempt that kind of interface (XBMC's) I would probably start with flash and silverlight.

other than that, you can make an image of your desired UI, and then cut it up into buttons, spacers, etc. then design your gui in gtk or whatever and set the images to the buttons and other objects.

Yeah, GTK isn't really meant for this. But check out Audacious (a simple player) and its look. It is really good and you could learn from its source. I'm not exactly sure how they achieve this awesome look, but I'm pretty sure it has something to do with GTK.

---

### Post by shawnhcorey on 2011-06-09
> **doas777 said:**
> I think your goal may be too aggressive for GTK.

Agreed.

However, if you truly want to do GUI programming, I suggest you learn [Glade]("http://glade.gnome.org/"), a user-interface designer.  Glade is for GTK but if you want cross-platform, consider [wxGlade]("http://wxglade.sourceforge.net/"), a user-interface designer for [wxWidgets]("http://www.wxwidgets.org/").  Originally written for Python, it now can be used with many languages and any application created with it can run on any machine with wxWidgets.

---

### Post by simeon87 on 2011-06-09
> **shawnhcorey said:**
> Agreed.

However, if you truly want to do GUI programming, I suggest you learn [Glade]("http://glade.gnome.org/"), a user-interface designer.  Glade is for GTK but if you want cross-platform, consider [wxGlade]("http://wxglade.sourceforge.net/"), a user-interface designer for [wxWidgets]("http://www.wxwidgets.org/").  Originally written for Python, it now can be used with many languages and any application created with it can run on any machine with wxWidgets.

GTK is also cross-platform.

---

### Post by shawnhcorey on 2011-06-09
> **simeon87 said:**
> GTK is also cross-platform.

Oops, forgot about that.  Thanks for pointing it out.

---

### Post by krazyd on 2011-06-09
I would recommend Qt.

Widgets can be styled using a simple declarative language similar to CSS. This might make things easier if you're not a programmer.

Check out Qt Style Sheets here:
[http://doc.trolltech.com/latest/stylesheet.html](http://doc.trolltech.com/latest/stylesheet.html)
Usage examples here:
[http://doc.trolltech.com/latest/stylesheet-examples.html](http://doc.trolltech.com/latest/stylesheet-examples.html)

---

