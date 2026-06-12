---
title: "GTK troubleshooting..."
date: 2009-09-30
forum: Programming Talk
---

### Post by J V on 2009-09-30
So I'm having trouble with GTK/Glade (C isn't my language of choice so I may be missing something simple)

As this thread inevitably fills up, I will keep the "probleme de l'heure" on this post so people know what the hell is going on :)

Ok, my first few problems...

[LIST]
[*]Getting images to work
[*]How do I stop a window being completley destroyed? I want to destroy the variable, but keep the data in the gtk.builder object... is this possible? Should I just hide all the windows rather than destroy them? What happens if say a video player is running in a window that is hidden, won't that suck up memory?
[/LIST]
Gtk is so much better than .NET, I can see that already, but the documentation seems a bit thin...

---

### Post by PmDematagoda on 2009-09-30
Please post the code, it's too difficult to figure out what you're doing wrong otherwise.

---

### Post by J V on 2009-09-30
There is no code yet (feels ashamed), I have written a few titbits, but its basicly just glade at the moment...

Glade won't let the progress bar go over 90%, I can't see any way to collapse certain parts of tables, and the images won't show properly...

The images are stuck in a folder images, but glade copies them to a pixbuff folder on the same level, so I woulden't know whats wrong with them... They show up fine in the glade window but don't in the main app...

Edit: About the collapsing thing, the notebook has something similar in that its able to change a section of the GUI instantly, except I just want to completely hide (Ie, no big blank hole in the form) the widgets

---

### Post by days_of_ruin on 2009-09-30
Post the little code that you do have. Also upload the glade file. 

