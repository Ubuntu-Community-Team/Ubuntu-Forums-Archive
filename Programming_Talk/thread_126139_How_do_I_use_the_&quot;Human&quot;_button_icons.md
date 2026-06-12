---
title: "How do I use the &quot;Human&quot; button icons?"
date: 2006-02-05
forum: Programming Talk
---

### Post by moephan on 2006-02-05
Hi all,

Here's an easy one:

I want the Ok, Cancel, Help buttons on my Python Gtk apps to look the same as the ones on the Ubuntu system apps, like network-manager, update-manager, etc... I do notice that there are some inconsistencies, but none the less, I assume there must be a standard path to the image files, but I can't find them anywhere. I am also open to the idea that I am going about it all wrong and I should just be telling my buttons what kind of buttons they are and they display the correct icon, but I haven't seen any documentation on that.

If anyone could point me in the right direction I would be most appreciative.

Cheers, Rick

---

### Post by ow50 on 2006-02-05
[QUOTE=moephan]I am also open to the idea that I am going about it all wrong and I should just be telling my buttons what kind of buttons they are and they display the correct icon, but I haven't seen any documentation on that.[/QUOTE]
Correct. Specify the type, not any image file.

Technically you can set any image on any button, but that would be bad practise. You should use the stock icons (gtk.STOCK_OK, gtk.STOCK_CANCEL, etc.) so that user has control over what the icons look like instead you as a programmer dictating the icons for all users. Using the stock icons means the user will get the Human icons if she is using the Human  theme.

---

### Post by moephan on 2006-02-05
Awesome! For the other pythoners out there ...

```

	img_ok = gtk.Image()
	img_ok.set_from_stock(gtk.STOCK_OK,gtk.ICON_SIZE_BUTTON)
	self.okbutton = gtk.Button("OK")
	self.okbutton.set_image(img_ok)

```

Cheers, Rick

---

### Post by ow50 on 2006-02-05
[QUOTE=moephan]Awesome! For the other pythoners out there ...[/QUOTE]
Well, you get the stock button easiest with
```
button = gtk.Button(stock=gtk.STOCK_OK)
```
This way you get the standard title, mnemonics and theme-dependent icon. Also, the title will get automatically translated.

---

### Post by moephan on 2006-02-05
Much better! Thanks a million.

Is there a place that has all this written down? I'm finding it difficult to get the gestalt of how to write standard compliant GUIs with Python and Gtk. I'm wondering if I just haven't found the right resources yet.

Cheers, Rick

---

