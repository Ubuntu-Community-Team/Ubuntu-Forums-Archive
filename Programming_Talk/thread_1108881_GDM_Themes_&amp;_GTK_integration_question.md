---
title: "GDM Themes &amp; GTK integration question"
date: 2009-03-28
forum: Programming Talk
---

### Post by skotos on 2009-03-28
I am developing a few GDM themes that I am going to publish since they are almost finished, but I have a few issues I would like to solve in order to have them consistently look.
My recent discover took me to look at a *Theme/gtk-2.0/gtkrc* I might customize for the theme, but I am not a GTK expert/developer, thus my questions follow.
[LIST=1]
[*]When I use the face browser I can easily change the background color (an image can do the trick), and the background color of the face as well as the username background color (two XML options are available), but - if I need to change the foreground color for the displayed username as well as the selected image and username background color I have just discovered that is strictly related to GTK. How can the *Theme/gtk-2.0/gtkrc* be changed in order to set these two values?
[*]As for question one, changing the desktop theme can change the GDM theme behavior by providing sometimes a dark actions/options/language/sessions menu and sometimes a bright one depending - probably, on how the desktop theme has been set/configured. Where are these values stored or how can they be stored with, for instance, a default font size, too?
[/LIST]
If I solved these issues, I definitely would get the exact look I am looking for.
Any help might be greatly appreciated. I have checked the Ubuntu *Human List* theme and I have learned a lot of interesting hacks, but I still cannot find the solution, though it might be probably the best undocumented source.

---

### Post by skotos on 2009-03-30
Bumping with some more info.

Digging up the undocumented and my unknowns...

I can now specify the style inside *gtkrc* for some classes:

```
class "GtkWidget"  style "widget-style"
class "GtkDialog" style "dialog-style"
class "GtkButton" style "button-style"
class "GtkRadioButton" style "radiobutton-style"
```and set a default font
```
style "global-style"
{
        font_name    = "Bitstream Vera Sans 10"
}
style "widget-style" = "global-style"
{
        # Whatever it needs to be set
}

```but still I haven't found the faces (aka *userlist*) gtk class: any idea on how to get it?

---

