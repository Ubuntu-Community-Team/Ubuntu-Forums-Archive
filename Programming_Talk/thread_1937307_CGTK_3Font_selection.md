---
title: "C/GTK 3/Font selection"
date: 2012-03-07
forum: Programming Talk
---

### Post by anewguy on 2012-03-07
Currently I'm working on an app using C and GTK 3 (and believe me, I'm far from "adequate" in either ;) ).  The portion I'm at now allows the user to select a font.  I currently have a gtk font button via gtk_font_button_new.  While I see the various fonts and such things as bold and/or italic as part of the font selection, and the font size, what I'd really like to do is have the user be able to select all of that separately - like in:

- font
- font size - font color - bold - italic - underline

as 2 lines on the screen. Actually setting up the font color, bold, italic and underline are easy buttons.  The font size needs to be in em's, and I'm not sure about setting that up.  I'd like a drop-down with the selections, and I could build that, but I'm not sure just exactly what the allowable sizes are that I should put in the drop-down.

Then there's the font itself.  I can get the font name fine, but what I don't seem to be able to do is turn off the showing of the size, etc..  I've used the show_style and show_size both to false - and indeed it has stopped what is shown in the button on the screen from showing style and size, but what I really need to do is stop the selection dialog provided by GTK from displaying the font size selector at the bottom of the screen.  Is this possible?  

If that is not possible, I supposed I could build my own drop-down font selector, but that seems like a needless expense (for me - remember I'm really not even "adequate" at C and GTK)  of a large amount of time and beginners' frustration.

I looked at extracting the size from the selection screen, but then you need to use Pango, and right now I can't make heads or tails of it at even the slightest little bit.

I also saw reference to using something like GtkFontDialog or some such thing instead.  Just trying to set up that button gives me a GTK run time error about trying to set something when the window is a parent already.  I looked through the docs and the net on that one and couldn't find anything to solve it.

I'm attaching a screenshot in case it helps visualize more what I'm doing and where I'd like it to be.

Thanks so much in advance!
Dave ;)

---

### Post by r-senior on 2012-03-07
GtkFontChooserDialog would give you control over the family, style and size. It's the standard way of getting a font selection and that's the approach I would take.

The gtk_font_chooser_dialog_new function takes a title and a parent window as its parameters. Did you specify your main window as the parent? Do you have other dialog windows displayed by the application and did you destroy them?

---

### Post by anewguy on 2012-03-07
> **r-senior said:**
> GtkFontChooserDialog would give you control over the family, style and size. It's the standard way of getting a font selection and that's the approach I would take.

The gtk_font_chooser_dialog_new function takes a title and a parent window as its parameters. Did you specify your main window as the parent? Do you have other dialog windows displayed by the application and did you destroy them?

That's the one I was having problems with - I have an opening window, which is hidden at the time because it opened a "Panel Options" Window called "panel_win1".  Since panel_win1 was the only visible screen at the time, and the one that has the button, I thought I needed to put panel_win1 as the window name on the font choose dialog.  That's when I get the error at run-time.  I never tried the name of the opening window, as I was thinking I needed the current active window - perhaps as I wrong about that ;)  I was hoping it would present a more "traditional" font selection/size selection/bold-italic-underline type of selection - but I did note in the docs that it uses the same function that I currently have the button defined for, so I hope that isn't an onimous sign ;)  I just want something similar to what you see even right here on the reply page in the forum for fonts - separate font, size, B I U, and color.  If I can get that all on 1 selection screen with the font chooser dialog it would be great!  Just that pesky little error - 1 I assume is just from my lack of knowlegde at this time ;)

Thanks for the help!  Look forward to your reply!

Dave ;)

---

### Post by r-senior on 2012-03-07
I have seen dialog windows chained like that in some applications but not tried it with GTK3. I assume you can and I assume you'd set the parent of the font selection dialog as your dialog.

I've just coded a font selection into a Python GTK3 application that I'm using to learn a bit about GTK3. I don't know if seeing that helps:

