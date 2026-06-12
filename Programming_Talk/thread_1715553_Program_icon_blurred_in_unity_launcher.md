---
title: "Program icon blurred in unity launcher"
date: 2011-03-27
forum: Programming Talk
---

### Post by Iehova on 2011-03-27
Hi,

I am a complete newbie to programming and decided to set myself the task of coding a GTK frontend to espeak in Python, because, well, I wanted one. :P

After a day's work I think I've made good progress and I'm very happy with the way things stand. My only problem is with the program's icon. The relevant code is here:

```
	def __init__(self):
		self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		self.window.set_position(gtk.WIN_POS_CENTER)
		self.window.set_size_request(600, 120)
		self.window.set_title("PySpeak")
		self.pixbuf = gtk.gdk.pixbuf_new_from_file('pyspeak.svg')
		self.window.set_icon(self.pixbuf)
```

Which I think is pretty standard. As I hoped, the icon appears in the unity launcher (I haven't tested standard gnome), but it's very very blurred. I've created another launcher icon, to run a script to start and stop the madwimax driver, and that looks fine, so I figure the problem must be something I'm doing.

Here is a screenshot: [http://img62.imageshack.us/img62/2975/screenshotts.png](http://img62.imageshack.us/img62/2975/screenshotts.png) . It's not the prettiest icon by any means, I'm not much of an artist either. ;)

Is this the standard way to display a taskbar icon? Should I have done something differently? Any help would be much appreciated.

P.S. I figured this didn't belong in the Natty forum because I don't think Unity is the issue here, rather I am. :P

EDIT: Oh, and the icon is SVG

---

### Post by deathadder on 2011-03-28
Hi,

I think what you want is [gtk.gdk.Pixbuf.scale_simple]("http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#method-gdkpixbuf--scale-simple").

Try something like this:
```
self.pixbuf = gtk.gdk.pixbuf_new_from_file('pyspeak.svg')
self.pixbuf = pixbuf.scale_simple(width, height, gtk.gdk.INTERP_BILINEAR)
self.window.set_icon(self.pixbuf)
```

You could alternatively try [gtk.gdk.pixbuf_new_from_file_at_size]("http://www.pygtk.org/docs/pygtk/class-gdkpixbuf.html#function-gdk--pixbuf-new-from-file-at-size")

---

### Post by Iehova on 2011-03-29
Hi deathadder,

Thanks very much for the help! I have tried:

```
		self.pixbuf = gtk.gdk.pixbuf_new_from_file_at_size('pyspeak.svg', 48, 48)
		self.window.set_icon(self.pixbuf)
```

and

```
		self.pixbuf = gtk.gdk.pixbuf_new_from_file('pyspeak.svg')
		self.pixbuf = self.pixbuf.scale_simple(48, 48, gtk.gdk.INTERP_BILINEAR)
		self.window.set_icon(self.pixbuf)
```

But the image still appears blurry, likewise if I use existing icons (I tried bash.svg at 128*128 and 48*48) they too appear blurry. There must be something I'm missing...

---

### Post by deathadder on 2011-03-29
Hmmm, in that case I'm not too sure at the moment. I'll have a look around and let you know if I find anything helpful! :)

---

### Post by pavolzetor on 2011-08-09
Hi, I have same problem, I have reported bug

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/823214](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/823214)

It seems, that using .desktop files solve it

---

