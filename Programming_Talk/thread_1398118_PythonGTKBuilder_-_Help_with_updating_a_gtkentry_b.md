---
title: "Python/GTKBuilder - Help with updating a gtkentry box..."
date: 2010-02-04
forum: Programming Talk
---

### Post by danbishop88 on 2010-02-04
Hopefully this is quite simple, but I've only been using Python for three days so far...

Basically I have a class (Gui) that controls the gui, I also have another class, in a module called clipboards.py, that access the clipboard. I want to be able to update a GTKEntry box using a def in the gui class, but to do this, I have to create a new instance of the Gui class and so a new, identical copy, of the gui spawns.

Everytime the clipboard changes, I get a new icon in the notification area, linked to a new instance of the gui...

Perhaps there is something fundamentally wrong with the way I've coded this? I'd really like to keep things as separate as possible though.

The following is the main file I run to start the program:

```
#!/usr/bin/env python
import ui
import clipboards

if __name__ == '__main__':
    startmonitoring = clipboards.linuxclipboard()    
    app = ui.Gui()
    app.startgui()

```

This is ui.py:

```
#!/usr/bin/env python
import gtk
import config

class Gui(object):
    #This bit fires up the GUI    
    def startgui(self):
        try:
            gtk.main()
        except KeyboardInterrupt:
            pass

    #Code for quitting the program
    def quit(self):
        gtk.main_quit()

    #Provides the necessary information for glade file and status icon locations
    def __init__(self):
        self.builder = gtk.Builder()
        try:
            gtk.destroy()
        except:
            print "nope"
        self.builder.add_from_file("ViciousLex.glade")
        self.builder.connect_signals(self)
        #Set status icon    
        self.statusIcon = gtk.StatusIcon()
        self.statusIcon.set_from_file("icons/lex14.png")
        self.statusIcon.set_visible(True)
        self.statusIcon.set_tooltip("Lex - A global dictionary")
        #Connect status icon left click to activate dictionary window
        self.statusIcon.connect("activate", self.activate_dictionary_window)
        #Connect status icon right click to activate popup menu
        self.statusIcon.connect("popup_menu", self.popup)
        self.load_preferences()

    #This code is used to toggle the visibility of any given window
    def toggle_visibility(self, widget):
        widget_name = self.builder.get_object(widget)
        #Check whether window is currently invisible
        if widget_name.get_property("visible") == 0:
            #if so, show it        
            widget_name.show()
        else:
            #if not, hide it
            widget_name.hide()

##############################
#STATUS ICON INTERACTION CODE#
##############################

    #Toggle visibility of dictionary window when status icon is clicked
    def activate_dictionary_window(self, widget, data=None):
        dictionary_window = self.builder.get_object('dictionary_window')
        #Check to see if dictionary window is already visible
        if dictionary_window.get_property("visible") == 0:
            #if not, show it        
            dictionary_window.show()
        else:
            #if so, hide it
            dictionary_window.hide()

    #Handle right click on status menu to activate Popup menu
    def popup(self, button, widget, time, data=None):
        status_icon_menu = self.builder.get_object('tray_icon_menu')
        #Check to see if dictionary window is already visible
        status_icon_menu.popup(None, None, None, 3, time)

    ####################
    #POPUP MENU ACTIONS#
    ####################

    #Code for quit button.
    def on_quit_activate(self, widget):
        self.quit()

    #Code for show dictionary.
    def on_show_activate(self, widget):
        self.toggle_visibility('dictionary_window')

    #Code for show preferences
    def on_preferences_activate(self, widget):
        self.toggle_visibility('preferences_window')
    
    #Code for about box
    def on_about_activate(self, widget):
        about = gtk.AboutDialog()
        about.set_program_name("Lex")
        about.set_version("1.5")
        about.set_copyright("Copyright 2010 Dan Bishop")
        about.set_comments("Lex is a powerful, multilingual dictionary.")
        about.set_website("http://www.danbishop.org")
        about.set_authors("Dan Bishop <dan@danbishop.org>")
        about.set_logo(gtk.gdk.pixbuf_new_from_file("icons/lexlogo.png"))
        about.run()
        about.destroy()

###################
#DICTIONARY WINDOW#
###################
    def update_search_entry(self, text):
        search_entry = self.builder.get_object('search_entry')
        search_entry.set_text(text)
    ###########################
    #DICTIONARY WINDOW ACTIONS#
    ###########################
    def on_preferences_button_clicked(self, widget):
        self.toggle_visibility('preferences_window')

    def on_dictionary_window_delete_event(self, widget, data=None):
        self.toggle_visibility('dictionary_window')
        return 'TRUE'

####################
#PREFERENCES WINDOW#
####################
    ################################
    #PREFERENCES WINDOW LOAD VALUES#
    ################################
    #This function is called on startup to set GUI elements to match those stored in the config file.
    def load_preferences(self):
        #This sets the language from combobox        
        language_from = self.builder.get_object('language_from')
        try:
            language_from_value = config.load_value_from_config('Languages', 'language from')    
            language_from.set_active(int(language_from_value))    
        except:
            language_from.set_active(0)
            print "No setting for 'Language to translate from' found: using default."
        
        #This sets the language to combobox        
        language_to = self.builder.get_object('language_to')
        try:
            language_to_value = config.load_value_from_config('Languages', 'language to')    
            language_to.set_active(int(language_to_value))    
        except:
            language_to.set_active(1)
            print "No setting for 'Language to translate to' found: using default."

        #This sets the state of the monitor clipboard checkbox
        clipboard_checkbutton = self.builder.get_object('watch_clipboard_checkbutton')
        try:
            clipboard_checkbutton_value = config.load_value_from_config('Behaviour', 'monitor clipboard')
            clipboard_checkbutton.set_active(int(clipboard_checkbutton_value))    
        except:
            clipboard_checkbutton.set_active(1)
            print "No setting for 'monitor clipboard' found: using default."

        #This sets the state of the show notifications checkbox
        show_notifications_checkbutton = self.builder.get_object('show_notifications_checkbutton')
        try:
            show_notifications_checkbutton_value = config.load_value_from_config('Behaviour', 'show notifications')
            show_notifications_checkbutton.set_active(int(show_notifications_checkbutton_value))    
        except:
            show_notifications_checkbutton.set_active(1)
            print "No setting for 'show notifications' found: using default."
    ############################
    #PREFERENCES WINDOW ACTIONS#
    ############################
    def on_preferences_window_delete_event(self, widget, data=None):
        self.toggle_visibility('preferences_window')
        return 'TRUE'

    def on_language_from_changed(self, widget):
        language_from = self.builder.get_object('language_from')
        language_from_name = language_from.get_active_text()
        language_from_value = language_from.get_active()
        print 'Changed language to translate from: ' + str(language_from_value)
        config.save_value_to_config('Languages', 'language from', language_from_value)

    def on_language_to_changed(self, widget):
        language_to = self.builder.get_object('language_to')
        language_to_name = language_to.get_active_text()
        language_to_value = language_to.get_active()
        print 'Changed language to translate to: ' + str(language_to_value)
        config.save_value_to_config('Languages', 'language to', language_to_value)

    def on_watch_clipboard_checkbutton_toggled(self, widget):
        clipboard_checkbutton = self.builder.get_object('watch_clipboard_checkbutton')
        clipboard_checkbutton_value = clipboard_checkbutton.get_active()
        print 'Monitor clipboard: ' + str(clipboard_checkbutton_value)
        config.save_value_to_config('Behaviour', 'monitor clipboard', int(clipboard_checkbutton_value))

    def on_show_notifications_checkbutton_toggled(self, widget):
        show_notifications_checkbutton = self.builder.get_object('show_notifications_checkbutton')
        show_notifications_checkbutton_value = show_notifications_checkbutton.get_active()
        print 'Show notifications: ' + str(show_notifications_checkbutton_value)
        config.save_value_to_config('Behaviour', 'show notifications', int(show_notifications_checkbutton_value))

        
```