```
dialog = Gtk.FontChooserDialog('Select Font', self)
dialog.set_font(self.current_font)
response = dialog.run()
new_font = dialog.get_font()
dialog.destroy()

if response != Gtk.ResponseType.CANCEL:
    self.current_font = new_font

```

In this context, "self" is the main application window. The "current_font" is just a string like "Monospace 10". Python maps directly onto the GTK3 functions so you should be able to convert this into C quite easily.

---

### Post by anewguy on 2012-03-07
Hummmmmm......slightly different usage than what I've seen so far in the docs for C - I think I'll try a similar thing in C and see if it lets me get away with it!

Thanks!

Dave ;)

---

### Post by r-senior on 2012-03-07
I'm probably using the same GTK3 documentation via DevHelp. Python just maps directly onto the C functions with GTK3. So ...

```
dialog.set_font(font) -> gtk_font_chooser_set_font(font)
response = dialog.run() -> response = gtk_dialog_run(dialog)
new_font = dialog.get_font() -> new_font = gtk_font_chooser_get_font(dialog)
... and so on

```

Plus all those casting macros like GTK_WINDOW that I never got to grips with. Which is why you get to convert it back from Python. ;)

---

### Post by anewguy on 2012-03-08
Well, it appears maybe I'm doing something wrong in implementing the 2nd window.

In C, my "main" function defines the opening screen, which includes a button that says "Panel Options".  The signal handler for that button uses a callback function of "panel_optinos".

"panel_options" defines an entirely different screen, including other buttons.  The color buttons work - and they call a GTK color selection dialog.

When I make the font selection button define as:

```
     button4 = gtk_font_chooser_dialog_new("Select Panel Font Information",
                                           panel_win1);
```

and describe it's signal hanlder as:

