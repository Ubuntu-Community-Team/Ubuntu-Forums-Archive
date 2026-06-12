---
title: "Finding wallpaper used for any workspace (KDE/Gnome/Compiz/others...)?"
date: 2008-11-16
forum: Programming Talk
---

### Post by kaivalagi on 2008-11-16
Hi All,

I am attempting to write a python app to display html content on the desktop, with fake transparency, using a cropped wallpaper image for html background.

This is working fine for gnome/nautilus as I can get the wallpaper in use by fetching the correct gconf key for the file path and manipulate the image that way. However this doesn't cover all desktop configurations by a long shot....Compiz with a different wallpaper per workspace, and KDE etc aren't catered for.

Are there any python libraries around to provide the current workspaces wallpaper filepath for any OS configuration?

Can Xlib be used to get the current workspace root window image, so I can manipulate that? I did have a quick look at Xlib and got stuck, is there any good documentation and examples out there for python Xlib? This would be the best route I think, because it is at a low enough level to not be desktop manager specific...

The function to save the cropped image is like so currently:
[PHP]    def generateBackground(self, x, y, width, height):
        
        gconf_path_wallpaper = '/desktop/gnome/background/'
        self.background = "/tmp/"+str(uuid.uuid1())+".jpg"
        
        client  = gconf.client_get_default()
        wallpaper = client.get_string(gconf_path_wallpaper + 'picture_filename' )
        img = Image.open(wallpaper)
        box = (x, y, x+width, y+height)
        newimg = img.crop(box)
        newimg.save(self.background)[/PHP]

Any pointers in the right direction would be very much appreciated.

Cheers

---

### Post by kaivalagi on 2008-11-16
Any ideas anyone?

---

### Post by kaivalagi on 2008-11-22
Okay, well I figured out the Xlib part to get me the pixmap associated with the current screen. But am at a lose on how to convert it to some useful in python...

Now how do I convert a pixmap into a jpg for use with the python imaging library?

Any takers? Any help would be very much appreciated!

My test app is:

[PHP]#!/usr/bin/python
# -*- coding: utf-8 -*-
from Xlib import display, Xatom, X, Xutil, rdb
from Xlib.xobject.drawable import Window, Pixmap
from kaa import imlib2 # install: python-kaa-imlib2 (python-kaa-base ?)
from PIL import Image # install: python-imaging

display = display.Display()
screen = display.screen()
root = screen.root

XROOTPMAP_ID = display.intern_atom("_XROOTPMAP_ID")
ESETROOT_PMAP_ID = display.intern_atom("ESETROOT_PMAP_ID")

pmap = root.get_full_property(XROOTPMAP_ID, Xatom.PIXMAP)
if pmap == None:
    pmap = root.get_full_property(ESETROOT_PMAP_ID, Xatom.PIXMAP)

if pmap != None:
	pix = Pixmap(display.display, pmap.value[0])
	geom = pix.get_geometry()
	
        # so far so good, now what? neither of the below work...
        # I have tried lots of permutations of this and hit various
        # issues...what am I doing wrong?

	try:
		# imlib2
		img = imlib2.Image(pix)
		tempfile = "/tmp/"+str(uuid.uuid1())+".jpg"
		img.save(tempfile)
		print "saved image to: "+tempfile
	except Exception, e:
		print "failed to convert using IMLib: "+e.__str__()
	
	try:
		# python image library
		mode = 'RGB'
		size = (geom.width, geom.height)
		img = Image.frombuffer(mode, (int(geom.width), int(geom.height)), pix)
		tempfile = "/tmp/"+str(uuid.uuid1())+".jpg"
		img.save(tempfile)
		print "saved image to: "+tempfile
	except Exception, e:
		print "failed to covert using PIL: "+e.__str__()
[/PHP]

---

### Post by kaivalagi on 2008-11-29
Can anyone shed any light on this? Surely there is a way to get a jpg of the current wallpaper (without desktop icons etc), no matter what desktop manager is in use?

---

### Post by kaivalagi on 2008-12-15
Come on, surely someone has some clue about this...any ideas please

---

### Post by nvteighen on 2008-12-15
Just something... Aren't there are two possible ways to configure Compiz, through a file and through GConf? The Compiz Settings Manager gives such an option somewhere, so, unless it's a future feature, you may check that (first checking what WM is running, if Compiz, then check both possibilities).

