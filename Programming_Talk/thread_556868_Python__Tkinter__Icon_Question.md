---
title: "Python / Tkinter / Icon Question"
date: 2007-09-21
forum: Programming Talk
---

### Post by thomasaaron on 2007-09-21
Hi, folks. I've written a Python/Tkinter GUI, and put an icon on it (in the upper left...).
Here is my code:

iconbitmapLocation = "@iconMask.xbm"
iconmaskLocation = "@icon.xbm"
self.root.iconbitmap(iconbitmapLocation)
self.root.iconmask(iconmaskLocation)

Now, this works GREAT in Ubuntu. But when I ran the program through py2exe and ran it on a Windows machine, the icon is there, but it doesn't look very good. It is sort of grayed out.

I'm thinking I should use a .ico image (which I can create no problem with the Gimp). But I got an error that the program was unable to read the file.

Any ideas on how I can make the icon look good in Windows too?

Thanks,
Tom

---

### Post by loell on 2007-09-21
maybe its because of the image format, have you tried to load a PNG format?

---

### Post by thomasaaron on 2007-09-23
Well, I tried using a png image but get the same format.
I've not been able to come up with an image it can read other than xbm images made by the Gimp.

---