And finally, this is clipboards.py:

```
#!/usr/bin/env python
import gtk
import ui

class linuxclipboard(object):

    def __init__(self):
        self.clipboard = gtk.clipboard_get(gtk.gdk.SELECTION_PRIMARY)
        #gobject.timeout_add(1500, self.fetch_clipboard_info)
        self.clipboard.connect("owner-change", self.clipboard_text_received)
        return

    def read_clipboard(self):
        clipboard_text = self.clipboard.wait_for_text(self)
        return clipboard_text

    #signal handler called when the clipboard returns text data
    def clipboard_text_received(self, clipboard, text):
        clipboard_text = clipboard_text = self.clipboard.wait_for_text()
        print "Searched for: " + str(clipboard_text)
        return clipboard_text
```


I REALLY do appreciate any and all help people are willing to give! Thanks in advance :)

---

### Post by danbishop88 on 2010-02-04
Solved it :D (Thanks to my friend Alex Williams)

lex.py:
```
import ui
import clipboards

if __name__ == '__main__':
    app = ui.Gui()
    startmonitoring = clipboards.linuxclipboard(app)
    app.startgui()
```

clipboards.py:

```
import gtk
import ui

class linuxclipboard(object):

    def __init__(self, appref):
        self.clipboard = gtk.clipboard_get(gtk.gdk.SELECTION_PRIMARY)
        #gobject.timeout_add(1500, self.fetch_clipboard_info)
        self.clipboard.connect("owner-change", self.clipboard_text_received)
        self.app = appref
        return

    def read_clipboard(self):
        clipboard_text = self.clipboard.wait_for_text(self)
        return clipboard_text

    #signal handler called when the clipboard returns text data
    def clipboard_text_received(self, clipboard, text):
        clipboard_text = clipboard_text = self.clipboard.wait_for_text()
        print "Searched for: " + str(clipboard_text)
        self.app.update_search_entry(clipboard_text)
        return clipboard_text
```

---

