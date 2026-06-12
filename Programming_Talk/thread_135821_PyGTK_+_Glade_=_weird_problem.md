---
title: "PyGTK + Glade = weird problem"
date: 2006-02-24
forum: Programming Talk
---

### Post by sapo on 2006-02-24
Hi all, i ve started learning pygtk with glade, i m just making some test stuff. but i got some problems with simple things.

I designed 2 windows on glade, then exported it and loaded in the python script, the second window is hidden by default, then i wrote a function to show it up, ok it shows, them i wrote another function to hide it.. ok it hides...

But in the second time i show the window.. the window appear EMPTY, with just the title and NOTHING inside.. here is my code:

```
#!/usr/bin/python
# -*- coding: ISO8859-1 -*-

import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade

class main:
    def __init__(self):
        self.principal = gtk.glade.XML("scc.glade")
        self.w_cadcli = self.principal.get_widget("w_cadcli")
        dic = {"on_principal_destroy" : self.DestroyFunction,
               "on_w_cadcli_destroy" : self.hide_window,
               "on_cadcli_activate" : self.cad_cli}
        self.principal.signal_autoconnect(dic)
        principal = self.principal.get_widget("principal")
        principal.set_position(gtk.WIN_POS_CENTER)
        gtk.main()

    def DestroyFunction(self,obj):
        gtk.main_quit()

    def cad_cli(self,obj):
        self.w_cadcli.show()
        
    def hide_window(self,event):
        self.w_cadcli.hide()


if __name__ == '__main__':
    main()
```

Can anyone please help me? i was asking about it in the python irc channel, but got no luck solving it..

thanx in advance

---

### Post by Retrix on 2006-02-24
This one bit me as well when I first started with PyGTK. You basically need to add a 'return True' line at the end of the hide_window method to stop the window from being destroyed (only hidden).

More information [here]("http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq10.021.htp"). (The rest of the PyGTK FAQ is also a very good read).

-Sam

---