About KDE, I guess it works using a configuration file, somewhere in ~/.config

---

### Post by kaivalagi on 2008-12-15
> **nvteighen said:**
> Just something... Aren't there are two possible ways to configure Compiz, through a file and through GConf? The Compiz Settings Manager gives such an option somewhere, so, unless it's a future feature, you may check that (first checking what WM is running, if Compiz, then check both possibilities).

About KDE, I guess it works using a configuration file, somewhere in ~/.config

Thanks for the reply

I am reluctantly going down the route of dealing with each type of wallpaper setting possible. I am coding for gnome, kde and xfce, and will add compiz via gconf at some point too once I figure that out. But this method is far from ideal. 

There must be a way of getting the pixmap from root X window, which was set through any of the windows managers....still searching on that one...so far it seems that it's a one way street, setting the root pixmap is easy, getting it is not.

If I could come up with an independent means to get the image from the current root window that would be the ticket...however my X lib skills are extremely limited...

---

### Post by nvteighen on 2008-12-15
> **kaivalagi said:**
> Thanks for the reply

I am reluctantly going down the route of dealing with each type of wallpaper setting possible. I am coding for gnome, kde and xfce, and will add compiz via gconf at some point too once I figure that out. But this method is far from ideal. 

There must be a way of getting the pixmap from root X window, which was set through any of the windows managers....still searching on that one...so far it seems that it's a one way street, setting the root pixmap is easy, getting it is not.

If I could come up with an independent means to get the image from the current root window that would be the ticket...however my X lib skills are extremely limited...
I guess there's no universal way to do this. Mainly because there are differences on how the desktop is managed by the different DEs. And tracing the pixmap would also trace **anything**, including panels and such...

What happens is that you're struggling against different "platforms"... for a task that it may not be easily ported from one to the another. Also consider using native tools, e.g. are you sure you can't do this in KDE4 using a Plasmoid?

(I guess you want to emulate MS Win98+ Active Desktop...)

---

### Post by mssever on 2008-12-15
I don't think you can rely on the root window. For example, before I upgraded to Intrepid, I used Compiz to set multiple wallpapers (Intrepid's version of Compiz is broken in this regard). But if I switched to Metacity, or if Compiz crashed, I saw a different wallpaper altogether.  This indicates that Compiz was only layering its wallpaper on top of something else (the root window or even another layer). I also know that under some circumstances Nautilus controls the wallpaper--at least if you let Nautilus draw icons on your desktop (desktop icons are pure evil). For example, I was troubleshooting something on my brother's machine a while ago via SSH. I started up Nautilus without the --no-desktop option and pretty soon had his wallpaper. When I killed Nautilus completely (not always easy), I got my wallpaper back.

---

### Post by kaivalagi on 2008-12-15
Yeah, I think the root window will cause me issues due to layers and panels etc, I just managed to get something working using the gtk.gdk.pixbuf object as follows:

```
root = gtk.gdk.get_default_root_window();
rootwidth, rootheight = root.get_size();
pix = gtk.gdk.Pixbuf(gtk.gdk.COLORSPACE_RGB, 1, 8, rootwidth, rootheight);
pix.get_from_drawable(root, root.get_colormap(), 0, 0, 0, 0, rootwidth, rootheight);
pix.save("/tmp/test.png", "png")
```

I effectively get a screenshot....would this be the case if I managed to do the equivalent in Xlib, I don't know?

I guess I'll have to create a function for the purpose of getting the wallpaper image, which has to get updated as and when to cope with the changes in wallpaper implementation in the various desktop managers out there...

Shame really, a short fall in the X libraries afaik...means I can't cater for the openbox/awesome users out there too well...they'll have to use a --wallpaper option :)

Thanks guys

BTW, I guess the app I am working on does something similar to what active desktop in windows does/did, I hadn't thought  about that. But the app also has plugins to handle the retrieval of various bits of info, which is rendered in formatted html. I wanted something similar to conky, but that supported html formatting...see my sig for the link

---

### Post by Cracauer on 2008-12-15
I once tried to mess with that code to make GNOME be able to have different background images on two desktops (with different geometry, so same image looks really stupid). I came about as far as you did.

---

