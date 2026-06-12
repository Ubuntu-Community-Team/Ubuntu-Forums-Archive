---
title: "Why do we need RGBA?"
date: 2009-04-14
forum: Programming Talk
---

### Post by ElTimo on 2009-04-14
I'm confused as to why rounded menu corners requires rgba support. For one, Metacity can do rounded corners without compositing or rgba (via the X11 SHAPE extension, I believe), and Qt can do it as well. My question is this: why can't we just use the SHAPE extension on our menus to round the corners? Is there something that Qt does that GTK can't do?

---

### Post by rushmobius on 2009-04-14
While you can do rounded corners without RGBA, the A for alpha allows for smoother edges on curved surfaces so they don't look so jagged.

It also allows for partial transparency for things like shadows.

---

### Post by Can+~ on 2009-04-14
Have you used a graphic tool?

Try creating a soft-rounded corner without transparency, I mean, you'll en up with either colour or transparent, no middleground.

To illustrate:

Hard Edge (GIF):

[IMG]http://img.photobucket.com/albums/v517/CanXp/Diseno/hardedge.gif[/IMG] [IMG]http://img.photobucket.com/albums/v517/CanXp/Diseno/screenshot2.png[/IMG]

Soft Edge (PNG, Alpha channel):

[IMG]http://img.photobucket.com/albums/v517/CanXp/Diseno/softedge.gif[/IMG] [IMG]http://img.photobucket.com/albums/v517/CanXp/Diseno/screenshot1-1.png[/IMG]

---

### Post by ElTimo on 2009-04-15
Ah, so that's why Qt's corners look so weird. Theoretically, though, how would one go about implementing rounded corners without rgba support? I'm interested because there are exactly no apps that I use which make use of the Murrine engine's argb support, and i was looking to make a new GTK theme engine that could do rounded corners, since I don't usually like semitransparent windows, and i have compiz for shadows.

But just to make sure, it IS possible to do rounded menu corners without rgba?

---

### Post by moma on 2009-04-16
Gscreendump can add rounded corners to your screenshots and photos. It works fine with PNG-images, but with JPG-images the corners become black (not transparent). Is there any difference between PNG and JPEG images how they handle the "A" alpha-channel ?
[[img]http://bildr.no/thumb/390331.jpeg[/img]](http://bildr.no/view/390331)
The [script...]("http://code.google.com/p/gscreendump/source/browse/trunk/commands/command.lst") is probably not good enough.

---

### Post by tabibito on 2009-04-16
Well, JPEG doesn't support transparency at all. PNG in the other hand does.

---

### Post by hessiess on 2009-04-16
JPG is lossy, so it cannot even do chroma key transparency without a bunch of artifacts.

---

### Post by ibuclaw on 2009-04-16
RGBA is also needed if you want to add transparency to the **whole** window too, not just the borders.

ie: A terminal window with a transparent background. ;)

Also, afaik, RGBA allows smooth transparency, even when moving a window.

Take the following rudimentary example:
```

#!/usr/bin/perl
use strict;
use Glib qw/TRUE FALSE/;
use Gtk2 -init;
use Gnome2::Vte;

my $window = Gtk2::Window->new;
my $scrollbar = Gtk2::VScrollbar->new;
my $hbox = Gtk2::HBox->new;
my $terminal = Gnome2::Vte::Terminal->new;

$scrollbar->set_adjustment ($terminal->get_adjustment);

$window->add ($hbox);
$hbox->pack_start ($terminal, TRUE, TRUE, 0);
$hbox->pack_start ($scrollbar, FALSE, FALSE, 0);
$window->show_all;

$terminal->fork_command ('/bin/bash', ['bash', '-login'], undef,
                          $ENV{HOME}, FALSE, FALSE, FALSE);
$terminal->signal_connect (child_exited => sub { Gtk2->main_quit });
$window->signal_connect (delete_event => sub { Gtk2->main_quit; FALSE });

**$terminal->set_background_transparent(1);**
Gtk2->main;

```
Transparency is set, but when you move the window, it takes it's time to update/refresh itself. With the use of RGBA, this effect should be instant and will have a more visually appeasing look to it. [citation needed though, and a working example would be nice ;)]

> **ElTimo said:**
> Is there something that Qt does that GTK can't do?
Not really, the only differences between them are the language they are implemented in.

Qt is C++:
(Taken from Konsole)
```

/* Identified in object constructor */
,_blendColor(qRgba(0,0,0,0xff))
/*
...
...
*/
void Display::setOpacity(qreal opacity)
{
    QColor color(_blendColor);
    color.setAlphaF(opacity);
    _blendColor = color.rgba();
}

```
Whereas GTK is C:
(Taken from Gnome-Terminal)
```

static void
initialize_alpha_mode (TerminalWindow *window)
{
  TerminalWindowPrivate *priv = window->priv;
  GdkScreen *screen;
  GdkColormap *colormap;

  screen = gtk_widget_get_screen (GTK_WIDGET (window));
  colormap = gdk_screen_get_rgba_colormap (screen);
  if (colormap != NULL && gdk_screen_is_composited (screen))
    {
      gtk_widget_set_colormap(GTK_WIDGET (window), colormap);
      priv->have_argb_visual = TRUE;
    }
  else
    {
      priv->have_argb_visual = FALSE;
    }
}

```

As they say, there is more than one way to skin a cat.

Regards
Iain

---

