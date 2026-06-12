---
title: "[Python/PyGtk] Make image merge with background..."
date: 2011-06-17
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-17
hey guys .... i wanted to know how can i merge the image in the background of th widget......here is my code

code:
 # /usr/bin/env python
import pygtk,gtk

button=gtk.Button()
image=gtk.Image()
image.set_from_file("py.png")
image.set_size_request(100,100)
label=gtk.Label("Python")
hbox=gtk.HBox()
hbox.pack_start(image)
hbox.pack_start(label)
button.add(hbox)
vbox=gtk.VBox()
vbox.pack_start(button)
win=gtk.Window()
win.add(vbox)
win.show_all()
win.set_size_request(150,200)
win.connect("destroy",lambda wid:gtk.main_quit())
gtk.main()


Its a button with the image and the label....

I have attached the output....i want all the white portion of the image to merge with the background is thre a way to do that?????

---

### Post by dargaud on 2011-06-17
I don't know anything about gtk, but in general mergings are done using transparency colors (gif, 8-bit png) or alpha channel. Is the white of your image declared as transparent ? [more info]("http://www.imagemagick.org/discourse-server/viewtopic.php?f=1&t=18596")

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-17
thanks man that was really helpful...!!! :) thnks again buddy ... i dint know abt image transparency...:)

---

### Post by gmargo on 2011-06-17
I checked the official "python powered" logos from [http://www.python.org/community/logos/](http://www.python.org/community/logos/).

Those images do have a white background (+80% alpha) so they do not show up as transparent.

However, it is possible to edit the image to make it transparent.  I don't know if this can be done in the PyGTK toolkit on the fly, but I managed to do it with **gimp**, following this tutorial: [http://www.gimp.org/tutorials/Changing_Background_Color_1/](http://www.gimp.org/tutorials/Changing_Background_Color_1/)

Attached are the "before" and "after" images.  The original image I used was [http://www.python.org/community/logos/python-powered-h-140x182.png](http://www.python.org/community/logos/python-powered-h-140x182.png)
Download the two and put them side-by-side in your python test program to see the difference.
[ ]("http://www.python.org/community/logos/python-powered-h-140x182.png")

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-18
thanks for help guys i figured how to make images transparent in pygtk.....it uses pixbuf and then takes the image as pixbuf....

Thanks for ur effort gmargo :)

---

### Post by gmargo on 2011-06-18
> **Dhiraj Thakur(Invincible) said:**
> thanks for help guys i figured how to make images transparent in pygtk.....it uses pixbuf and then takes the image as pixbuf....


That's great.  How about sharing your solution?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-18
Yeah why not gmargo.....here's the code the image py.png is the one with white background....

code:

# /usr/bin/env python
import pygtk,gtk

button=gtk.Button()
pixbuf=gtk.gdk.pixbuf_new_from_file('py.png')
pixbuf=gtk.gdk.Pixbuf.add_alpha(pixbuf,255,255,255,255)
pixbuf=pixbuf.scale_simple(40,40,gtk.gdk.INTERP_BILINEAR)  #scaling the image so that it look's like a button ...lol
image=gtk.Image()
image.set_from_pixbuf(pixbuf)
label=gtk.Label("Python")
hbox=gtk.HBox()
hbox.pack_start(image)
hbox.pack_start(label)
button.add(hbox)
vbox=gtk.VBox()
vbox.pack_start(button)
win=gtk.Window()
win.add(vbox)
win.show_all()
win.set_size_request(150,3)
win.connect("destroy",lambda wid:gtk.main_quit())
gtk.main()


that's it....thanks again guys fr ur help....

---

