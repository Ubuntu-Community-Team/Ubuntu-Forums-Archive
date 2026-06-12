---
title: "Stop Dialog from destroying."
date: 2009-09-10
forum: Programming Talk
---

### Post by alzaf on 2009-09-10
I am writing a dialog that gets called from a program to collect information. What I would like to do is the dialog will only be destroyed if the information is entered. Unfortunately, I can't figure out how to do and I'm not sure if dialogs behave in that way.

Apart from the main program repeatedly calling the dialog until the information is calling, can anyone think of a more neater solution?

I've put the code in a test program in the

```

#example  base.py

import pygtk
pygtk.require('2.0')
import gtk
import os.path

class Base:

   #*******************************************************************************************************************
   ## Callback function for the music collection search button. Set up a file Chooser Dialog to get user selected location
   ## and set the music collection entry widget text to selected location

   #  @param self The object pointer
   #  @param music_entry entry widget for containing the music collection folder

   #*******************************************************************************************************************
   def music_button_cp(self, widget, music_entry):
      music_fcd = gtk.FileChooserDialog("Select Music Collection Folder..",
                               None,
                               gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER,
                               (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                                gtk.STOCK_OPEN, gtk.RESPONSE_OK))
      music_fcd.set_current_folder(os.path.expandvars("$HOME"))
      music_fcd.set_default_response(gtk.RESPONSE_OK)
      response = music_fcd.run()
      if response == gtk.RESPONSE_OK:
         music_entry.set_text(music_fcd.get_filename())
      music_fcd.destroy()


   #*******************************************************************************************************************
   ## Callback function for the mp3 player search button. Set up a file Chooser Dialog to get user selected location
   ## and set the mp3 player entry widget text to selected location

   #  @param self The object pointer
   #  @param mp3_entry entry widget for containing the mp3 player folder

   #*******************************************************************************************************************
   def mp3_button_cp(self, widget,mp3_entry):
      mp3_fcd = gtk.FileChooserDialog("Select MP3 Player Mount Folder..",
                               None,
                               gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER,
                               (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                                gtk.STOCK_OPEN, gtk.RESPONSE_OK))
      mp3_fcd.set_current_folder("/")
      mp3_fcd.set_default_response(gtk.RESPONSE_OK)
      response = mp3_fcd.run()
      if response == gtk.RESPONSE_OK:
         mp3_entry.set_text(mp3_fcd.get_filename())
      mp3_fcd.destroy()

   #*******************************************************************************************************************
   ## Call back function for Continue button on dialog.
   #  @param self The object pointer
   #  @param widget The widget pointer
   #  @param dialog startup dialog widget
   #  @param music_folder entry widget for containing the music collection folder
   #  @param mp3_folder entry widget for containing the mp3 player folder

   #*******************************************************************************************************************
   def response_cb(self, widget, response_id, dialog, music_folder, mp3_folder):
   
      music_coll_folder = music_folder.get_text()
      mp3_player_folder = mp3_folder.get_text()

      correct_music_info = True
      correct_mp3_info = True
      if music_coll_folder != "":
         print "music_coll_folder=" + music_coll_folder
      else:
         correct_music_info = False
      if mp3_player_folder != "":
         print "mp3_player_folder=" + mp3_player_folder
      else:
         correct_mp3_info = False

      if correct_music_info == True and correct_mp3_info == True:
         dialog.set_default_response(gtk.RESPONSE_NONE)
      else:
         dialog.set_default_response(gtk.RESPONSE_CANCEL)
         message_str = "The following information is missing:\n\n"
         if correct_music_info == False:
            message_str = message_str + "* No music collection folder\n"
         if correct_mp3_info == False:
            message_str = message_str + "* No mp3 player folder\n"
         message = gtk.MessageDialog(None, gtk.DIALOG_MODAL, gtk.MESSAGE_ERROR, gtk.BUTTONS_OK, message_str)
         x = message.run()
         if x == gtk.RESPONSE_OK:
            message.destroy()


   #*******************************************************************************************************************
   ## Set up Startup dialog and run it to get folder of music collection and mp3 player
   #  @param self The object pointer

   #*******************************************************************************************************************
   def __init__(self):
      dialog = gtk.Dialog("First Time Setup", None, gtk.DIALOG_MODAL | gtk.DIALOG_DESTROY_WITH_PARENT, buttons=None )
      dialog.set_size_request(500, 130)
      dialog.add_button("continue ->", gtk.RESPONSE_ACCEPT)
      table = gtk.Table(2, 3, False)
      table.set_row_spacings(2)
      table.set_col_spacings(2)
      
      # values colx, coly, roxx, rowy
      label = gtk.Label("Music Directory")
      table.attach(label, 0,1, 0,1, gtk.SHRINK, gtk.SHRINK)
      label.show()
      label = gtk.Label("MP3 Player Folder")
      table.attach(label, 0,1, 1,2, gtk.SHRINK, gtk.SHRINK)
      label.show()
      music_entry = gtk.Entry()
      music_entry.set_max_length(50)
      table.attach(music_entry, 1,2, 0,1, gtk.FILL, gtk.FILL)
      music_entry.show()
      mp3_entry = gtk.Entry()
      table.attach(mp3_entry, 1,2, 1,2)
      mp3_entry.show()
      music_button = gtk.Button("Browse...")
      music_button.connect("clicked", self.music_button_cp, music_entry)
      table.attach(music_button, 2,3, 0,1, gtk.SHRINK, gtk.SHRINK)
      music_button.show()
      mp3_button = gtk.Button("Browse...")
      mp3_button.connect("clicked", self.mp3_button_cp, mp3_entry)
      table.attach(mp3_button, 2,3, 1,2, gtk.SHRINK, gtk.SHRINK)
      mp3_button.show()
   
      dialog.connect("response", self.response_cb, dialog, music_entry, mp3_entry)
      dialog.vbox.pack_start(table, True, True, 0)
      table.show()
      dialog.show()
      x = dialog.run()   
      if x == gtk.RESPONSE_NONE:
         dialog.destroy()

if __name__ == "__main__":
   base = Base()

```

---

### Post by steeleyuk on 2009-09-10
This is my go at fixing it, from what I can tell it works. As I tell everyone I try to help though, I'm no expert and it might not be what you wanted or there might be a better way to do it.

---

### Post by alzaf on 2009-09-10
Thanks for reply to me steeleyuk, that works!!

The dialog I am writing is to get details when the program I am writing first runs. 

I was hoping to run the dialog before the main window (gtk.main) comes up. It looks like it doesn't work that way. I'll have to amend my code to take account of it (the main window has a treestore which gets file names from the settings in the dialog box).

Edit: It's too late in the night, to think programming. The dialog will be run before the main window.

---

