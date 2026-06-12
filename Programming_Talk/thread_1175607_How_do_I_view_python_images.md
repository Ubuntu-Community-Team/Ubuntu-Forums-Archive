---
title: "How do I view python images?"
date: 2009-06-01
forum: Programming Talk
---

### Post by Fzang on 2009-06-01
As far as I've understood with my extremely limited knowledge about python (limited = none, none at all, absolutely none and nothing) images and GUI can be imported/embedded (whatever you call it) into the python file. My question is, how do I view and edit those images in the python file in a simple manner?

Do I want to program something? Not the slightest. I want to theme and tweak my system as I please but sometimes there are some annoying small images and icons that don't follow any scheme and can't be found anywhere in the system - they're in the app itself and I have a really hard time modifying these.

And while I'm at it, is python a good place to start programming if you're 17 and want a hobby for the summer? :D

---

### Post by decoherence on 2009-06-01
> **Fzang said:**
> As far as I've understood with my extremely limited knowledge about python (limited = none, none at all, absolutely none and nothing) images and GUI can be imported/embedded (whatever you call it) into the python file.


Sure you can embed an image in to a python file or any other type of file. I'm not sure why someone would... maybe for ease of distributing the file? I'm no Python expert, mind you, so maybe it is common practice. (anyone?) Or, maybe I've totally misunderstood your question! ;) Well, I'll try anyway.

> 

My question is, how do I view and edit those images in the python file in a simple manner?



Basically, to view such embedded data, you need to determine where it starts and stops and what format it is. Seeing as Python is an easy-to-read interpreted language, this shouldn't be hard; just open up the file in a text editor. Determine the format of the embedded image by checking the function used to read the image data... it should describe whether it is interpreting it as a jpeg, png or what.

Then extract the data from the file (could be as simple as copy/paste?), paste it in to another file with the appropriate image suffix (.jpg, .png, etc) open it in the appropriate program, make your edits, embed it back in to the program (by opening it in a text editor and, again, copy/paste) and you're done! (in theory!)

> Do I want to program something? Not the slightest. I want to theme and tweak my system as I please but sometimes there are some annoying small images and icons that don't follow any scheme and can't be found anywhere in the system - they're in the app itself and I have a really hard time modifying these.


curious for some specific examples.

> 
And while I'm at it, is python a good place to start programming if you're 17 and want a hobby for the summer? :D

Yes, yes, 1000 times yes!! Go for it!

Also, you may want to look at the PyGame and Pyglet modules if you're interested in graphical programs.

---

### Post by Fzang on 2009-06-01
Okay so I'm not sure if it's actually in the python file, there are many other files to pick from... gotta start somewhere :p

I checked the dropbox (that's the application. I can't stand the blue tray icon. I want it black like all others, no matter what it takes :D) and it came up with a HUGE block of text which I'm not really sure about. The text looks like /x12'/x04'/x02'/ etc etc etc. What is this? I don't think gedit is messing up because I can read the first bits of code just fine... ah well, have a look, I don't know what to say.

The source and the executable from /usr/bin attached.

---

### Post by decoherence on 2009-06-01
> **Fzang said:**
> it came up with a HUGE block of text which I'm not really sure about. The text looks like /x12'/x04'/x02'/ etc etc etc. What is this?

I expect that is your image. I'm not sure about the format... does anyone know what format "gtk.gdk.pixbuf_new_from_data()" expects?

I'll do a bit more looking if I have time...

---

### Post by simeon87 on 2009-06-01
> **decoherence said:**
> I expect that is your image. I'm not sure about the format... does anyone know what format "gtk.gdk.pixbuf_new_from_data()" expects?

The docs can be found [here](http://www.pygtk.org/pygtk2reference/class-gdkpixbuf.html#function-gdk--pixbuf-new-from-data).

---

### Post by benj1 on 2009-06-02
from the file you posted most of it is c apart from some set up scripts.
theres a serializeimages.py file.

thats gets png images from data/icons/hicolor/64x64/apps/dropbox.png and data/icons/hicolor/16x16/apps/dropbox.png

they are just normal png files which you can modify without python.

if you look in usr/share/pixmaps/dropbox you should find the pngs it uses there.

---

### Post by Fzang on 2009-06-02
Unfortunately, those icons are just the application's default icons and not the icon it uses for the tray. The tray icon is not in hicolor or anywhere in the app's files or anywhere I've searched...

---

### Post by benj1 on 2009-06-02
have you looked to see if its loose in the /usr/share/pixmaps directory, rather than in its own directory.

other than that i don't know, i don't use drop box.

---