Here are some very good tutorials on using glade:
[http://live.gnome.org/Glade/Tutorials]("http://live.gnome.org/Glade/Tutorials")

---

### Post by J V on 2009-10-01
Thanks, been to the tutorials (skimmed over them a bit)

[http://www.2shared.com/file/8154010/8dc28b83/osrs.html](http://www.2shared.com/file/8154010/8dc28b83/osrs.html)

Glade 2 btw... (Just realised theres a glade 3, getting it now) The images show up fine in glade but don't in the compiled program... (Edit: don't show up in glade 3...)

I'm going with gtkpython, but I never really "got it" with OO, so how would I make the about window popup when the buttons pressed? Sorry this is just not working, I hate OO :/

Latest problem: I can't instance a class in a module... It says that "global name 'callback' is not defined"... I presume tons of people have used classes from modules, but I don't know where to find that stuff :P

---

### Post by J V on 2009-10-03
Ok, little recap...

Need the images to work (Compiler is showing where they are expected to be, but I want them to be in a subdir, however that option under glade preferences keeps resetting...)

Need to be able to collapse certain areas (For example, the taskbar needs to be practically non-existant until someone hits alt)

Need to load the glade file in PyGTK without it automatically popping up all the windows at once...

---

### Post by SledgeHammer_999 on 2009-10-03
> **J V said:**
> Ok, little recap...

Need the images to work (Compiler is showing where they are expected to be, but I want them to be in a subdir, however that option under glade preferences keeps resetting...)

mmm, why don't you provide some sample code and the compiler error?

> Need to be able to collapse certain areas (For example, the taskbar needs to be practically non-existant until someone hits alt)

I haven't ever tried glade, but I think you should do this kind of stuff through code. I don't think this is possible through glade.

> Need to load the glade file in PyGTK without it automatically popping up all the windows at once...

Again please post some sample code. I strongly think this is a problem with your code.

---

### Post by J V on 2009-10-03
> mmm, why don't you provide some sample code and the compiler error?This is a glade problem, the sample has already been posted...

> I haven't ever tried glade, but I think you should do this kind of stuff through code. I don't think this is possible through glade.I know it isn't possible through glade, I'm wondering how I would collapse a container without actually destroying it...

> Again please post some sample code. I strongly think this is a problem with your code.     This is some of the code responsible... See comment...

```
import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade
import callbacks

class osiris:
    def __init__ (self):
        self.gladefile = "osrs.glade"  
            self.wTree = gtk.glade.XML(self.gladefile) # Commenting this line stops windows from opening, according to documentation, setting the second variable to "None" should stop windows automatically opening, instead it throws an error: "(main.py:11110): libglade-CRITICAL **: glade_xml_build_interface: assertion `wid != NULL' failed"
        
        self.MainWindow = self.wTree.get_widget("MainWindow")
        self.call = callbacks.callback()
    
if __name__ == "__main__":
    osrs = osiris()
    gtk.main()
```

---

### Post by SledgeHammer_999 on 2009-10-03
I don't know python so I will explain in general for the second question:
Every container derives from the class widget. Every widget has a function named hide(). So all you have to do is container.hide() (translate it to python).

About third question: Since I don't know python nor have glade I hope someone else spots the problem.

About first: I can't seem to find the glade sample you posted. Did you edited it out?
EDIT: nevermind, I found it.

EDIT2:
For me the pics show. All I had to do is put the a random pic(with the correct name) in the SAME folder as the glade file.
Also the progress bar goes above 90% in the glade designer.
(I loaded your glade in the glade3 designer)

---

### Post by J V on 2009-10-03
> I don't know python so I will explain in general for the second question:
Every container derives from the class widget. Every widget has a function named hide(). So all you have to do is container.hide() (translate it to python).

About third question: Since I don't know python nor have glade I hope someone else spots the problem.

About first: I can't seem to find the glade sample you posted. Did you edited it out?
EDIT: nevermind, I found it.

EDIT2:
For me the pics show. All I had to do is put the a random pic(with the correct name) in the SAME folder as the glade file.
Also the progress bar goes above 90% in the glade designer.
(I loaded your glade in the glade3 designer)Ok, thanks, that will completley hide it? (I noticed that empty cells take up space but just show grey)

When you hit preferences for a glade file, it offers you the option to ask for the images from a subdirectory, but every time I load the file again its been reset...

Yes, apparently the glade 2 designer didn't allow anything over 90%, glade 3 has it fixed

Thanks :P

---

### Post by SledgeHammer_999 on 2009-10-03
Yes it will hide it AND every widget it contains. Then use container.show() to show it again. Maybe you need to disable/destroy/reconfigure the empty cells.(I have not experience with them).

---

### Post by J V on 2009-10-03
Hmm... does this hide the entire container or can it be used for individual cells? (Not much good if it hides the contents but the space is still taken up...)

Edit: Images needed a ./ before the dir. got them to work now...

Edit2: I have a table with the images and their labels next to each other (As you can see in the file previously mentioned), I need a window to popup (Similar to a tooltip), if I wanted this image to popup if someone hovers over the image, or the label, then it would reset the hover timer if someone switched from image to label... I need them to behave as one... is there anything that can do this? (A special widget mabey? I would certainly prefer that, as I can tick homogeneous and keep them the same size without adding tons of space to the image coloumns...

---

### Post by SledgeHammer_999 on 2009-10-03
> **J V said:**
> Hmm... does this hide the entire container or can it be used for individual cells? (Not much good if it hides the contents but the space is still taken up...)

Try it and see what happens.

---

### Post by J V on 2009-10-03
Got a new problem... by using the correct relative directory (uploading glade file now) The images show up correctly, but in the terminal output, it is still looking for the images in the wrong place...

On the bright side though, the windows opening automatically was a bug because I opened my glade2 file in glade3... don't know where that came from...

[http://www.2shared.com/file/8202154/841e42ab/osrs.html](http://www.2shared.com/file/8202154/841e42ab/osrs.html)

---

### Post by SledgeHammer_999 on 2009-10-03
1.Can you post the terminal output?
2.Maybe in the preferences instead of "./images" put "images/".

---

### Post by J V on 2009-10-03
tried the other one... and another variation... Still not doing the files...

Terminal output is a long list of this:
```
(main.py:17880): libglade-WARNING **: Error loading image: Failed to open file './rouges.gif': No such file or directory

(main.py:17880): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'
```

In addition...

```
./main.py:27: GtkWarning: gtk_notebook_set_tab_label: assertion `GTK_IS_WIDGET (child)' failed
  self.wTree = gtk.glade.XML(self.gladefile)
```

Theres a few other things... but your post made me forget them :P

---

### Post by SledgeHammer_999 on 2009-10-03
> The images show up correctly, but in the terminal output, it is still looking for the images in the wrong place...

Are you sure that "rouges.gif" is displayed?

---

### Post by J V on 2009-10-03
Its displayed in glade yes, but not in the application when I run it... the application is looking in the wrong place...

But at the moment I fixed the problem with the windows opening... now I can't get them to open at all :P

I am also getting an error after the image errors:
```
(main.py:18823): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
```vbox is the very first widget type under the window...

Edit: This is a bug... and apparently there's no fix... Anyone know a way around it?

---

### Post by J V on 2009-10-04
OK! Figured out how to get windows to show etc! Its really great :P

Still having trouble with the images though... doesn't seem to be a problem with glade, perhaps with pyGTK...

Edit: To make my aboutdialog hide without destroying it (and completely removing from the xml object), I mapped a hide_all() to both the close and response signals... (I still can't get it to stop destroying the window on close) Won't this cause trouble later on when hundreds of active windows still exist? Is there a better way I should be going about this?

---

### Post by J V on 2009-10-05
Ok, now the glade file is writing the relative directory for the images in a comment at the top of the file, but pygtk isn't prepending the image locations with it...

Anyone know how that happened or do I have to make a regex to add the image locations myself?

Also, I am completely at a loss as to how to open/close windows... I need to create them so that they can be destroyed when closed, and I need to be able to open/close them from the callback class in another file (an import), to keep things tidy...

So far, just hiding windows doesn't work (If someone clicks the X it is destroyed and can't be opened again), and I can't figure out how to open them from the callbacks class... following is some of the source...

Also, callbacks isn't being registered as the signal handler...

```
import callbacks

class osiris:
    def __init__ (self):
        #Set the Glade file    
        self.gladefile = "osrs.glade"
            #Get callbacks
            self.call = callbacks.callback(self)
            self.Main = gtk.glade.XML(self.gladefile,"MainWindow").get_widget("MainWindow")
        self.Main.show_all()
``````
parent = ""
class callback:
    def __init__ (self,parentapp):
        
        #Set the Glade file
        parent = parentapp
            gtk.glade.XML(parent.gladefile).signal_autoconnect(self)
        
    #####    Callbacks        #####    
    ###    MainWindow        ###
    def on_quit_activate(self,widget):
        print "Help"
    def on_about_activate(self,widget):
        parent.About = gtk.glade.XML(self.gladefile,"aboutdialog").get_widget("aboutdialog")
        parent.About.show_all()
        print widget
                
    ###    aboutdialog        ###
    def aboutdialog_hide(self,widget,response):
        parent.About.destroy()
```

---

### Post by J V on 2009-10-05
The good news is, I fixed pretty much all the problems :P

I have 4 issues atm though...

1. The ever present images
2. The structure of my program (Callbacks in another file loaded like module) means that when a window is created it is created in the callbacks module (I presume this is called namespace), how do I link the main .py file to it so I can easily grab windows? (Or how do I create the windows in the main.py in the first place?)
3. Certain windows that there should be only one of, can be easily duplicated (Clicking on the menu item a second time for example), is there a builtin way to stop this from happening? Or do I have to stick if statements for a larger overhead in my events?
4. I have a button I need to register both left, and right-clicks on... Is there a signal that will work with this, or do I have to write an if to find out which button is being pressed?

---

### Post by SledgeHammer_999 on 2009-10-05
> **J V said:**
> 
3. Certain windows that there should be only one of, can be easily duplicated (Clicking on the menu item a second time for example), is there a builtin way to stop this from happening? Or do I have to stick if statements for a larger overhead in my events?
4. I have a button I need to register both left, and right-clicks on... Is there a signal that will work with this, or do I have to write an if to find out which button is being pressed?

3. after you create the window set the button's sensitivity to false

4. as far as I know both right and left click are firing the same event. (I am talking about the signal_button_press_event and  signal_button_release_event). You should check the GdkEventButton that is sent to your callback.(more specifically the "button" property of the struct).

I don't know how these things are named in pygtk but I think you get the idea.

---

### Post by J V on 2009-10-05
Thanks for the help, I really don't want to have to set sensitivity to false every time...

Perhaps its possible to say window.show_all() in an if statement, and if false, load the xml a second time and do it again... Yes I think that's the only way to be certain... At least without 5 lines of code in every function...

I guess I'll be working on it tomorrow again huh :P (Also, I can't get the events to register any more... strange...)

