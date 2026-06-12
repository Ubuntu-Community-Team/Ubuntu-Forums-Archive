---
title: "Gtk folks, help me out!"
date: 2005-09-19
forum: Programming Talk
---

### Post by mostwanted on 2005-09-19
I'm trying to make an image viewing application, but I'm having trouble getting the image widget to work properly. The trouble is with updating the image with another pixbuf after it's been used once.

I'm using tables and trying to reattach the image at the same coordinates works, but doesn't remove what's already there (e.g. I see 2 images). Merely updating what the Image object points to doesn't work of course. What can I do?

I'm using Gtk# with C#, but examples in any programming language will be accepted.

---

### Post by doclivingston on 2005-09-19
What are you using to update the image? I'm fairly sure that the c# equivalent of gtk_image_set_from_pixbuf should work.

---

### Post by mostwanted on 2005-09-19
Wee, I got it working :D Thanks!

Gtk# doesn't have a definition of a method by that name, which sorta confused me, but it did have a property simply named Pixbuf:

```
// Load into buffer and update image
private void LoadImg(string path)
{
	try
	{
		// New pix buffer loaded with a test image into an Image container class
		img.Pixbuf = new Gdk.Pixbuf(path);
	}
	catch (Exception e)
	{
		Console.WriteLine("An exception occured: {0}", e.Message);
	}
}
```

---

### Post by mostwanted on 2005-09-19
It's a simple image viewer/slideshow thinger. You load a folder into it and then you can view the images one by one.

Source: [http://rafb.net/paste/results/M1bRGj73.html](http://rafb.net/paste/results/M1bRGj73.html) 

Download here for use with Mono (might also work in .NET, I'm not sure):

[http://htmldesign.dk/public/downloads/PhotoSafari.exe](http://htmldesign.dk/public/downloads/PhotoSafari.exe)

---

