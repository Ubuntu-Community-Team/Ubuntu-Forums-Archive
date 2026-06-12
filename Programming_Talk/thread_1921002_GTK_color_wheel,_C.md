---
title: "GTK color wheel, C"
date: 2012-02-05
forum: Programming Talk
---

### Post by anewguy on 2012-02-05
First off, I'm not much in the way of programming in C - I like it, it's just I've been gone from it for so long that I don't understand what the simplest of things are saying anymore.

I'm writing a program to help some people out with something dealing with gnome shell, and I need to be able to display color selection then "get" what was selected.  The same with fonts.  GTK has all the wonderful tools to do it, and I wrote something using C and GTK a couple of years ago - using Windows, push buttons, etc., but never selection tools like this.  I look on line at the "tutorial" pages I have found don't really show someone dumb like me how to use them to make a working function - it just shows the definitions, and that's one of things I see and can't figure out.  So, it makes me frustrated at myself for not understanding after all these years.

So, could some one point me to a site or two that has real samples of these things - you know, a main window like I know how to do, where a user presses a button to go to another window where they select what they want to change, which it turn pops up the color or font change dialogs and they get the result back?

Usually once I seem something that shows the basics of how it is used in the real world I can take it from there.  It's just seeing it and trying to understand it first.

Thanks in advance!
Dave ;)

---

### Post by PaulM1985 on 2012-02-06
There are controls in the GTK library that allow for selecting colours, see here:
[http://developer.gnome.org/gtk/2.24/](http://developer.gnome.org/gtk/2.24/)

and here is a tutorial page showing how some of those things are used:
[http://www.gtk.org/tutorial1.2/](http://www.gtk.org/tutorial1.2/)

Paul

---

### Post by r-senior on 2012-02-06
The Zetcode GTK tutorial has a decent colour chooser example (right at the end of the page):

[http://zetcode.com/tutorials/gtktutorial/gtkdialogs/](http://zetcode.com/tutorials/gtktutorial/gtkdialogs/)

---

### Post by anewguy on 2012-02-06
Yeah, I can get it to show the selection wheel popup, but what I can't figure out is how to get the resulting color selection.  The tutorials I have found, including those you have pointed me to, all say to set up code to check the returned value for OK, and if it's OK they all show the same thing to get the color.  There's a couple of problems:  (1) the color selection popup that comes up doesn't HAVE an OK button (2) they all say to check the value using a gtk statement that includes "->colorsel".  I have colorsel defined as shown, yet it won't compile because it says it's not of member of that GTK function.

So, I have a color wheel - figure it will be easy enough to set it to a default color prior to the call - you can spin around to select a color, change the RGB, etc., values but no "OK" button.  With the problem with the colorset gdk color item in the get color statement, I have no way to see what the color is that was selected.

Can't make heads or tails of the whole mess.

Thanks!
Dave ;)

---

### Post by r-senior on 2012-02-07
Are you creating this with GTK3?

I just took that Zetcode example and it works OK when compiled against GTK2:

```
gcc -o colorSelect colorSelect.c `pkg-config --libs --cflags gtk+-2.0`
```

But it won't compile against GTK3. I dug around in the [GTK3 documentation](http://developer.gnome.org/gtk3/stable/index.html) and came up with the following modification to the select_font function to make it work with GTK3. (I know ... it should probably be select_color, but that's what it is in that example).

```
void select_font(GtkWidget *widget, gpointer label)
{

  GtkResponseType result;
  GtkColorSelection *colorsel;

  GtkWidget *dialog = gtk_color_selection_dialog_new("Font Color");
  result = gtk_dialog_run(GTK_DIALOG(dialog));

  if (result == GTK_RESPONSE_OK)
  {

    GdkColor color;
[COLOR="Green"]    GtkWidget *colorSelection;

    colorSelection = gtk_color_selection_dialog_get_color_selection(
	GTK_COLOR_SELECTION_DIALOG(dialog));

    gtk_color_selection_get_current_color(GTK_COLOR_SELECTION(colorSelection), &color);
[/COLOR]
    gtk_widget_modify_fg(GTK_WIDGET(label),
        GTK_STATE_NORMAL,
        &color);
  } 

  gtk_widget_destroy(dialog);
}
```

Compiled with this:

```
gcc -o colorSelect colorSelect.c `pkg-config --libs --cflags gtk+-3.0`
```

... and it works OK. My GTK programming is very rusty but I think that's correct. The "OK" button appears to have changed to "Select".

I guess with GTK3 being relatively new, a lot of examples out there are going to need converting.

---

### Post by anewguy on 2012-02-18
I've been using the online GTK 3 documents themselves.

Normally the call returns a large hex string - a minimum of 4 characters each for the red, green and blue values, plus there is the alpha (opacity) value.  I'm able to get the color, convert it to a string and pull out the 2-character values, and I also could just use GdkColor->RR, etc..  The normal colors I've got covered.  What I can't figure out for the life of me is how to use the alpha value, with a range of 65000+, to come up with the fractional value that things like color rrggbbaa strings require - the valu from 0 to 1.  I also don't know how to convert that value back to the large alpha value.  It sounds crazy, but I really need to be able to do that.

I also am having trouble (again, since GTK3) setting background and foreground colors on a gtk label.  Doing so makes no difference to what is visible on the screen.

EDIT:  I mispoke - it's not a gtk label, it's a gtkbutton with label.  From what I've found, I have to modify the base color when it's a btkbutton with text.  I modified the code for that, and still nothing changes on the screen.

Thanks!
Dave ;)

---