```
     g_signal_connect (G_OBJECT (button4), "font-set",
                       G_CALLBACK (update_css_panel_font),
                       NULL);
```
(the "font-set" signal apparently isn't correct - need to change it)

with the idea that since it's a gtk_font_choose_dialog button it should work like the color buttons -> go through the font selectiong then return and follow my signal handler "update_css_panel_font".

The button and it's preceeding text description go on 1 line of the display - using a non-homogenous table:
```
     gtk_table_attach (GTK_TABLE(display_table), label3,0,1,4,5,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);
     gtk_table_attach (GTK_TABLE(display_table), button4,1,5,4,5,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);

```

This table attach generates the following:

```
(gscedit:27746): Gtk-WARNING **: Can't set a parent on a toplevel widget


```

I have put printf's in to trace where everything is happening.  It goes through all the remaining code for setting up the window "panel_win1" and reaches the end of the "panel_options" function - a RETURN statement.

Here in may be my mistake:  it has worked in the past doing the return - the 2nd screen shows, functions, let me exit back to the first, etc..  But when using the font_chooser_dialog_new I now get this error when it either processes the return or whatever actually happens with the return:

```
dave@asus-desktop:~/gnome_shell_css$ ./gscedit
define button4
button4 defined
This probably generates the font-set warning

(gscedit:27746): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `font-set' is invalid for instance `0x26648b0'
Got the font-set warning, eh?
Put button4 in display table

(gscedit:27746): Gtk-WARNING **: Can't set a parent on a toplevel widget

Finished putting button4 in display table
hide opening_window
show panel win1
hide objects not to be shown initially
done hiding objects
**
Gtk:ERROR:/build/buildd/gtk+3.0-3.2.0/./gtk/gtkcontainer.c:3312:gtk_container_propagate_draw: assertion failed: (gtk_widget_get_parent (child) == GTK_WIDGET (container))
Aborted
dave@asus-desktop:~/gnome_shell_css$ 

```

Note the final error:
```
Gtk:ERROR:/build/buildd/gtk+3.0-3.2.0/./gtk/gtkcontainer.c:3312:gtk_container_propagate_draw: assertion failed: (gtk_widget_get_parent (child) == GTK_WIDGET (container))
Aborted

```

I assume this has something to do with the similar warning generated when I try to add it to the display window (panel_win1) via the table.

But it also leaves me wondering, and I'll be danged if I can find reference to it anywhere on the net, am I handling the end of the function for the 2nd screen correctly, or does it somehow have to "run" gtk_main as well?

Any help on this entire mess would be greatly appreciated.  I've purposely kept things simple compared to what I would like to do because being away from things since 1994 has left me with the understanding of what I want to do internally, but my C is terribly rusty - it's like being a rookie, and GTK - well, that's new strange animal to me. ;)

Dave ;)

---

### Post by r-senior on 2012-03-08
> **anewguy said:**
> 
```
button4 = gtk_font_chooser_dialog_new("Select Panel Font Information", panel_win1);
```
This looks wrong to me. The gtk_font_chooser_dialog_new function returns a widget but it's a dialog window, not a button.

I was thinking that you'd declare a plain old button with "Change Font" on it, connect up the "clicked" signal to a handler and in the handler have the C equivalent of the code that I posted previously. That displays a dialog, waits for a response and grabs the newly selected font from the dialog.

However, I notice there is a also a GtkFontButton widget that shows the font family and size and this is probably what you were talking about originally. (Apologies, I'm still learning GTK3, just as much as you are).

I knocked together a quick example (in Python again). It's just calling those exact same C functions under the hood:

```
from gi.repository import Gtk

class MainWindow(Gtk.Window):

    def __init__(self):
        Gtk.Window.__init__(self, title='Test')

        # Set up the font button
        self.font_button = Gtk.FontButton()
        self.font_button.set_font_name('Liberation Mono 12')
        self.font_button.connect('font-set', self.on_font_set)

        # Layout the window with a grid
        grid = Gtk.Grid()
        grid.attach(font_button, 0, 0, 1, 1)
        self.add(grid)

    def on_font_set(self, widget):
        print self.font_button.get_font_name()

window = MainWindow()
window.connect('delete-event', Gtk.main_quit)
window.set_size_request(320, 240)
window.show_all()
Gtk.main()
```

This displays a GtkFontButton in a window, initialises it to a font and connects up the "font-set" signal. Not much else to do. The screenshots show this in action. When the dialog window selects a font, my on_font_set method gets called and prints the name of the selected font to the console.

So, based on your initial question:

> what I'd really like to do is have the user be able to select all of that separately - like in:

- font
- font size - font color - bold - italic - underline


Either the plain button and font chooser dialog would work, or the font chooser button that I've played with here (which displays the font chooser dialog automatically).

The thing you wouldn't have would be the colour. Those dialogs don't deal with colour. So you'd either have to have a custom dialog or just put a font button and colour button side by side on your settings dialog. The font button would show the font chooser dialog and the colour button would show the colour chooser dialog.

The errors you are getting stem from mixing up the font chooser button and font chooser dialog. If you follow the same pattern I've shown above for the font chooser button, it *should* work.

---

### Post by anewguy on 2012-03-08
What your screen shots show is what I get with what I was already using - in C:



button4 = gtk_font_button_new();
gtk_font_button_set_show_style(button4, FALSE);
gtk_font_button_set_show_size(button4, FALSE);  */

This creates the button.

And:

g_signal_connect (G_OBJECT (button4), "font-set",
 G_CALLBACK (update_css_panel_font),
 NULL);

sets up the callback.

The button works fine this way - the button shows on the screen, when you click it you get the same font selection things you show in your screen prints.  Once the selection is made, the selection dialog closes and control is passed to my callback function to do what I want with the results.

Pretty simple.  Since that's what you get going the other way, there's no use in my pursuing it any further and just sticking with what I've got until I sort out how to do it on my own.

But I'd really like the font names/families to be selectable in 1 box without the size selection being there or the attributes like bold, etc., being there.  I then want a separate pull-down for the font size, another for the font color, and 3 separate buttons for bold, underline and italic.   If you look at the options available in posting a message here, you'll see what I mean:

"Fonts" is a pull down for just font names
"Sizes" is a pull down for just font sizes
"A" is a pull down for just font colors
and finally, on the 2nd line, B,I and U.

This is how I want to be able to present things.  Going by other dialogs, including combobox selection, I would have thought GTK would have a configurable interface for this as well. 

It looks like I need to read on font list and build my own combobox for that, then do the same for font sizes, though I'm not sure if there is a list somewhere I can read of sizes.  Color would just be a color button.  Bold, italic and underline are simple.  So, I may have more work ahead of me trying to build my own interface.

Dave ;)

---

### Post by anewguy on 2012-03-08
Forgot my attachments - 1st shows the panel options screen after the opening window was hidden, with the mouse on the font button.  The 2nd shows what I get when I click that button.  While not demonstrable on the screen, when I've made my selection it does go to my callback function where I store internally what was selected.

This entire program is updating a CSS file, so I always store things in a format ready for writing to that file.

---

### Post by r-senior on 2012-03-09
> **anewguy said:**
> But I'd really like the font names/families to be selectable in 1 box without the size selection being there or the attributes like bold, etc., being there.  I then want a separate pull-down for the font size, another for the font color, and 3 separate buttons for bold, underline and italic.
It sounds more and more like you need to make your own custom font dialog.

I guess another thing is that for CSS you ought to provide relative-sized fonts, i.e. percentages and names like small, medium, large. Things you won't get from the standard GTK font dialogs:

[http://www.w3.org/TR/CSS21/fonts.html#font-size-props](http://www.w3.org/TR/CSS21/fonts.html#font-size-props)

To list fonts, you'll need Pango. Basic steps appear to be getting a PangoContext with gtk_widget_get_pango_context then using pango_context_list_families.

---

### Post by anewguy on 2012-03-09
I was afraid of that.......I took a quick peek at Pango for the string conversion of the gtk font selection, and I've got to say right now it might as well be some other language as it makes no sense to me.  So, now I have to decide if I REALLY want to go to the hassle of learning that for just one volunteer project, or if I just want to give up on the project.  Seems like everything I'm doing for it is a hurdle, when it seems like such things should be easily done.

Thanks again!

Dave ;)

---

### Post by r-senior on 2012-03-10
Don't give up! The Pango internals for working out string lengths do look complex but listing fonts is just those two functions and doesn't look too bad.

I've played around with different ways of creating GTK3 applications and, despite C being my strongest language behind Java, I didn't have the stomach for C and GTK3. I found it like swimming in mud. I imagine there's a point where you become fluent but I found it difficult.

I tried C++/gtkmm3 and that was better but I've ended up teaching myself Python. The gobject repository bindings for Python take some getting used to and the documentation is sparse but I'm learning that route because I find it the most productive. I find I can concentrate on the application more.

---

### Post by anewguy on 2012-03-11
I think part of my problem is I never learned the object-oriented approach to programming.  Some languages like Java, python, etc., haven't made a lot of sense to me yet and I think it's because I don't have that toolbox of knowledge.  Keep telling myself I'll learn it, but at 55+ and not having worked since 1996 (or maybe it was 1994 - I can't even remember anymore), I just haven't been able to push myself there yet.  Many, many years ago while working I took a course in C++, but it turned out to be just things likes cin and cout - nothing on OOP.  So, I take a 2nd class in C++ and what happens?  They assume you already knew OOP and where familiar with all of the concepts of inheritance, etc..  Heck, I don't even know the structure of an OOP language, let alone the concepts.

This GTK crap is killing me.  Things should be quite easy to do, but they just aren't.  I even went so far as to try Gambas, and, well, there must be a secret there - I know Visual Basic but this Gambas was just another mystery to me.

I HATE giving up on things, especially when it's just a lack of knowledge, but the learning curve on this crap is horrendous.

---

### Post by anewguy on 2012-03-15
I'm going to close this thread, and try a different approach on the forum to see if i can get more help.

Thank you!!

Dave ;)

---

