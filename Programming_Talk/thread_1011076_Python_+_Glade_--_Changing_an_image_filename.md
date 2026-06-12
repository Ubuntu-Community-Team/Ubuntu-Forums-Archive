---
title: "Python + Glade -- Changing an image filename"
date: 2008-12-14
forum: Programming Talk
---

### Post by robz0rz on 2008-12-14
Hello all


I'm creating a little tool to change certain aspects of my new custom icon-theme, like branding, folders, etc. I decided this was a good project to start learning Python and PyGTK with it.

I'm slowly understanding how Python works, it's a lot of fun to write it actually!

I used Glade to create a user interface. I'm now at a point where I have a GtkImage somewhere, and I want to change the filename of the source image it uses. In other words: I want to set the image it displays through Python instead of Glade (because the image can change on certain events).

```
imgFuture = self.wTree.get_widget("BrandingFutureSVG")
```

What method do I have to call on imgFuture in order to do this? Thanks

---

### Post by .nedberg on 2008-12-14
You can use:
```

filename = path-and-or-filename.png
imgFuture.set_from_file(filename)

```

---

### Post by robz0rz on 2008-12-14
Thanks! That worked!

Is there any way I can find these methods myself? Is there a good documentation?

For example, other things I am trying to archieve are:
Extracting the filename from the widget
Changing the items in a ComboBox

---

### Post by .nedberg on 2008-12-14
[http://www.pygtk.org/](http://www.pygtk.org/)

Have a look under "Documentation".

---

### Post by mssever on 2008-12-14
> **robz0rz said:**
> Is there any way I can find these methods myself? Is there a good documentation?
Install DevHelp and the PyGTK doc package. DevHelp will then give you all that info.

---

