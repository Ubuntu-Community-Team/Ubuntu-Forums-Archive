---
title: "Re-writing an old python app and need help"
date: 2007-01-07
forum: Programming Talk
---

### Post by rioghal on 2007-01-07
Here's what I am doing. I found a nice little pygtk app here:
[http://awesum.sourceforge.net/](http://awesum.sourceforge.net/)

I am learning python and pygtk at the moment and am using my new skills to re-write an app that I like. I originally had a bash script that prompted the user for a file and an expected md5 checksum and then compared the file with the checksum the user entered. I had been using it quite a bit until I found awesum at the above URL.

I have re-written a bit of the python script and the .glade file but I need one more thing to be able to make the GUI look better.
As you can see from the first attached screenshot, the original app uses an old GtkOptionMenu (which is depricated) and I'd like to replace it with two radio buttons, as seen in the second attached screenshot, to make the GUI look better. What I need is to learn how to detect which of the two radio buttons is selected so the app knows whether to use MD5 or SHA1 as the digest type.

How does one determine which radio button is selected?

Here is a bit of the code so you can see what the app is doing. The name of the widget I want to replace is 'csum_type' (I added the red color to the text), it's the one in the first screenshot that has 'MD5" in it:

```

    #Determine the correct algorithm
    history = gladeXML.get_widget("[COLOR=Red]csum_type[/COLOR]").get_history()
    if(history == 0):
        algorithm = "MD5"
    elif(history == 1):
        algorithm = "SHA"
    else:
        #Error
        raise "ERROR: csum_type out of range"

    #Get the filename
    filename = get_filename()

    if(filename != ""):
        if(do_checksum(filename, checksum, algorithm)):
            #Checksum verification successful
            msgdlg = gtk.MessageDialog(
                None,
                gtk.DIALOG_MODAL,
                gtk.MESSAGE_INFO,
                gtk.BUTTONS_CLOSE,
                "Checksum verification successful!"
                )
            msgdlg.run()
            msgdlg.destroy()
            gladeXML.get_widget("expected_csum").set_text("")
        else:
            #Checksum verification failed
            msgdlg = gtk.MessageDialog(
                None,
                gtk.DIALOG_MODAL,
                gtk.MESSAGE_ERROR,
                gtk.BUTTONS_CLOSE,
                "Checksum values do not match."
                )
            msgdlg.run()
            msgdlg.destroy()
            gladeXML.get_widget("expected_csum").set_text("")

    return


```
So, anyone want to teach me how to detect which radio button was selected? I'm betting it's something simple like:
```

gladeXML.get_widget("csum_type").get_[COLOR=Red]selected[/COLOR]()

```

---

### Post by xtacocorex on 2007-01-07
I have a Python/C++ code that has radio buttons in it.  I'm showing sections of it below that sets up all the widgets for the main GUI (made with Glade). The code may not look complete and I've done this because I cut out sections that don't matter to the radio button stuff.

The functions that work with the radio buttons are:
setChoiceTecplot
setChoiceICEM

The foilSave_activate function uses the two functions along with another one to save different file types.

This program isn't released, so you're the first person to see this code besides myself.  The C++ portion of it contains some novel airfoil generation techniques that I haven't quite figured out how to protect, so I've kept it hidden.

Hope this helps some.

[php]
                 self.foilChoiceTec = self.wTree.get_widget("foilChoiceTecplot")
        self.foilChoiceIcm = self.wTree.get_widget("foilChoiceICEM")

        # Create our dictionary and connect it
        dic = {    "on_foilWindow_destroy" : gtk.main_quit,
                      "on_foilViewer_expose_event" : self.foilPixmap_expose,
                   "on_foilAbout_activate" : self.foilAbout_activate,
                    "on_foilSave_activate" : self.foilSave_activate,
                   "on_foilQuit_activate" : gtk.main_quit,
          "on_foilGenerate_button_press_event" : self.foilCreate_wrapper,
           "on_foilMaxCLocScale_value_changed" : self.foilMaxCLoc_update,
               "on_foilCTCScale_value_changed" : self.foilCTC_update,
             "on_foilThickScale_value_changed" : self.foilThick_update,
                "on_foilChoiceTecplot_toggled" : self.setChoiceTecplot,
                   "on_foilChoiceICEM_toggled" : self.setChoiceICEM}
        self.wTree.signal_autoconnect(dic)
        
        # Set self.foilChoiceTec to be active
        self.foilChoiceTec.set_active(True)
        
    # foilSave_activate
    def foilSave_activate(self,widget):
        """ Open the Save Dialog """
        #self.foilSaveD = foilSaveDialog()
        #self.foilSaveD.run(self.statText,self.fType)
        if self.fType == "tecplot":
            self.fName =  self.foilName+"_tec.plt"
        elif self.fType == "icem":
            self.fName = self.foilName+"_icem.dat"
        self._foilWriteFile()
        
    # setChoiceTecplot
    def setChoiceTecplot(self,widget):
        """ Sets the filechoice to 'tecplot' when the radio button is 
            checked in it's favor """
        if widget.get_active():
            self.fType = "tecplot"
        else:
            self.fType = "icem"
        
    # setChoiceICEM
    def setChoiceICEM(self,widget):
        """ Sets the filechoice to 'icem' when the radio button is 
            checked in it's favor """
        if widget.get_active():
            self.fType = "icem"
        else:
            self.fType = "tecplot"
[/php]

---

### Post by rioghal on 2007-01-09
I have been told that this pygtk file is quite odd and to leave it alone until I have a better grasp of python.. sounds like good advice.

---

### Post by xtacocorex on 2007-01-09
Like I said, the file isn't complete and what I listed is just sections of it that deal with the radio button. 

The advice you were given about my code is probably good though.  The code I did was my first time doing pyGTK and I was using tutorials online and looking at the pyGTK documentation.

Here are the tutorial sites I have bookmarked:
[http://www.learningpython.com/](http://www.learningpython.com/)
[http://pygtk.org/pygtk2tutorial/index.html](http://pygtk.org/pygtk2tutorial/index.html)

---

