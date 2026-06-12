---
title: "Ok, I give up. Gtk programmers, help me!"
date: 2009-10-15
forum: Programming Talk
---

### Post by Keyper7 on 2009-10-15
Here's the background: I have a dream. A dream of integrating Conky seamlessly with Gnome Panel. To achive this dream, I'm trying to use gnome-swallow-applet.

Unfortunately, Swallower does not handle Conky transparency well. So I decided to peek at the code and discover why. It is only one file, attached to this post.

The following snipped caught my attention:

```

    case PANEL_PIXMAP_BACKGROUND:
        // This appears to be broken in Gnome 2.2!!!
        //style->bg_pixmap[0] = pixmap;
        //gtk_widget_set_style(ap->parentWidget, style);
        break;

```

Since years have passed since Gnome 2.2, I decided to give this commented code a shot and changed it to:

```

    case PANEL_PIXMAP_BACKGROUND:
        // This appears to be broken in Gnome 2.2!!!
        style->bg_pixmap[0] = g_object_ref(pixmap);
        gtk_widget_set_style(ap->parentWidget, style);
        break;

```

It was a good progress. Conky is now showing the panel as background! However, there is one problem: there seems to be a one-pixel border around the applet, displacing the background position by one pixel. This is not a problem when I use a solid color as a background (including semitransparent colors), but it's ugly when I use a background image. Attached is an example, with the Dust theme panel.

I researched high and low on to how to remove this one-pixel annoyance, but nothing worked. Can a Gtk guru around here help me in this issue?

---

### Post by Reiger on 2009-10-15
I am not a GTK code but since it sounds a wee bit familiar to other issues; I can give you some reply:

Does the swallower applet basically &#8216;swallow&#8217; a Window/Panel (by which I mean an application Window or panel) and re-position it as applet in the panel? If that is the case there may be an old border (window-border or panel border) interfering with the visuals you aim for: try to see if heavy-handed dis-abling of borders and similar decorations fixes the problem.

---

### Post by Keyper7 on 2009-10-15
Thanks Reiger. I didn't solve my problem yet, but discovered a few things.

It seems that the applet creates a GtkDrawingArea inside the PanelApplet widget and draws the swallowed window contents into it. Since PanelApplet is a GtkContainer, I can change its border width, and when I tried to increase the border width I discovered that the border goes **around** the one-pixel border I don't want to have. So it seems that this is actually a **padding** issue: there is undesired space between the PanelApplet border and its only child, the GtkDrawingArea.

---

### Post by Keyper7 on 2009-10-17
Bumping and hoping...

---

