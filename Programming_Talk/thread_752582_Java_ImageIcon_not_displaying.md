---
title: "Java ImageIcon not displaying"
date: 2008-04-11
forum: Programming Talk
---

### Post by DBQ on 2008-04-11
Hi everybody.

I have another strange problem.  I am using java JpopupMenu.  I want my menu to have an icon next to the text.  For some reason the ImageIcon object finds the file, but does not display the image.  Note: I tried jpg, gif, and png.  None are displaying.

Any ideas?

---

### Post by kostkon on 2008-04-11
Are you sure that you are putting the right path as an argument, e.g.:
```
ImageIcon testicon=new ImageIcon("../../images/popup_icon.gif");
```

---

### Post by DBQ on 2008-04-11
I am including the right path - the object finds it.

---

### Post by kostkon on 2008-04-11
> **DBQ said:**
> I am including the right path - the object finds it.
OK, I see.

Hmmm, you could try to set the position of the text relative to the icon with the *setHorizontalTextPosition(int textPosition)* method that a *JMenuItem *object inherits from *javax.swing.AbstractButton*.

Maybe the text blocks the icon from appearing, it does not leave space for it. Thus, after you create the menu items, call the *setHorizontalTextPosition()* accordingly, e.g.:
```
testItem.setHorizontalTextPosition(JMenuItem.RIGHT);
```

---

### Post by DBQ on 2008-04-11
I figured it out.  Apperently when using eclicpse, you must also include the image to the resource list. Thanks for trying to help though.

---

### Post by xlinuks on 2008-04-12
If your project/test will have many menu icons/images make sure to load them in a separate thread and apply them wisely when ready, if failed loading image provide a custom painted "no-image" BufferedImage for your GUI to work even if resources not found. This will also protect you from issues on windows/Linux you might get weird/different behaviour because of asynchronous image loading.
If you didn't run into such issues yet, you will run into this sooner or later as the gui gets stuffed.

---

