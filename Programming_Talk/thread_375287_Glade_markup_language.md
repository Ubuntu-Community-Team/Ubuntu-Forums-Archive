---
title: "Glade markup language"
date: 2007-03-03
forum: Programming Talk
---

### Post by TheForkOfJustice on 2007-03-03
Can someone post a link to examples of markup codes you can use in Glade?

I specifically need the one that increases font size, but the more I have available, the better.

---

### Post by azazel00 on 2007-03-03
I'm not complete sure I understand your question.

Here is an example of a Glade file for a simple text editor:
[Simple Text Editor]("http://ruby-gnome2.sourceforge.jp/hiki.cgi?c=plugin;plugin=attach_download;p=Simple+Text+Editor;file_name=simple-editor.glade")

I suggest using Glade-3 rather than messing with the files manually. (Unless you have a load of time to waste.. :) )

Regards,
az

---

### Post by TheForkOfJustice on 2007-03-03
> **azazel00 said:**
> I'm not complete sure I understand your question.

Here is an example of a Glade file for a simple text editor:
[Simple Text Editor]("http://ruby-gnome2.sourceforge.jp/hiki.cgi?c=plugin;plugin=attach_download;p=Simple+Text+Editor;file_name=simple-editor.glade")

I suggest using Glade-3 rather than messing with the files manually. (Unless you have a load of time to waste.. :) )

Regards,
az

What I'm saying is that labels have the option of using markup language to change how they appear, like:

```
<b></b>
``` For [B]bold
[/B]```
<i></i>
``` for [I]italics
[/I]```
<u><u/>
```for _underscore_...and so forth

I was asking if there was a list out there of all possible codes that can be used in such a fashion, especially one that increases font size.

And yes, I do use Glade 3.  I wouldn't dare do it any other way :)

---

### Post by lnostdal on 2007-03-03
[http://developer.gnome.org/doc/API/2.0/pango/PangoMarkupFormat.html](http://developer.gnome.org/doc/API/2.0/pango/PangoMarkupFormat.html)

also take note of what is mentioned here about external sources if this is relevant for you: [http://developer.gnome.org/doc/API/2.0/gtk/GtkLabel.html#gtk-label-set-markup](http://developer.gnome.org/doc/API/2.0/gtk/GtkLabel.html#gtk-label-set-markup)

---

### Post by TheForkOfJustice on 2007-03-03
> **lnostdal said:**
> [http://developer.gnome.org/doc/API/2.0/pango/PangoMarkupFormat.html](http://developer.gnome.org/doc/API/2.0/pango/PangoMarkupFormat.html)

also take note of what is mentioned here about external sources if this is relevant for you: [http://developer.gnome.org/doc/API/2.0/gtk/GtkLabel.html#gtk-label-set-markup](http://developer.gnome.org/doc/API/2.0/gtk/GtkLabel.html#gtk-label-set-markup)

Thanks, I can even make sense of SOME of that ;P

Now, if I were only a good enough programmer to make heads of tails of the 'Signals' tab in Glade I'd be doing a lot better.

Do you have a link to a wiki or something that explains what a person can do in that section?  I'd like to know how to get a window to pop-up when I click a button (and many other things).

---

### Post by lnostdal on 2007-03-03
i prefer setting up signal-to-handler bindings in the source code itself because then i do not have to use Glade (or edit XML) if i want to change the name of the handler .. like this (this is from ubuntu-programming3.pdf, here: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) ):

```

void updateLabel(GtkWidget* widget, gpointer data){
...
}
...
  window1 = (GtkWindow*)glade_xml_get_widget(xml, "window1");
  spinbutton1 = (GtkSpinButton*)glade_xml_get_widget(xml, "spinbutton1");
...
  g_signal_connect(G_OBJECT(spinbutton1), "value-changed",
                   G_CALLBACK(updateLabel), NULL);
...
  g_signal_connect(G_OBJECT(window1), "delete-event",
                   G_CALLBACK(gtk_main_quit), NULL);

```

what the [`g_signal_connect']("http://developer.gnome.org/doc/API/2.0/gobject/gobject-Signals.html#g-signal-connect") calls do is set up "bindings" between signals that happen "on widgets" and which handlers to call when the signals happen, like this:

[list]
[*] when the ["value-changed"]("http://developer.gnome.org/doc/API/2.0/gtk/GtkSpinButton.html#GtkSpinButton-value-changed")-signal happens on the widget `spinbutton1', the handler or function `updateLabel' will be called (thus updating the sum in the widget `label1' .. see the complete code in ubuntu-programming3.pdf for more about this context)

[*] when the ["delete-event"]("http://developer.gnome.org/doc/API/2.0/gtk/GtkWidget.html#GtkWidget-delete-event")-signal happens on the widget `window1' (when the user closes the window), the handler or function `gtk_main_quit' is called
[/list]

handlers are just functions .. and you can use any function, both user-defined and built-in functions .. `updateLabel' is a user-defined function,  while `gtk_main_quit' is a function that already exists in gtk+ -- and both can be used as handlers for signals

..now, starting glade-3, creating a new window-widget then looking at the signals-pane you'll see that GtkWindow has both signals that are defined in the GtkWindow-class itself and its superclasses .. so it inherits both properties and signals from it's superclasses (or "superwidgets") and you can use any of them for your GtkWindow-widget

if you for instance want a modal popup dialog to appear with the message "Are you sure you want to quit?" when the user tries to close the main window, the signal you are after is "delete-event" from the GtkWidget-subtree (in glade this) .. basically what you do is simply type in the name of what handler (function which you'll later define in your code if you've not already done so) it should call when that signal happens where it says "type the signal's handler here"

imagine you have this code:

```

void askForQuitConfirmation(GtkWidget* widget, gpointer data){
 // code to popup a modal dialog and take action accordingly based on users answer
}

```

..what the glade-signal-thingy does for you is only setting up this:

```

  g_signal_connect(G_OBJECT(window1), "delete-event",
                   G_CALLBACK(askForQuitConfirmation), NULL);

```

..and you trigger libglade to do this by calling [http://developer.gnome.org/doc/API/libglade/gladexml.html#GLADE-XML-SIGNAL-AUTOCONNECT](http://developer.gnome.org/doc/API/libglade/gladexml.html#GLADE-XML-SIGNAL-AUTOCONNECT)

very simple :)

---

### Post by TheForkOfJustice on 2007-03-03
> **lnostdal said:**
> 
very simple :)


Heh, for someone who does this often, yes it is :D

Well, we all have to start somewhere (hacking may way through the terminology is hard enough).

---

