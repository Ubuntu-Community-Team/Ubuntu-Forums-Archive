---
title: "[gtkmm] Draw with cairo then create a Pixbuf out of it"
date: 2011-05-28
forum: Programming Talk
---

### Post by t1497f35 on 2011-05-28
Hi,
I need to create a Gtk::ToolButton with a custom image that I have to draw myself.

Hence the steps would probably be:
1) Create a cairo context/drawable
2) draw my stuff on it
3) create a pixbuf and somehow apply the previously drawn stuff to this pixbuf
4) create a Gtk::ToolButton with this pixbuf

Anyone knows how to do this?

Basically I can't figure out how to draw something using Cairo and then make a Pixbuf out of it.

---

### Post by SledgeHammer_999 on 2011-05-28
I think you're looking for [static Glib::RefPtr<Pixbuf> Gdk::Pixbuf::create(const Cairo::RefPtr< Cairo::Surface > &src, int src_x, int src_y, int width, int height)](http://developer.gnome.org/gtkmm/unstable/classGdk_1_1Pixbuf.html#aa5ca16c0ba15e4b9abb9bbc3a8f3d121)

If not, please let me know.

---

### Post by t1497f35 on 2011-05-28
Thanks a lot,
that function seems to be from gtk3 since it's not in the gtkmm-2.4 API.
I looked into the gtkmm3 API (installed Fedora 15) and it's indeed there, so if I don't find any solution for gtk2 I'll probably migrate my desktop and the app I'm trying to create to gtk3, thanks.

---

### Post by SledgeHammer_999 on 2011-05-28
DISCLAIMER: I haven't used cairo(or any other drawing API) so I may confuse you.

First of all, if I understood you correctly, you don't have sample code written. 
Also from the cairo docs(pointed from my link above) it seems that Cairo::Surface is a base class. I assume in your drawing you'll use Cairo::ImageSurface which inherits Cairo::Surface. Then you can use [Cairo::ImageSurface::get_data()](http://www.cairographics.org/documentation/cairomm/reference/classCairo_1_1ImageSurface.html#a94ba52fe4a201579c8a5541717822bdb) and combine with the appropriate Gdk::PixBuf::create().

(Indeed my previous link says "since 2.30" which means gtk3)

---

### Post by t1497f35 on 2011-05-29
Thanks, I actually did try out that approach before and it doesn't work (I don't know why), Gdk and Cairo could treat their big/little endian or whatever else differently, cause all I'm getting is a scrambled image, here's my code and a screenshot:

[PHP]
const int size = 24;
    
    Cairo::RefPtr<Cairo::ImageSurface> imSur = Cairo::ImageSurface::create(Cairo::FORMAT_RGB24, size, size);
    Cairo::RefPtr<Cairo::Context> cr = Cairo::Context::create(imSur);
    
//draw something to test out
    cr->set_source_rgb(0, 0, 1);
    cr->rectangle(0, 0, size, size);
    cr->fill();
    
    cr->move_to(0, 0);
    cr->set_source_rgb(0, 1, 0);
    cr->line_to(size, size);
    cr->stroke();
    
    Glib::RefPtr<Gdk::Pixbuf> pixbuf = Gdk::Pixbuf::create_from_data(
    imSur->get_data(), Gdk::COLORSPACE_RGB, false, 8, size, size, imSur->get_stride());

    Gtk::Image *pImg = Gtk::manage(new Gtk::Image(pixbuf));
    Gtk::ToolButton *btn = Gtk::manage(new Gtk::ToolButton());
    btn->set_icon_widget(*pImg);
    append(*btn);
[/PHP]

---

### Post by gmargo on 2011-05-29
> **t1497f35 said:**
> ```

    Glib::RefPtr<Gdk::Pixbuf> pixbuf = Gdk::Pixbuf::create_from_data(
    imSur->get_data(), Gdk::COLORSPACE_RGB, [COLOR=Red]false[/COLOR], 8, size, size, imSur->get_stride());

```

