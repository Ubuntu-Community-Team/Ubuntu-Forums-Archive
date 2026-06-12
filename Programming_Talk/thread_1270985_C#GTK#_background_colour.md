---
title: "C#/GTK# background colour"
date: 2009-09-20
forum: Programming Talk
---

### Post by dchurch24 on 2009-09-20
I'm really stuck in a project I'm writing. I have a threaded TCPIP listener and connection to my MySQL database all working fine.

The hard bit seems to be changing the background colour of a button!!

How do you do this using C# and Gtk#?

I feel quite foolish asking such a question, but I've been googling for an hour now and am finding nothing!

---

### Post by Joshua Lückers on 2009-09-20
I found a [post](http://www.mail-archive.com/gtk-list@gnome.org/msg09146.html) on a gtk mailing list. I'll hope this will help you.

---

### Post by dchurch24 on 2009-09-20
Thank you, although I didn't really use that link, I did have a look and it did point me in the right direction.

Just so that there's something for people to google, I shall answer how to do it. It's really simple:

```

using Gtk;
...
Gdk.Color col = new Gdk.Color(255,0,0);		
[widget name here].ModifyBg (Gtk.StateType.Normal, col);
...

```

---

### Post by jl2035 on 2011-11-16
I guess this thread is no longer alive...

but anyway...

I'm trying to make Gtk buttons some other bg or fg color than default gray button color. 

Gdk.Color col = new Gdk.Color(255,0,0);		
btn1.ModifyBg (Gtk.StateType.Normal, col);

This code does nothing for me... is it even posible to change color of the button.

---