Edit: Perhaps on certain one-of-a-kind windows I can set the close/destroy event return to true so that it won't close but just hide... This would however be a right pain in the rear concerning memory limitations...

---

### Post by J V on 2009-10-06
Latest problem: "GtkWarning: Ignoring the separator setting"

This error is thrown when I print the results of "gtk.glade.XML(filename).signal_autoconnect(self)"

Also, because this is the function that connects the signals, none of them work atm...

Coulden't find anything about it on google, need help from an expert :/

---

### Post by J V on 2009-10-07
Ok, switched to GTKbuilder, thats fixed most of it...

How do I stop a window being completley destroyed? I want to destroy the variable, but keep the data in the gtk.builder object... is this possible? Should I just hide all the windows rather than destroy them? What happens if say a video player is running in a window that is hidden, won't that suck up memory?

---

### Post by J V on 2009-10-08
bump = boring :D

My gtkmessagedialog won't signal properley... I have 2 custom buttons, and 2 signals (One for cancel and the x button, one for quit)

Niether of these signals are even being called... Whats wrong?

---

### Post by J V on 2009-10-10
Ok, I need help...

I need to set up this program so windows don't get destroyed... The reason for this is that I only load the xml file once (through gtkbuilder)

Could anyone please give me a shirt example of how OO is supposed to work on GUI applications? I really don't get it :|

---

### Post by SledgeHammer_999 on 2009-10-10
I suggest you start a new topic and put on the title that you're using pygtk and glade.

---

### Post by J V on 2009-10-10
ok...

---