### Post by sapo on 2006-02-24
I did it, but still it doesnt work :( omg

---

### Post by WelterPelter on 2006-02-24
[comp.lang.python]("http://groups.google.com/group/comp.lang.python")  is where I go with these sorts of questions. Usually instant answers.

---

### Post by sapo on 2006-02-24
Man.. this is pissing me off, i rewrote an example by hand, take a look here:

```
#!/usr/bin/python
# -*- coding: ISO8859-1 -*-

import pygtk
pygtk.require("2.0")
import gtk

class main:
    def  __init__(self):
        #Create two windows
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.new_window = gtk.Window(gtk.WINDOW_TOPLEVEL)

        self.window.connect("delete_event", self.destroy)
        self.new_window.connect("delete_event", self.show_hide_janela)

        #Destroy events
        self.window.connect("destroy", self.destroy)
        self.new_window.connect("destroy", self.show_hide_janela)        

        self.window.set_border_width(10)
        self.new_window.set_border_width(10)        

        #Two buttons, one for each window
        self.button = gtk.Button("Show hide Window")
        self.button2 = gtk.Button("Damit!")        
        #action for the click action on the buttons
        self.button.connect("clicked",self.show_hide_janela)
        self.button2.connect("clicked",self.show_hide_janela)        

        #add the buttons to thw windows
        self.window.add(self.button)
        self.new_window.add(self.button2)

        #Show both buttons and just the first window
        self.button2.show()
        self.button.show()
        self.window.show()

        gtk.main()
    def show_hide_janela(self,obj):
        #if the second window is open hide it, if dont show it
        if self.new_window.get_property("visible") == True:
            self.new_window.hide()
        else:
            self.new_window.show()
        return True
    
    def destroy(self,*args):
        gtk.main_quit()

        
main()

```

This actually shows and hides the second window when i click the button, but when i click on CLOSE on the second window, the next time i show it up, it opens empty, without the button.

I ve tried a lot of things but cant find a way to fix this :(

---

### Post by psychicdragon on 2006-02-25
Hey sapo,

Take a look at this: 
[http://pygtk.org/pygtk2reference/class-gtkwidget.html#signal-gtkwidget--delete-event](http://pygtk.org/pygtk2reference/class-gtkwidget.html#signal-gtkwidget--delete-event)

The delete-event signal creates a [gtk.gdk.Event]("http://pygtk.org/pygtk2reference/class-gdkevent.html") object, which you're not going to need in this case. Change the callback to look like this and your program should work correctly.
```
def show_hide_janela(self,obj, ev=None):
```

---

### Post by sapo on 2006-02-25
Thanx, i did it and it actually worked on the "handcoded" version, but in the glade version it didnt.

What could be wrong? 
Or is it a sign trying to say: "Stop using this rad crap and do it by hand!"?

---

### Post by psychicdragon on 2006-02-25
No, Glade is cool. I use it all the time.

I think in the Glade version, this should work...
```
def hide_window(self, widget, event):
```
If not post the glade file and I'll try it myself.

---

### Post by sapo on 2006-02-25
Ok, here is the glade version and the last code i wrote.. i cant see why this doesnt work omg

I attached the .py and the .glade files, hope you can see whats wrong. :-k

---

### Post by psychicdragon on 2006-02-25
Whoops, I'm stupid. I didn't read the code properly.

Basically, you need to change the signal from "destroy" to "delete-event" because you don't want to destroy the window, just hide it.

---

### Post by sapo on 2006-02-25
OMG IT WORKS!

Man.. i almost didnt sleep last night trying to make this thing works.. and it was THIS SIMPLE! thanx a lot.

Anyway, i just started to use glade cause i really love python and its simplicity, and at my work we are starting to make a new application for commercial porpuses, and i m trying to convince my boss to use python, thats why i m trying to learn glade.

Btw i have a question, you said you use glade all the time, the application we are about to make is going to have a LOT of windows, so how do you manage this on glade? loading THEM ALL in the startup isnt going to hang up the performance?

How is the best way to make these windows? to make another .glade file i need to make another project and them reload everything again, cause i didnt find any way to make a glade file for each window or something like that.

---

### Post by psychicdragon on 2006-02-25
You can use more than one glade file in a project, but glade is kind stupid about the way it manages projects so you'll have to move the .glade files around manually and delete a lot of .gladep files. You just have to create a project for each window and then when you've got all the windows made move glade files to a single directory.

There's a different program you can use to create glade files called gazpacho, that is more modern and has a nicer interface, but it doesn't seem to support all the widgets that glade-2 does. At least the version in Breezy doesn't.

I'm not the best person to ask about performance issues, most of the programs I've made using PyGTK + Glade have been smallish ones, with only a couple of windows. That said, a lot of large applications do use glade, look at how many glade files evolution uses:
```
/usr/share/evolution/2.4/glade
/usr/share/evolution/2.4/glade/e-timezone-dialog.glade
/usr/share/evolution/2.4/glade/e-delegate-dialog.glade
/usr/share/evolution/2.4/glade/ldap-config.glade
/usr/share/evolution/2.4/glade/contact-list-editor.glade
/usr/share/evolution/2.4/glade/proxy-login-dialog.glade
/usr/share/evolution/2.4/glade/contact-editor.glade
/usr/share/evolution/2.4/glade/e-table-field-chooser.glade
/usr/share/evolution/2.4/glade/gal-define-views.glade
/usr/share/evolution/2.4/glade/exchange-permissions-dialog.glade
/usr/share/evolution/2.4/glade/e-foreign-folder-dialog.glade
/usr/share/evolution/2.4/glade/alarm-list-dialog.glade
/usr/share/evolution/2.4/glade/gal-view-new-dialog.glade
/usr/share/evolution/2.4/glade/gal-categories.glade
/usr/share/evolution/2.4/glade/e-active-connection-dialog.glade
/usr/share/evolution/2.4/glade/e-table-config.glade
/usr/share/evolution/2.4/glade/mail-dialogs.glade
/usr/share/evolution/2.4/glade/e-attachment.glade
/usr/share/evolution/2.4/glade/mail-config.glade
/usr/share/evolution/2.4/glade/alarm-notify.glade
/usr/share/evolution/2.4/glade/proxy-add-dialog.glade
/usr/share/evolution/2.4/glade/eab-contact-commit-duplicate-detected.glade
/usr/share/evolution/2.4/glade/alarm-dialog.glade
/usr/share/evolution/2.4/glade/recurrence-page.glade
/usr/share/evolution/2.4/glade/junk-settings.glade
/usr/share/evolution/2.4/glade/exchange-delegates.glade
/usr/share/evolution/2.4/glade/e-table-config-no-group.glade
/usr/share/evolution/2.4/glade/e-send-options.glade
/usr/share/evolution/2.4/glade/exchange-folder-tree.glade
/usr/share/evolution/2.4/glade/smime-ui.glade
/usr/share/evolution/2.4/glade/fullname.glade
/usr/share/evolution/2.4/glade/task-page.glade
/usr/share/evolution/2.4/glade/goto-dialog.glade
/usr/share/evolution/2.4/glade/e-contact-print.glade
/usr/share/evolution/2.4/glade/schedule-page.glade
/usr/share/evolution/2.4/glade/filter.glade
/usr/share/evolution/2.4/glade/event-page.glade
/usr/share/evolution/2.4/glade/meeting-page.glade
/usr/share/evolution/2.4/glade/e-itip-control.glade
/usr/share/evolution/2.4/glade/eab-contact-duplicate-detected.glade
/usr/share/evolution/2.4/glade/exchange-change-password.glade
/usr/share/evolution/2.4/glade/cal-prefs-dialog.glade
/usr/share/evolution/2.4/glade/import.glade
/usr/share/evolution/2.4/glade/fulladdr.glade
/usr/share/evolution/2.4/glade/url-editor-dialog.glade
/usr/share/evolution/2.4/glade/task-details-page.glade
/usr/share/evolution/2.4/glade/proxy-listing.glade
/usr/share/evolution/2.4/glade/im.glade
/usr/share/evolution/2.4/glade/properties.glade
/usr/share/evolution/2.4/glade/gal-view-instance-save-as-dialog.glade
```
Keep in mind that when using gtk.glade.XML, you can specify a root widget to load from. It has to be a top-level widget like a window or popup-menu though.
For example:
```
widgets = gtk.glade.XML(glade_file, "main_win")
more_widgets = gtk.glade.XML(glade_file, "foo")
something = gtk.glade.XML(a_different_glade_file, "window")
```

---

### Post by psychicdragon on 2006-02-25
I should add, if you're planning to make a commercial program you should definately do some research into getting PyGTK applications running on Windows. Windows doesn't come with Python like most Linux distrobutions do :rolleyes:.

---

### Post by sapo on 2006-02-25
[QUOTE=psychicdragon]I should add, if you're planning to make a commercial program you should definately do some research into getting PyGTK applications running on Windows. Windows doesn't come with Python like most Linux distrobutions do :rolleyes:.[/QUOTE]
Thanx a lot about the glade tips.

And i already did my research and already have that little example running on windows, i m currently using on both linux and windows the following:

pygtk and kinterbasdb (firebird database)

I tested on windows and it runs perfectly without changed even one line of code, just installing gtk and pygtk was enough :)

I m trying to use python cause i can do multiplataform stuff and because is very easy and quick to write apps, delphi is a pain in the butt.

I tryied wxPython too, but the wxglade is too buggy, and i think that pygtk is far easier and have a loooooooot more documentation that wxPython.

---

### Post by amonlee on 2007-09-03
Thank you guys. 

Changing the signal to delete_event still not work for me. Any ideas? Help please.

---

### Post by amonlee on 2007-09-03
Sorry, I just fixed that problem.

I need a "return True" statement at the end of the hide function to make it work.

Again. Thanks a ton for you guys' great tips.


Best Wishes
amonlee

---