Try changing the **has_alpha** field from false to true.

I created something similar in pygtk, and got the same image pattern you did.  When I tried has_alpha=true, it started working.  Perhaps because the cairo FORMAT_RGB24 really uses 32-bits (24-bits color plus an empty alpha byte.)

---

### Post by t1497f35 on 2011-05-29
Thanks, unfortunately it still shows up a scrambled image.
In case anyone wanna tinker with this issue, it's in Toolbar.cpp, source code attached.

EDIT: forgotten: DONT run this app on Ubuntu 11.04 cause 11.04 ships with a nasty gtkmm bug which is not yet fixed.

---

### Post by SledgeHammer_999 on 2011-05-31
> **t1497f35 said:**
> Thanks, unfortunately it still shows up a scrambled image.
In case anyone wanna tinker with this issue, it's in Toolbar.cpp, source code attached.

EDIT: forgotten: DONT run this app on Ubuntu 11.04 cause 11.04 ships with a nasty gtkmm bug which is not yet fixed.


I don't know what your cairo drawing does and I don't know how the image is expected to look. But here is how it looks on Debian Unstable. Is it correct?

[[IMG]http://img9.imageshack.us/img9/4174/cairor.png[/IMG]](http://img9.imageshack.us/i/cairor.png/)

---

### Post by t1497f35 on 2011-05-31
Nope, it should be a blue rectangle with a green line across it... (I do this simple drawing just to check if it's working at all, if it worked I'd draw the image I actually need there to be, the "view" buttons, like on the mac finder)

[COLOR=#000000][COLOR=#FF8000]//draw something to test out
    [/COLOR][COLOR=#0000BB]cr[/COLOR][COLOR=#007700]->[/COLOR][COLOR=#0000BB]set_source_rgb[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700]);
    [/COLOR][COLOR=#0000BB]cr[/COLOR][COLOR=#007700]->[/COLOR][COLOR=#0000BB]rectangle[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]size[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]size[/COLOR][COLOR=#007700]);
    [/COLOR][COLOR=#0000BB]cr[/COLOR][COLOR=#007700]->[/COLOR][COLOR=#0000BB]fill[/COLOR][COLOR=#007700]();
    
    [/COLOR][COLOR=#0000BB]cr[/COLOR][COLOR=#007700]->[/COLOR][COLOR=#0000BB]move_to[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]);
    [/COLOR][COLOR=#0000BB]cr[/COLOR][COLOR=#007700]->[/COLOR][COLOR=#0000BB]set_source_rgb[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]);
    [/COLOR][COLOR=#0000BB]cr[/COLOR][COLOR=#007700]->[/COLOR][COLOR=#0000BB]line_to[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]size[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]size[/COLOR][COLOR=#007700]);
    [/COLOR][COLOR=#0000BB]cr[/COLOR][COLOR=#007700]->[/COLOR][COLOR=#0000BB]stroke[/COLOR][COLOR=#007700]();


[COLOR=Black]Anyway, I'll probably just move the app (some day) to gtk3 (gtk3 will ship with Ubuntu 11.10 by default) and that will hopefully help fix this issue with the solution you provided above. Until then I'll just develop the app without the "change view buttons" functionality which the pixbufs were supposed to represent.[/COLOR]
[/COLOR][/COLOR]

---

### Post by gmargo on 2011-05-31
I think what is happening is that the pixbuf holding the image is freed at the end of the Toolbar constructor. I got around this by forcing the copy constructor to trigger so that Glib::RefPtr does it's job.  (This may be all  wrong.  If you see the image getting corrupted again, then I've just moved the problem, not solved it.)

The following diff to Toolbar.cpp will make it work:
```

diff -r -u ufb.orig/gui/Toolbar.cpp ufb.test/gui/Toolbar.cpp
--- ufb.orig/gui/Toolbar.cpp    2011-05-29 21:19:44.000000000 -0700
+++ ufb.test/gui/Toolbar.cpp    2011-05-31 08:58:13.732524447 -0700
@@ -30,9 +30,10 @@
     Glib::RefPtr<Gdk::Pixbuf> pixbuf = Gdk::Pixbuf::create_from_data(
     imSur->get_data(), Gdk::COLORSPACE_RGB, true, 8, size, size, imSur->get_stride());
     
-    cr->paint();
+    //cr->paint();
 
-    Gtk::Image *pImg = Gtk::manage(new Gtk::Image(pixbuf));
+    // Force copy constructor to trigger so image is not freed.
+    Gtk::Image *pImg = Gtk::manage(new Gtk::Image(pixbuf->copy()));
     Gtk::ToolButton *btn = Gtk::manage(new Gtk::ToolButton());
     btn->set_icon_widget(*pImg);
     append(*btn);

```

---

### Post by t1497f35 on 2011-05-31
Oh boy you're so right I even feel ashamed that it's a scope issue.. thanks anyone!

Edit: Cairo::ImageSurface was getting out of scope, for some reason.

Edit 2: there are my 2 view buttons!

[PHP]
Gtk::Image* Toolbar::createViewImage(const guchar type) {
    static const int size = 24, gap = 4;
    Cairo::RefPtr<Cairo::ImageSurface> imSur = Cairo::ImageSurface::create(Cairo::FORMAT_RGB24, size, size);
    Cairo::RefPtr<Cairo::Context> cr = Cairo::Context::create(imSur);
    cr->set_source_rgb(0, 0, 0);
    cr->set_line_width(1.0);
    cr->set_antialias(Cairo::ANTIALIAS_NONE);//to draw thin lines
    
    if((type & View::VIEW_AS_LIST) != 0) {
        for(int i=gap; i<size; i+=5) {
            cr->move_to(gap, i);
            cr->line_to(size-gap, i);
            cr->stroke();
        }
    } else if((type & View::VIEW_AS_ICONS) != 0) {
        
        const int w = 6;
        //top left
        cr->rectangle(gap, gap, w, w);
        cr->stroke();
        //top right
        cr->rectangle(size-gap-w, gap, w, w);
        cr->stroke();
        
        //bottom left
        cr->rectangle(gap, size-gap-w, w, w);
        cr->stroke();
        
        //bottom right
        cr->rectangle(size-gap-w, size-gap-w, w, w);
        cr->stroke();
    }
    
    Glib::RefPtr<Gdk::Pixbuf> pixbuf = Gdk::Pixbuf::create_from_data(
        imSur->get_data(), Gdk::COLORSPACE_RGB, true, 8, size, size, imSur->get_stride());

    return Gtk::manage(new Gtk::Image(pixbuf->copy()));//copy to tackle out of scope issue
}
[/PHP]

---

### Post by SledgeHammer_999 on 2011-05-31
Hmm maybe this is a bug in gtkmm? Shouldn't the Gtk::Image constructor increase the refcount? Or are you supposed to keep the pixbuf around? (as a private variable of the class)

---

### Post by t1497f35 on 2011-05-31
It could be a bug indeed, there _is_ a bug in gtkmm that I'm aware of (in Ubuntu 11.04), so yet another one wouldn't surprise me.
The one [I'm aware of]("http://mail.gnome.org/archives/gtkmm-list/2011-May/msg00001.html") has been fixed upstream though (on May 9th I guess), but no clue if/when it lands in Ubuntu 11.04.

---

### Post by SledgeHammer_999 on 2011-05-31
If I have time I'll try to ask on the mailing list to confirm that this is a bug.

Side note: Does it work, if you manually increase the refcount of the RefPtr instead?

---

### Post by t1497f35 on 2011-05-31
> **SledgeHammer_999 said:**
> If I have time I'll try to ask on the mailing list to confirm that this is a bug.

Side note: Does it work, if you manually increase the refcount of the RefPtr instead?
I don't really know how to do that (increase refcount manually), do you? Did a quick google no luck.

---

### Post by SledgeHammer_999 on 2011-05-31
```
pixbuf->reference();
```

Basically everything that inherits from Glib::ObjectBase has this function.

---

### Post by t1497f35 on 2011-06-01
Thanks a lot! It started working now without having to make a copy of the Pixbuf!

But guess what, I don't need to increment the refcount of the pixbuf itself (it doesn't fix the issue), but for some reason either that of the cairo context (Cairo::RefPtr<Cairo::Context> cr) [FONT=Arial Black]**or**[/FONT] of the cairo image surface (Cairo::RefPtr<Cairo::ImageSurface> imSur), here:

[PHP]
Gtk::Image* Toolbar::createViewImage(const guchar type) {
    static const int size = 18, gap = 3;
    Cairo::RefPtr<Cairo::ImageSurface> imSur = Cairo::ImageSurface::create(Cairo::FORMAT_RGB24, size, size);
    imSur->reference();//THIS FIXES IT
    Cairo::RefPtr<Cairo::Context> cr = Cairo::Context::create(imSur);
    //cr->reference();//THIS ALSO FIXES IT,
//but not needed since reference() already applied above
    cr->set_source_rgb(0, 0, 0);
    cr->set_line_width(1.0);
    cr->set_antialias(Cairo::ANTIALIAS_NONE);
    
    if((type & View::VIEW_AS_LIST) != 0) {
        for(int i=gap; i<size; i+=3) {
            cr->move_to(gap, i);
            cr->line_to(size-gap, i);
            cr->stroke();
        }
    } else if((type & View::VIEW_AS_ICONS) != 0) {
        const int w = 4;
        //top left
        cr->rectangle(gap, gap, w, w);
        cr->stroke();
        //top right
        cr->rectangle(size-gap-w, gap, w, w);
        cr->stroke();
        //bottom left
        cr->rectangle(gap, size-gap-w, w, w);
        cr->stroke();
        //bottom right
        cr->rectangle(size-gap-w, size-gap-w, w, w);
        cr->stroke();
    }
    
    Glib::RefPtr<Gdk::Pixbuf> pixbuf = Gdk::Pixbuf::create_from_data(
        imSur->get_data(), Gdk::COLORSPACE_RGB, true, 8, size, size, imSur->get_stride());

    return Gtk::manage(new Gtk::Image(pixbuf));//NO COPY NOW!
}
[/PHP]

---

### Post by SledgeHammer_999 on 2011-06-01
Hmm, but are you sure this is the correct way? Maybe you're leaking memory by not freeing imSur...

Maybe imSur is meant to be a private variable in your class(or be stored in a vector) so it won't go out of scope and thus get destroyed???

(I am not sure about any of these. I'll try to make a post in the mailing list if I find the time).

---

### Post by t1497f35 on 2011-06-01
I'm simply doing what works since (I think) it doesn't work the way it's supposed to, so I don't really have a much better option than this one - to increase the refcount and hence avoid an extra pixbuf copy.
I'm not leaking memory because it's about 2 tiny images 18x18 pixels each.
To tell you the truth imho the gtkmm devs are so involved in gtkmm3 that the gtkmm2.4 has regressed and is quite buggy right now, anyone is free to disagree obviously.

---

### Post by SledgeHammer_999 on 2011-06-01
> **t1497f35 said:**
> I'm simply doing what works since (I think) it doesn't work the way it's supposed to, so I don't really have a much better option than this one - to increase the refcount and hence avoid an extra pixbuf copy. 
Well as I said the other option is to keep the imSur as private variable or in a vector which is private in your class; Basically keep them around till the destruction of the class.

> I'm not leaking memory because it's about 2 tiny images 18x18 pixels each. Technically you are leaking :p

Anyway. This is beating a dead horse. I am glad I found another experienced(as it seems) Gtkmm developer here.

---

