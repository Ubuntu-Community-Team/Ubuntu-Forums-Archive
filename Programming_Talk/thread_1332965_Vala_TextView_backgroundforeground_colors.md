---
title: "Vala: TextView background/foreground colors"
date: 2009-11-20
forum: Programming Talk
---

### Post by kumoshk on 2009-11-20
In Vala, using a GTK GUI, how do I change the background and foreground colors of a TextView widget *without* using a color chooser?

It would be nice if I could just put in a hexadecimal value or something.

I tried this, but it didn't seem to work:
```
var mybgcolor=Gdk.Color();
mybgcolor.red=0;
mybgcolor.blue=0;
mybgcolor.green=0;
this.text_view = new TextView();
this.text_view.modify_bg(Gtk.StateType.NORMAL, mybgcolor);
```

Also, if you can give similar help on how to set the font, let me know.

It's easy enough to do these things with WxPython (in Python), however, but Python won't suffice well for what I'm making. It'd be nice if they had WxWidgets for Vala.

---

### Post by days_of_ruin on 2009-11-21
Use [Gtk.Widget.modify_base]("http://references.valadoc.org/gtk+-2.0/Gtk.Widget.modify_base.html").

---

### Post by kumoshk on 2009-11-21
> **days_of_ruin said:**
> Use [Gtk.Widget.modify_base]("http://references.valadoc.org/gtk+-2.0/Gtk.Widget.modify_base.html").

Hmm. It seems that no matter what color I put in with this method, it always turns out black. It's better than white, but, I like options. Any advice?

Here's the code I used:
```
var mybgcolor=Gdk.Color();
mybgcolor.red=0;
mybgcolor.blue=255;
mybgcolor.green=0;        
this.text_view.modify_base(Gtk.StateType.NORMAL, mybgcolor);
```

---

### Post by kumoshk on 2009-11-21
I must be setting the color incorrectly, or something. Any ideas on how to set it without a color chooser dialog? I can see ways to do it with one.

---

### Post by kumoshk on 2009-11-21
> **kumoshk said:**
> I must be setting the color incorrectly, or something. Any ideas on how to set it without a color chooser dialog? I can see ways to do it with one.

I see my problem. The types for red, blue and green aren't supposed to be between 0 and 255, but rather between 0 and 65535. The type is a struct called uint16.

Hmm. This is kind of wild. Any idea how to do 6-digit hexadecimal input? e.g. #35F3EA

I've tried doing this through parse, but that seems to require a colormap or something, and that seems to require alloc_color to be initialized, but it won't initialize.

---

### Post by kumoshk on 2009-11-21
> **kumoshk said:**
> Any idea how to do 6-digit hexadecimal input? e.g. #35F3EA

Hooray! I've found out how to do this:

```
Gdk.Color.parse("#FFFFFF", out mybgcolor);
```

The whole out thing threw me off (still not used to that), otherwise I would have figured this out sooner, probably.

It doesn't work if I do the non-hex method before this in the same code, however. But, multiple calls of this seem to work fine. I'm guessing it's because they use different ranges of numbers.

Thanks for all the help!

If anyone's curious, modify_text works like modify_base for the font color.

Now I need to figure out how to set fonts.

---

### Post by kumoshk on 2009-11-21
> **kumoshk said:**
> Now I need to figure out how to set fonts.
Here's an example of how:
```
var docfont=new Pango.FontDescription();
docfont.set_family("Gentium");
docfont.set_size(18000);
this.text_view.modify_font(docfont);
```

---

